# Configuration

### Constants

Please add the needed values for the plugins in use.

{% code title="constants.typoscript \(defaults\)" %}
```text
plugin.tx_openimmofortypo3 {
    settings {
        x_auth_token = xxx

        url = https://openimmo.xxx.xxx

        assets = /assets/xxx

        list {
            uid = xx
            endpoint = /api/1.0/property/events/{page}
        }

        listRentLiving {
            uid = xx
            endpoint = /api/1.0/property/events/rent/living/{page}
        }

        listRentBusiness {
            uid = xx
            endpoint = /api/1.0/property/events/rent/business/{page}
        }

        listPurchaseLiving {
            uid = xx
            endpoint = /api/1.0/property/events/purchase/living/{page}
        }

        listPurchaseBusiness {
            uid = xx
            endpoint = /api/1.0/property/events/purchase/business/{page}
        }

        detail {
            uid = xx
            endpoint = /api/1.0/property/event/{identifier}
        }

        notepad {
            uid = xx
        }

        request {
            uid = xx
            endpoint = /api/1.0/feedback/event/post
            metadata {
                mail {
                    subject = Objektanfrage expr_123
                    to = g.kathan@zwei14.de
                    cc =
                    bcc =
                    from = whatever@xxx.xx
                }
                feedback {
                    object {
                        identifier = oobj_id
                    }
                }
            }
        }

        tx_form {
            Zwei14\\OpenimmoForTypo3\\Domain\\Finishers\\ImmoSolveCENTRAL\\V30\\Request\\RequestFinisher {
                event {
                    target_metadata {

                    }
                }
                openimmo_feedback {
                    version = 1.2.5
                    sender {
                        name = Name des Immosolve Vermarktungskanals
                        makler_id = Mandantennummer
                    }
                    objekt {
                        portal_obj_id = 12345678
                        anbieter_id = Mandantennummer
                    }
                }
            }
        }

    }
}
```
{% endcode %}

