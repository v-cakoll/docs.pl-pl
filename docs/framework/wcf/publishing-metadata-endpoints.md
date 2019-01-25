---
title: Publikowanie punktów końcowych metadanych
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5de1122a4b603e4c0cd3ae55f3ac7424a7fd77f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626596"
---
# <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych
Usługi Windows Communication Foundation (WCF) publikowanie metadanych przez publikowanie punktów końcowych metadanych. Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i protokołu HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają adres, powiązanie i kontrakt i można ich dodać do hosta usługi przy użyciu konfiguracji lub w kodzie. Aby włączyć publikowanie punktów końcowych metadanych, należy dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowanie do usługi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Pokazuje, jak skonfigurować usługę WCF w celu publikowania metadanych, aby klienci mogą pobierać metadane za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
 [Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć publikowanie metadanych dla usługi WCF w kodzie, tak aby klienci mogą pobierać metadane za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
## <a name="see-also"></a>Zobacz także
- [Publikowanie metadanych](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
