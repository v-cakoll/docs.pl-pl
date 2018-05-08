---
title: Publikowanie punktów końcowych metadanych
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 6060850b78c890e043dfaf6f242460bc6e0ef627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych
Usługi Windows Communication Foundation (WCF) publikowanie metadanych przez publikowanie punkty końcowe metadanych. Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają address, binding i kontrakt i będzie możliwe ich dodanie do usługi hosta za pomocą konfiguracji lub w kodzie. Aby włączyć publikowanie punktów końcowych metadanych, należy dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowania do usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Pokazuje, jak skonfigurować [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Publikowanie metadanych, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu usługi `?wsdl` ciągu zapytania.  
  
 [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć publikowanie metadanych dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi w kodzie, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie metadanych](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
