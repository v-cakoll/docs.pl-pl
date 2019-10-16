---
title: Publikowanie punktów końcowych metadanych
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319894"
---
# <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych
Usługi Windows Communication Foundation (WCF) publikują metadane, publikując co najmniej jeden punkt końcowy metadanych. Publikowanie metadanych usługi sprawia, że metadane są dostępne przy użyciu standardowych protokołów, takich jak WS-MetadataExchange (MEX) i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, które mają adres, powiązanie i kontrakt oraz mogą być dodawane do hosta usługi za pomocą konfiguracji lub w kodzie. Aby włączyć Publikowanie punktów końcowych metadanych, należy dodać do usługi zachowanie usługi <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Demonstruje sposób konfigurowania usługi WCF w celu publikowania metadanych, dzięki czemu klienci mogą pobierać metadane przy użyciu protokołu WS-MetadataExchange lub żądania HTTP/GET przy użyciu ciągu zapytania `?wsdl`.  
  
 [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć Publikowanie metadanych dla usługi WCF w kodzie, aby klienci mogli pobrać metadane przy użyciu protokołu WS-MetadataExchange lub żądania HTTP/GET przy użyciu ciągu zapytania `?wsdl`.  
  
## <a name="see-also"></a>Zobacz także

- [Publikowanie metadanych](./feature-details/publishing-metadata.md)
