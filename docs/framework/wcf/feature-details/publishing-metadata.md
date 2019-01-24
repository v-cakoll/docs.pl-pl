---
title: Publikowanie metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 1f216fe045dff9eca98c821724372e4426620f47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548810"
---
# <a name="publishing-metadata"></a>Publikowanie metadanych
Usługi Windows Communication Foundation (WCF) publikowanie metadanych przez publikowanie punktów końcowych metadanych. Publikowanie metadanych usługi udostępnia metadane za pomocą standardowych protokołów, takich jak żądania WS-MetadataExchange (MEX) i protokołu HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, w tym mają adres, powiązanie i kontrakt i można ich dodać do hosta usługi przy użyciu konfiguracji lub kodu imperatywnego.  
  
## <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych  
 Aby opublikować punkty końcowe metadanych dla usługi WCF, należy najpierw dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> usługi zachowanie do usługi. Dodawanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpienie umożliwia usłudze uwidaczniają punkty końcowe metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowanie usługi, należy następnie udostępnić punkty końcowe metadanych, które obsługują protokół wymiany Metadanych lub które reagują na żądania HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Używa <xref:System.ServiceModel.Description.WsdlExporter> Aby wyeksportować metadane dla wszystkich punktów końcowych usługi w usłudze. Aby uzyskać więcej informacji na temat eksportowania metadanych z usługi, zobacz [eksportowania i importowania metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Dodaje <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienia jako rozszerzenie do hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Udostępnia implementację dla publikowania protokołów metadanych. Można również użyć <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> można pobrać metadanych usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="mex-metadata-endpoints"></a>Punkty końcowe metadanych wymiany Metadanych  
 Aby dodać punkty końcowe metadanych, które używają protokołu MEX, Dodaj punkty końcowe usługi do hosta usługi używanego przez `IMetadataExchange` kontraktu usługi. Obejmuje WCF <xref:System.ServiceModel.Description.IMetadataExchange> interfejs o tej nazwie kontraktu usługi, używanego jako część modelu programowania usługi WCF. Punkty końcowe usługi WS-MetadataExchange lub MEX punktów końcowych, można użyć jednej z czterech domyślne powiązania, które statycznych metod fabryki uwidaczniają na <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy, aby dopasować domyślne powiązania, używany przez usługi WCF narzędzi, takich jak Svcutil.exe. Można również skonfigurować MEX punktów końcowych metadanych przy użyciu własnego niestandardowego powiązania.  
  
### <a name="http-get-metadata-endpoints"></a>Punkty końcowe HTTP GET metadanych  
 Aby dodać punkt końcowy metadanych do usługi, który odpowiada na żądania HTTP/GET, należy ustawić <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> do `true`. Można również skonfigurować punkt końcowy metadanych, który używa protokołu HTTPS, ustawiając <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> do `true`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Pokazuje, jak skonfigurować usługę WCF w celu publikowania metadanych, aby klienci mogą pobierać metadane za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
 [Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć publikowanie metadanych dla usługi WCF w kodzie, tak aby klienci mogą pobierać metadane za pomocą usługi WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Zobacz także
- [Eksportowanie i importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
