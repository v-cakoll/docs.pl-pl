---
title: Różnice między walidacją certyfikatów usług w programach Internet Explorer i WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: ecc2b16eae5428e305f5f6096d6d7994256d86c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488689"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Różnice między walidacją certyfikatów usług w programach Internet Explorer i WCF
Z powodu różnicy między sposób programu Internet Explorer i Windows Communication Foundation (WCF) sprawdź poprawność certyfikatów usługi użycie protokołu HTTPS jest to możliwe, że program Internet Explorer nie będzie mógł uzyskać dostępu do strony pomocy lub Web Services Description Language (WSDL) usługi mimo że klienta WCF jest w stanie pomyślnie wysyłanie komunikatów do punktów końcowych usługi. Jest to spowodowane programu Internet Explorer sprawdza, czy certyfikat serwera ma `ServerAuthentication` obiektu w flagi rozszerzonego użycia identyfikatorów (OID), natomiast WCF nie wymusza takiego ograniczenia. Jeśli nie można uzyskać dostępu do strony usługi pomocy lub WSDL usługi jest program Internet Explorer, użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można uzyskać dostępu do metadanych usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
