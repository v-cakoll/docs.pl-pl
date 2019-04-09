---
title: Pobieranie metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: bb415d88c2bae75cb16aa137bdf867eb463afa63
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152402"
---
# <a name="retrieving-metadata"></a>Pobieranie metadanych
Pobieranie metadanych jest proces żądania i pobierania metadanych z punktu końcowego metadanych, takich jak punkt końcowy metadanych WS-MetadataExchange (MEX) lub punkt końcowy metadanych HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Pobieranie metadanych z wiersza polecenia, używając Svcutil.exe  
 Można pobrać metadanych usługi przy użyciu usługi WS-MetadataExchange i HTTP/GET żądań [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie i przekazywanie `/target:metadata` przełącznika i adresu. Svcutil.exe pliki do pobrania metadanych pod określonym adresem i zapisuje plik na dysku. Używa svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia wewnętrznie i ładuje z konfiguracji <xref:System.ServiceModel.Description.IMetadataExchange> konfiguracji punktu końcowego, którego nazwa odpowiada schemat adresu przekazany do Svcutil.exe jako dane wejściowe.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Pobieranie metadanych programowo przy użyciu obiekt klasy MetadataExchangeClient  
 Windows Communication Foundation (WCF) można pobrać metadanych usługi za pomocą standardowych protokołów, takich jak usługi WS-MetadataExchange i żądania HTTP/GET. Obu tych protokołów są obsługiwane przez <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Możesz pobrać metadanych usługi przy użyciu <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu, podając adres punktu końcowego metadanych i powiązanie opcjonalne. Wiązanie używane przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia może być jednym z domyślne powiązania z <xref:System.ServiceModel.Description.MetadataExchangeBindings> klasy statycznej, powiązanie dostarczone przez użytkownika lub powiązanie ładowane z konfiguracji punktu końcowego dla `IMetadataExchange` kontraktu. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Również może rozpoznać odwołania URL protokołu HTTP do korzystania z metadanych <xref:System.Net.HttpWebRequest> typu.  
  
 Domyślnie <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> wystąpienia jest powiązana z pojedynczej <xref:System.ServiceModel.ChannelFactory> wystąpienia. Możesz zmienić lub Zastąp <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> wystąpienia używanego przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> metodę wirtualną. Podobnie, można zmienić lub Zastąp <xref:System.Net.HttpWebRequest> wystąpienia używanego przez <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> na wysyłanie żądań HTTP/GET przez zastąpienie <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> metodę wirtualną.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: używanie programu Svcutil.exe do pobierania dokumentów metadanych](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Pokazuje sposób użycia Svcutil.exe do pobierania dokumentów metadanych.  
  
 [Instrukcje: dynamiczne uzyskiwanie metadanych wiązania przy użyciu klasy MetadataResolver](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Pokazuje sposób użycia <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> można uzyskać metadanych wiązania dynamicznie w czasie wykonywania.  
  
 [Instrukcje: używanie elementu MetadataExchangeClient do pobierania metadanych](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Pokazuje sposób użycia <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> klasy, aby pobrać pliki metadanych do <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> obiekt, który zawiera <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> obiekty do zapisu do plików lub do innych celów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
