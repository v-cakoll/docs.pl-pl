---
title: Protokół PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 9f1850ff3a42526de988df032c39aaa916987d25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662664"
---
# <a name="peer-name-resolution-protocol"></a>Protokół PNRP
W środowiskach peer-to-peer elementów równorzędnych użyć systemy rozpoznawania nazw określonych w ustalaniu siebie nawzajem lokalizacje sieciowe (adresy, protokoły i porty) na podstawie nazw lub innych typów identyfikatorów. W przeszłości rozpoznawania nazw równorzędnych ma zostały skomplikowane natury przejściowy łączność, a także innych braków w ramach systemu nazw domen (DNS).  
  
 Platforma sieci Peer-to-Peer Microsoft® Windows® rozwiązuje ten problem za pomocą rozpoznawania protokołu PNRP (Peer Name), bezpieczne, skalowalne i dynamicznego rejestrowania nazw oraz protokołu rozpoznawania nazw, zaprojektowane dla Windows XP, a następnie uaktualnienia w Windows Vista™. Protokół PNRP działa bardzo inaczej od tradycyjnych protokołów rozpoznawania nazw, otwierając ekscytujące nowe możliwości dla deweloperów aplikacji.  
  
 Z PNRP nazwy elementów równorzędnych może być stosowane do komputera, lub poszczególne aplikacje lub usługi na maszynie. Rozpoznawania nazw równorzędnych zawiera adres, port i prawdopodobnie Ładunek rozszerzony. Ten system zalety odporności na uszkodzenia, nie wąskich gardeł i nazwę rozwiązania, które nigdy nie będzie zwracać stare adresy; Wprowadzanie protokołu idealnym rozwiązaniem służącym do lokalizowania użytkowników urządzeń przenośnych.  
  
 Pod względem zabezpieczeń, nazwy elementów równorzędnych może być publikowane jako zabezpieczone (chroniony) lub niezabezpieczone (bez ochrony). Protokół PNRP używa kryptografii klucza publicznego do ochrony nazwy bezpiecznego elementów równorzędnych przed fałszowaniem; zarówno komputerów, jak i usług może być nazwany przy użyciu protokołu PNRP.  
  
Peer Name Resolution Protocol pokazuje następujące właściwości:  
  
-   Rozproszone i niemal całkowicie bez użycia serwera. Serwery są tylko wymagane dla bootstrapping procesu.  
  
-   Bezpieczne publikowanie nazw bez angażowania osób trzecich. W przeciwieństwie do publikacji nazwę DNS PNRP nazwa publikacji jest natychmiastowe i bez ponoszenia kosztów finansowych.  
  
-   Protokół PNRP aktualizacje w w czasie rzeczywistym, co uniemożliwia rozpoznawanie stare adresy.  
  
-   Rozpoznawanie nazw za pośrednictwem protokołu PNRP wykracza poza komputerów, umożliwiając również rozpoznawania nazw dla usług.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>The System.Net.PeerToPeer namespace  
  
-   Funkcje PNRP jest definiowany przez <xref:System.Net.PeerToPeer> przestrzeni nazw w ramach platformy .NET Framework w wersji 3.5. Zapewnia ona zestaw typów, które może służyć do rejestrowania i rozpoznawania nazw równorzędnych za pomocą usługi dostępne PNRP.  
  
-   (PNRP i mechanizmy rozpoznawania elementów równorzędnych niestandardowe można tworzyć i utworzona przy użyciu typów podawany <xref:System.ServiceModel.PeerResolvers> przestrzeni nazw.)  
  
-   Podstawowe typy, które są używane do rejestrowania i rozpoznawania nazw za pomocą usługi PNRP dostępne są następujące:  
  
-   <xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępne chmury PNRP, łącznie z jego zakres.  
  
-   <xref:System.Net.PeerToPeer.PeerName>: Określa nazwę elementu równorzędnego, który może służyć do rejestrowania i następnie rozpoznawania elementu równorzędnego w chmurze.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>: Określa rekord w chmurze PNRP, który zawiera informacje o rejestracji dla elementu równorzędnego, która zawiera punkty końcowe sieci, w których równorzędną można nawiązać połączenie.  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje procesu rejestracji dla nazwy elementów równorzędnych, włączając w to metody, uruchamianie i zatrzymywanie rejestrowania nazw elementów równorzędnych.  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazw równorzędnych do swojej sieci punkty końcowe:, w tym synchroniczne i asynchroniczne metody dla rozpoznawania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)
- [Przykład technologii PeerToPeer](https://go.microsoft.com/fwlink/?LinkID=179571)
