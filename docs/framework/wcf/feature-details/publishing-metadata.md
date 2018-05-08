---
title: Publikowanie metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 6e6c6d10eb0cd03ea2665f1787dba4e09528a141
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="publishing-metadata"></a>Publikowanie metadanych
Usługi Windows Communication Foundation (WCF) publikowanie metadanych przez publikowanie punkty końcowe metadanych. Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, mają address, binding i kontrakt i będzie możliwe ich dodanie do hosta usługi przy użyciu konfiguracji lub imperatywnych kodu.  
  
## <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych  
 Aby opublikować punkty końcowe metadanych dla usługi WCF, należy najpierw dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowania do usługi. Dodawanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpienia umożliwia usłudze do udostępnienia punkty końcowe metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowanie usługi można następnie udostępnić punkty końcowe metadanych, które obsługują protokół MEX lub które odpowiadają na żądania HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Używa <xref:System.ServiceModel.Description.WsdlExporter> Aby wyeksportować metadane dla wszystkich punktów końcowych usługi w usłudze. Aby uzyskać więcej informacji na temat eksportowania metadanych z usługi, zobacz [eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Dodaje <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienia jako rozszerzenie hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Udostępnia implementację dla publikowania protokołów metadanych. Można również użyć <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> można pobrać metadanych usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="mex-metadata-endpoints"></a>Punkty końcowe metadanych MEX.  
 Aby dodać punkty końcowe metadanych, które używają protokołu MEX, należy dodać punkty końcowe usługi do hosta usługi używanego przez `IMetadataExchange` kontraktu usługi. Obejmuje WCF <xref:System.ServiceModel.Description.IMetadataExchange> interfejs o tej nazwie kontraktu usługi, których mogą używać jako część modelu programowania usług WCF. Punkty końcowe usługi WS-MetadataExchange lub MEX punktów końcowych, można użyć jednej z powiązania cztery domyślne, które udostępniają metod statycznych fabryki na <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy odpowiadające powiązania domyślna używana przez narzędzia WCF, takich jak Svcutil.exe. Można także skonfigurować punkty końcowe metadanych MEX przy użyciu własnego niestandardowego powiązania.  
  
### <a name="http-get-metadata-endpoints"></a>Punkty końcowe metadanych GET protokołu HTTP  
 Aby dodać punkt końcowy metadanych z usługą, która odpowiada na żądania HTTP/GET, ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> do `true`. Istnieje również możliwość skonfigurowania punktu końcowego metadanych, który używa protokołu HTTPS przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> do `true`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Pokazuje, jak skonfigurować usługę WCF w celu publikowania metadanych, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
 [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć publikowanie metadanych dla usługi WCF w kodzie, dzięki czemu klienci mogą pobierać za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie i importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
