# Rasa

> **TL;DR** : [Rasa Docs](https://rasa.com/docs/rasa/installation/)

## Setting Files

Rasa has a lot of configuration files, in our case, following configuration files should be used.

main:

- domain.yml
- nlu.yml
- stories.yml
- config.yml

optional:

- rules.yml
- actions.py
- endpoints.yml
- credentials.yml

## Current Settings

### nlu.yml

define available intents, synonyms, table, regex

### domain.yml

define enabled intents, responses, actions, entities, slots

> response setting could be listed in other setting files

currently enabled intent:

- greet
- goodbye
- out_of_scope
- check-restler
- check-actuator-health
- check-actuator-info
- check-swagger-api-list
- service-basic-info
- ask_job_health_report
- ask_job_test_report
- ask_jenkins_job_build_number
- check-kmamiz-struct
- kmamiz-high-risk
- kmamiz-high-risk-detail
- test-jenkins-git-info

currently enabled response:

- utter_fallback
- utter_out_of_scope
- utter_out_of_scope_greet
- utter_out_of_scope_bye
- utter_restler
- utter_actuator_health
- utter_actuator_info
- utter_swagger
- utter_service_info
- utter_jenkins_health
- utter_jenkins_test
- utter_jenkins_build
- utter_kmamiz_struct
- utter_kmamiz_risk_service
- utter_kmamiz_risk_service_detail
- utter_jenkins_git_info

### stories.yml

### config.yml

## Optional Settings

### rules.yml

out of scope intents handle:

1. out of scope
2. say hello
3. say goodbye

```yml
- rule: out-of-scope
  steps:
    - intent: out_of_scope
    - action: utter_out_of_scope

- rule: out-of-scope-greet
  steps:
    - intent: greet
    - action: utter_out_of_scope_greet

- rule: out-of-scope-bye
  steps:
    - intent: goodbye
    - action: utter_out_of_scope_bye
```

fallback handle:

```yml
- rule: fallback if not sure
  steps:
    - intent: nlu_fallback
    - action: utter_fallback
```

### actions.py

you can add some function you want to execute here.

### endpoints.yml

you can change rasa action endpoint url here.

### credentials.yml

you can change rasa api endpoint url here.
