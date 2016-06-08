If you try to eager load associations in Rails:

```ruby
campaigns = Campaign.includes(:campaigns_kpis).decorate

# $ Campaign Load...
# $ CampaignKpi Load...
```

And try to decorate its association with `<association>.decorate`:

```ruby
campaign = campaigns.first
campaigns_kpis = campaign.campaigns_kpis.decorate

# It will query the association again:
# $ CampaignKpi Load...
```

To avoid this, you can decorate each association instance individually:

```ruby
campaigns_kpis = campaign.campaigns_kpis.map { |campaign_kpi| campaign_kpi.decorate }
```

Or:

```ruby
campaigns_kpis = CampaignKpiDecorator.decorate_collection(campaign.campaigns_kpis)
```

More info:

- [Draper forces DB queries on decorated model's associations](https://github.com/drapergem/draper/issues/646)
