---
title: Przechowywanie wersji odnajdywania
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 4a1ca07fc6773ce6f883d654abfedab4986341e1
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425253"
---
# <a name="discovery-versioning"></a>Przechowywanie wersji odnajdywania

Ten temat zawiera krótkie omówienie wdrożenia niektóre nowe funkcje odnajdywania. Daje ona również przegląd informacji na temat sposobu wybierz wersję odnajdywania do użycia.

## <a name="discovery-versioning"></a>Przechowywanie wersji odnajdywania

Funkcja odnajdowania obsługuje trzy wersje protokołu WS_Discovery. Odnajdywanie interfejsy API pozwalają na wybór wersji protokołu, którego chcesz użyć. W tym dokumencie krótko opisano ustawienia dotyczące przechowywania wersji.

Następujące klasy odnajdywania powstał <xref:System.ServiceModel.Discovery.DiscoveryVersion> właściwości i podejmij <xref:System.ServiceModel.Discovery.DiscoveryVersion> argumentu w ich konstruktory:

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>

### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005

Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako Konstruktor parametru powoduje, że implementacja przy użyciu wersji April2005 protokołu WS Discovery. Ta wersja odnosi się do opublikowanej wersji specyfikacji protokołu WS Discovery. Na potrzeby współdziałania z starszych aplikacji wykorzystujących April2005 wersję protokołu WS Discovery, można używać tej wersji.

### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11

Domyślna wersja odnajdywania używany przez interfejsy API to <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Jest to standardowy bieżącą wersję protokołu WS Discovery.

## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1

Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jako parametr konstruktora sprawia, że implementacja Użyj Komitet wersję roboczą 1 wersję protokołu WS Discovery. Ta wersja protokołu powinna służyć pod kątem współdziałania z implementacjami dysku CD 1 wersję protokołu WS Discovery.

## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>Obsługa wielu punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście pojedynczą usługę

Można udostępnić wiele punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście jednej usługi. W tym celu należy określić unikatowy adres dla każdego punktu końcowego odnajdywania protokołu UDP. W przykładzie poniżej pokazano, jak to zrobić.

```csharp
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);

newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionApril2005");

serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);
```
