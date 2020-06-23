---
title: Publikowanie metadanych
description: Dowiedz się, jak usługi WCF publikują metadane, publikując co najmniej jeden punkt końcowy metadanych, co umożliwia korzystanie z metadanych przy użyciu protokołów standardowych.
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 2aa6d877db4e5b09b4c594e6e87b63fb6c04703b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244962"
---
# <a name="publishing-metadata"></a>Publikowanie metadanych
Usługi Windows Communication Foundation (WCF) publikują metadane, publikując co najmniej jeden punkt końcowy metadanych. Publikowanie metadanych usługi sprawia, że metadane są dostępne przy użyciu standardowych protokołów, takich jak WS-MetadataExchange (MEX) i HTTP/GET. Punkty końcowe metadanych są podobne do innych punktów końcowych usługi, które mają adres, powiązanie i kontrakt oraz mogą być dodawane do hosta usługi za pomocą konfiguracji lub bezwzględnego kodu.  
  
## <a name="publishing-metadata-endpoints"></a>Publikowanie punktów końcowych metadanych  
 Aby opublikować punkty końcowe metadanych dla usługi WCF, należy najpierw dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie usługi do usługi. Dodanie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> wystąpienia umożliwia usłudze Udostępnianie punktów końcowych metadanych. Po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> zachowania usługi można uwidocznić punkty końcowe metadanych obsługujące protokół MEX lub reagujące na żądania HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>Używa <xref:System.ServiceModel.Description.WsdlExporter> do eksportowania metadanych dla wszystkich punktów końcowych usługi w usłudze. Aby uzyskać więcej informacji na temat eksportowania metadanych z usługi, zobacz [Eksportowanie i Importowanie metadanych](exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>Dodaje <xref:System.ServiceModel.Description.ServiceMetadataExtension> wystąpienie jako rozszerzenie do hosta usługi. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType>Zawiera implementację protokołów publikowania metadanych. Możesz również użyć, <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Aby pobrać metadane usługi w czasie wykonywania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> właściwości.  
  
### <a name="mex-metadata-endpoints"></a>Punkty końcowe metadanych MEX  
 Aby dodać punkty końcowe metadanych używające protokołu MEX, Dodaj punkty końcowe usługi do hosta usługi, który korzysta z `IMetadataExchange` kontraktu usługi. Program WCF zawiera <xref:System.ServiceModel.Description.IMetadataExchange> interfejs o tej nazwie kontraktu usługi, którego można użyć jako części modelu programowania WCF. Punkty końcowe WS-MetadataExchange, lub punkty końcowe MEX mogą korzystać z jednego z czterech domyślnych powiązań, które są uwidaczniane przez statyczne metody fabryki na <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasie w celu dopasowania do domyślnych powiązań używanych przez narzędzia WCF, takie jak Svcutil.exe. Możesz również skonfigurować punkty końcowe metadanych MEX przy użyciu własnego niestandardowego powiązania.  
  
### <a name="http-get-metadata-endpoints"></a>Punkty końcowe metadanych HTTP GET  
 Aby dodać punkt końcowy metadanych do usługi, która odpowiada na żądania HTTP/GET, ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Właściwość na <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> `true` . Istnieje również możliwość skonfigurowania punktu końcowego metadanych korzystającego z protokołu HTTPS przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwości <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> na `true` .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Pokazuje, jak skonfigurować usługę WCF do publikowania metadanych, aby klienci mogli pobrać metadane przy użyciu protokołu WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
 [Instrukcje: publikowanie metadanych dla usługi przy użyciu kodu](how-to-publish-metadata-for-a-service-using-code.md)  
 Pokazuje, jak włączyć Publikowanie metadanych dla usługi WCF w kodzie, aby klienci mogli pobrać metadane przy użyciu protokołu WS-MetadataExchange lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Zobacz też

- [Eksportowanie i importowanie metadanych](exporting-and-importing-metadata.md)
