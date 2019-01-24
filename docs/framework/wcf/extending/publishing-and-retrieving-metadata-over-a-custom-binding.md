---
title: Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 850f341e933e44d92f130dae90aff5b5c1a882b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639552"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Zapewnia obsługę Dodawanie punktu końcowego metadanych usługi. Te punkty końcowe metadanych mogą odpowiadać na żądania HTTP GET pod adresem URL, który ma `?wsdl` querystring i ROZPOCZYNANIE transferu WS żądania, zgodnie z definicją w specyfikacji WS-MetadataExchange (MEX). Implementowanie MEX punktów końcowych <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontraktu.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publikowanie metadanych za pośrednictwem powiązania niestandardowego  
 Punkty końcowe metadanych HTTP GET i HTTPS GET punkty końcowe metadanych, które są włączone, ustawiając <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> właściwości `true`. Nie można skonfigurować powiązania dla tych punktów końcowych.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange> Kontraktu, jednak może być używany z dowolnego punktu końcowego, w tym te, które używają niestandardowego powiązania, ponieważ <xref:System.ServiceModel.Description.IMetadataExchange> punkty końcowe są takie same jak innych endpoint usługi Windows Communication Foundation (WCF). Jeśli wiesz, jak do modyfikacji konfiguracji powiązania dostarczane przez system lub wiesz, jak skonfigurować <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, a następnie można skonfigurować powiązania do użycia z usługą <xref:System.ServiceModel.Description.IMetadataExchange> punktu końcowego.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Pobieranie metadanych za pośrednictwem powiązania niestandardowego  
 Można pobrać metadanych z Get protokołu HTTP i HTTPS Get punktów końcowych metadanych przy użyciu standardowych żądań HTTP lub HTTPS GET.  
  
 Aby pobrać metadane z punktu końcowego MEX metadane zazwyczaj można użyć jednego z standardowe powiązania MEX obsługiwane przez architekturę WCF. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typu i narzędzia Svcutil.exe automatycznie wybierz jedno z tych standardowych powiązań MEX na podstawie adresu punktu końcowego określonych metadanych.  
  
 Jeśli punkt końcowy metadanych punkcie końcowym MEX używa inne powiązanie niż standardowe powiązania MEX, można skonfigurować powiązania, używany przez <xref:System.ServiceModel.Description.MetadataExchangeClient> przy użyciu kodu lub przez zapewnienie <xref:System.ServiceModel.Description.IMetadataExchange> konfiguracji punktu końcowego klienta. Narzędzia Svcutil.exe automatycznie ładuje z jego pliku konfiguracji <xref:System.ServiceModel.Description.IMetadataExchange> konfiguracji punktu końcowego klienta, który ma taką samą nazwę jak schemat identyfikatora URI dla adresu punktu końcowego metadanych.  
  
## <a name="security"></a>Zabezpieczenia  
 Podczas publikowania metadanych za pośrednictwem powiązania niestandardowego, upewnij się, czy powiązanie zapewnia obsługę zabezpieczeń, która wymaga metadanych. Na przykład, aby zapobiec ujawnieniu informacji i upewnij się, klient ma prawo do uzyskania metadanych, możesz można zabezpieczeniu metadane i aplikacji przez skonfigurowanie usługi <xref:System.ServiceModel.Description.IMetadataExchange> punkt końcowy, aby wymagać uwierzytelniania i szyfrowania. Przykład [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) pokazuje, w tym scenariuszu.  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)
- [Powiązania elementu WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)
- [Instrukcje: Konfigurowanie niestandardowego protokołu WS-Metadata Exchange powiązania](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Instrukcje: Pobieranie metadanych przez MEX powiązanie inne niż](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
