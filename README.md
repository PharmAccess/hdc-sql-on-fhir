 # SQL-on-FHIR playground

## Context
We take the MomCare project from PharmAccess Foundation as a use-case for developing [SQL-on-FHIR](https://github.com/FHIR/sql-on-fhir-v2/discussions/60). Read more on MomCare [here](https://www.pharmaccess.org/stories/care-bundles/) and [here](https://www.pharmaccess.org/wp-content/uploads/2021/02/MOMcare_data-insights-v3-002.pdf).  Objective of this use-case is to create standardized SQL-on-FHIR queries to monitor the journeys of pregnant mothers in low- and middle income countries using the [WHO guidelines](https://apps.who.int/iris/bitstream/handle/10665/250796/9789241549912-eng.pdf).

In essence, we want to query whether certain activities (`encounter`, `procedure`) have taken place at predefined times during the pregnancy. The care model aims to incentivise pregnant mothers and antenatal clinics to regular check-ups and visits, which have been shown to reduce infant and maternal mortality.

## Synthetic pregnancy data
After [installing Syntea](https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running) we generate synthetic data of pregnancies in the bulk data format as follows:

```bash
touch ./synthea.properties
# set exporter.fhir.bulk_data = true with a text editor

java -jar synthea-with-dependencies.jar -c synthea.properties -p 1000 -g F -m Pregnancy
```

## Playground

Notebooks are included under `test`.