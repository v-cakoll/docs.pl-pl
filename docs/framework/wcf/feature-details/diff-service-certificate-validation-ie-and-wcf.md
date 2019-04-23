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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="76d1e-102">Różnice między weryfikacją certyfikatów usług w programach Internet Explorer i WCF</span><span class="sxs-lookup"><span data-stu-id="76d1e-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="76d1e-103">Z powodu różnic pomiędzy sposób programu Internet Explorer i Windows Communication Foundation (WCF) weryfikują certyfikaty usługi, gdy jest używany protokół HTTPS jest to możliwe, że program Internet Explorer nie będzie można uzyskać dostęp do strony pomocy lub Web Services Description Language (WSDL) usługi mimo, że klient WCF jest w stanie pomyślnie wysyłanie komunikatów z punktami końcowymi usługi.</span><span class="sxs-lookup"><span data-stu-id="76d1e-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="76d1e-104">Jest to spowodowane programu Internet Explorer sprawdza, czy certyfikat serwera ma `ServerAuthentication` obiektu w flagi rozszerzonego użycia identyfikatorów (OID), natomiast WCF nie wymusza ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="76d1e-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="76d1e-105">Jeśli program Internet Explorer nie może uzyskać dostęp do strony pomocy usługi lub pliku WSDL usługi, użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do dostępu do metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="76d1e-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d1e-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76d1e-106">See also</span></span>

- [<span data-ttu-id="76d1e-107">Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP</span><span class="sxs-lookup"><span data-stu-id="76d1e-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="76d1e-108">Instrukcje: Pobieranie metadanych i implementowanie zgodnej usługi</span><span class="sxs-lookup"><span data-stu-id="76d1e-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
