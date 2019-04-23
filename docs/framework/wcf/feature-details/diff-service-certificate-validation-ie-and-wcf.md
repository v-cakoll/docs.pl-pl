---
title: Różnice między weryfikacją certyfikatów usług w programach Internet Explorer i WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225924"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Różnice między weryfikacją certyfikatów usług w programach Internet Explorer i WCF
Z powodu różnic pomiędzy sposób programu Internet Explorer i Windows Communication Foundation (WCF) weryfikują certyfikaty usługi, gdy jest używany protokół HTTPS jest to możliwe, że program Internet Explorer nie będzie można uzyskać dostęp do strony pomocy lub Web Services Description Language (WSDL) usługi mimo, że klient WCF jest w stanie pomyślnie wysyłanie komunikatów z punktami końcowymi usługi. Jest to spowodowane programu Internet Explorer sprawdza, czy certyfikat serwera ma `ServerAuthentication` obiektu w flagi rozszerzonego użycia identyfikatorów (OID), natomiast WCF nie wymusza ograniczenia typu. Jeśli program Internet Explorer nie może uzyskać dostęp do strony pomocy usługi lub pliku WSDL usługi, użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do dostępu do metadanych usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Instrukcje: Pobieranie metadanych i implementowanie zgodnej usługi](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
