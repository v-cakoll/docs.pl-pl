---
title: "Różnice między walidacją certyfikatów usług w programach Internet Explorer i WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12e30d9df9d6bb0a9f8776099951e4354d302ebf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Różnice między walidacją certyfikatów usług w programach Internet Explorer i WCF
Z powodu różnicy między sposób programu Internet Explorer i [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sprawdzania poprawności certyfikatów usługi użycie protokołu HTTPS jest możliwe, program Internet Explorer nie będzie mógł nawet uzyskać dostęp do strony pomocy lub Web Services Description Language (WSDL) usługi Chociaż [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient jest w stanie pomyślnie wysyłać punktów końcowych usługi. Jest to spowodowane programu Internet Explorer sprawdza, czy certyfikat serwera ma `ServerAuthentication` obiekt identyfikatorów (OID), flagi rozszerzonego użycia, podczas gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wymusza takiego ograniczenia. Jeśli nie można uzyskać dostępu do strony usługi pomocy lub WSDL usługi jest program Internet Explorer, użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można uzyskać dostępu do metadanych usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
