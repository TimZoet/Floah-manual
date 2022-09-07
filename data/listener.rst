Data Listeners
==============

The :code:`floah::Widget` class inherits from :code:`floah::DataListener`, making it possible for all widgets to receive
update events from data sources. A widget can register itself with the data source(s) it references. For that purpose,
the base :code:`floah::DataSource` class has an :code:`addDataListener` method (and of course a corresponding
:code:`removeDataListener`). A listener can register with multiple sources, and multiple listeners can be registered
with the same source.

When a data source emits an update event, it will call the :code:`onDataSourceUpdate` method of all listeners that
registered. The data source passes a reference to itself to the method, so that the listeners can figure out which data
source was updated, should they have more than one.

When updating a widget's data sources, this will typically follow the pattern *remove self from old data source* >
*store reference to new data source in member* > *add self to new data source*. The :code:`Widget` class has a utility
method, :code:`replaceDataSource`, that takes care of all that and returns whether the data source reference was
actually replaced. This return value can be used to trigger widget updates and redraws.

Below a short snippet showcasing a widget that has two data sources and listens to their updates:

.. code-block:: cpp

    class YourWidget : public floah::Widget
    {
    public:
        void setListDataSource(floah::IListDataSource* source);
        void setIndexDataSource(floah::IIntegralValueDataSource* source);

        void onDataSourceUpdate(floah::DataSource& source) override;

    private:
        floah::IListDataSource*          list  = nullptr;
        floah::IIntegralValueDataSource* index = nullptr;
    };

    void YourWidget::setListDataSource(floah::IListDataSource* source)
    {
        if (replaceDataSource(&list, source)) staleData |= ...;
    }

    void YourWidget::setIndexDataSource(floah::IIntegralValueDataSource* source)
    {
        if (replaceDataSource(&index, source)) staleData |= ...;
    }

    void YourWidget::onDataSourceUpdate(floah::DataSource& source)
    {
        if (&source == list)
            staleData |= ...;
        else
            staleData |= ...;
    }
