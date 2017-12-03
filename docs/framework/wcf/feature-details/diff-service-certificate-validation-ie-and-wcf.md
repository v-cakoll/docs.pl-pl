---
title: "Różnice między weryfikacją certyfikatów usług w programach Internet Explorer i WCF"
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
ms.openlocfilehash: b74886f05ca6dc38c724e02cd091c6dd212c554f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="244db-102">Różnice między weryfikacją certyfikatów usług w programach Internet Explorer i WCF</span><span class="sxs-lookup"><span data-stu-id="244db-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="244db-103">Z powodu różnicy między sposób programu Internet Explorer i [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sprawdzania poprawności certyfikatów usługi użycie protokołu HTTPS jest możliwe, program Internet Explorer nie będzie mógł nawet uzyskać dostęp do strony pomocy lub Web Services Description Language (WSDL) usługi Chociaż [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient jest w stanie pomyślnie wysyłać punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="244db-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="244db-104">Jest to spowodowane programu Internet Explorer sprawdza, czy certyfikat serwera ma `ServerAuthentication` obiekt identyfikatorów (OID), flagi rozszerzonego użycia, podczas gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wymusza takiego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="244db-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="244db-105">Jeśli nie można uzyskać dostępu do strony usługi pomocy lub WSDL usługi jest program Internet Explorer, użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można uzyskać dostępu do metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="244db-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244db-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="244db-106">See Also</span></span>  
 [<span data-ttu-id="244db-107">Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP</span><span class="sxs-lookup"><span data-stu-id="244db-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="244db-108">Porady: Pobieranie metadanych i implementacji usługi zgodne</span><span class="sxs-lookup"><span data-stu-id="244db-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
