---
title: Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 329daa39a14ed4c839ecbaa6cf9df036ceabee34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795515"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Zapewnia obsługę dodawania punktu końcowego metadanych do usługi. Te punkty końcowe metadanych mogą odpowiadać na żądania HTTP GET pod adresem URL, który `?wsdl` ma ciąg QueryString i żądania GET WS-transfer zgodnie z definicją w specyfikacji WS-MetadataExchange (Mex). Punkty końcowe MEX implementują <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontrakt.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publikowanie metadanych za pośrednictwem niestandardowego powiązania  
 Punkty końcowe metadanych Get http i HTTPS GET metadanych są włączane przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> właściwości `true`lub <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> . Nie można skonfigurować powiązań dla tych punktów końcowych.  
  
 Umowy, ale mogą być używane z dowolnym punktem końcowym, łącznie z tymi, które używają niestandardowych powiązań <xref:System.ServiceModel.Description.IMetadataExchange> , ponieważ punkty końcowe są identyczne z jakimkolwiek innym punktem końcowym usługi Windows Communication Foundation (WCF). <xref:System.ServiceModel.Description.IMetadataExchange> Jeśli wiesz, jak zmodyfikować konfigurację powiązania dostarczonego przez system lub wiesz <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, jak skonfigurować program, możesz skonfigurować powiązanie do użycia <xref:System.ServiceModel.Description.IMetadataExchange> z punktem końcowym.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Pobieranie metadanych za pośrednictwem niestandardowego powiązania  
 Metadane można pobrać z punktów końcowych HTTP GET i HTTPS GET metadanych przy użyciu standardowych żądań HTTP lub HTTPS GET.  
  
 Aby pobrać metadane z punktu końcowego metadanych MEX, można na ogół użyć jednej ze standardowych powiązań MEX obsługiwanych przez program WCF. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typ i narzędzie Svcutil. exe automatycznie wybiera jedno z tych standardowych powiązań MEX na podstawie adresu określonego punktu końcowego metadanych.  
  
 Jeśli punkt końcowy metadanych MEX używa innego powiązania niż jedno ze standardowych powiązań Mex, można skonfigurować powiązanie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient> kod przy użyciu lub <xref:System.ServiceModel.Description.IMetadataExchange> podając konfigurację punktu końcowego klienta. Narzędzie Svcutil. exe automatycznie ładuje ze swojego pliku <xref:System.ServiceModel.Description.IMetadataExchange> konfiguracji konfigurację punktu końcowego klienta, która ma taką samą nazwę jak schemat identyfikatora URI dla adresu punktu końcowego metadanych.  
  
## <a name="security"></a>Zabezpieczenia  
 Podczas publikowania metadanych za pośrednictwem niestandardowego powiązania upewnij się, że powiązanie zapewnia obsługę zabezpieczeń wymaganą przez Twoje metadane. Na przykład aby zapobiec ujawnieniu informacji i upewnić się, że klient ma uprawnienia do uzyskiwania metadanych, można zwiększyć bezpieczeństwo metadanych i aplikacji przez skonfigurowanie <xref:System.ServiceModel.Description.IMetadataExchange> punktu końcowego, aby wymagał uwierzytelniania i szyfrowania. Przykładowy [punkt końcowy niestandardowej bezpiecznej metadanych](../samples/custom-secure-metadata-endpoint.md) demonstruje ten scenariusz.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług](../securing-services.md)
- [Powiązania elementu WS-MetadataExchange](ws-metadataexchange-bindings.md)
- [Instrukcje: Konfigurowanie powiązania WS-Metadata Exchange niestandardowego](how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Instrukcje: Pobieranie metadanych przez powiązanie inne niż MEX](how-to-retrieve-metadata-over-a-non-mex-binding.md)
