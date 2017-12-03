---
title: Publikowanie metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 275499a2373bfd1a1713d0b9c7291a117faa9671
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-metadata"></a>Publikowanie metadanych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usługi Publikowanie metadanych przez publikowanie punkty końcowe metadanych. Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, mają address, binding i kontrakt i będzie możliwe ich dodanie do hosta usługi przy użyciu konfiguracji lub imperatywnych kodu.  
  
## <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych  
 Aby opublikować punkty końcowe metadanych dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, należy najpierw dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowania do usługi. Dodawanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpienia umożliwia usłudze do udostępnienia punkty końcowe metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowanie usługi można następnie udostępnić punkty końcowe metadanych, które obsługują protokół MEX lub które odpowiadają na żądania HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Używa <xref:System.ServiceModel.Description.WsdlExporter> Aby wyeksportować metadane dla wszystkich punktów końcowych usługi w usłudze. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Eksportowanie metadanych z usługą, zobacz [eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Dodaje <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienia jako rozszerzenie hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Udostępnia implementację dla publikowania protokołów metadanych. Można również użyć <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> można pobrać metadanych usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="mex-metadata-endpoints"></a>Punkty końcowe metadanych MEX.  
 Aby dodać punkty końcowe metadanych, które używają protokołu MEX, należy dodać punkty końcowe usługi do hosta usługi używanego przez `IMetadataExchange` kontraktu usługi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obejmuje <xref:System.ServiceModel.Description.IMetadataExchange> interfejs o tej nazwie kontraktu usługi, których mogą używać jako część [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania. Punkty końcowe usługi WS-MetadataExchange lub MEX punktów końcowych, można użyć jednej z powiązania cztery domyślne, które udostępniają metod statycznych fabryki na <xref:System.ServiceModel.Description.MetadataExchangeBindings> powiązania domyślne używane przez klasę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] narzędzi, takich jak Svcutil.exe. Można także skonfigurować punkty końcowe metadanych MEX przy użyciu własnego niestandardowego powiązania.  
  
### <a name="http-get-metadata-endpoints"></a>Punkty końcowe metadanych GET protokołu HTTP  
 Aby dodać punkt końcowy metadanych z usługą, która odpowiada na żądania HTTP/GET, ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> do `true`. Istnieje również możliwość skonfigurowania punktu końcowego metadanych, który używa protokołu HTTPS przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> do `true`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Pokazuje, jak skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Publikowanie metadanych, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu usługi `?wsdl` ciągu zapytania.  
  
 [Porady: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć publikowanie metadanych dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi w kodzie, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
