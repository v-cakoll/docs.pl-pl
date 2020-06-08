---
title: Protokół PNRP
description: Dowiedz się więcej na temat protokołu PNRP (Peer Name Resolution Protocol), bezpiecznej, skalowalnej i dynamicznej rejestracji nazw oraz protokołu rozpoznawania nazw.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502226"
---
# <a name="peer-name-resolution-protocol"></a>Protokół PNRP
W środowiskach komunikacji równorzędnej elementy równorzędne używają określonych systemów rozpoznawania nazw do rozwiązywania wszystkich lokalizacji sieciowych (adresów, protokołów i portów) z nazw lub innych typów identyfikatorów. W przeszłości rozpoznawanie nazw elementów równorzędnych zostało skomplikowane przez niezależną łączność przejściową, a także inne braki w ramach systemu nazw domen (DNS).  
  
 Platforma sieci równorzędnej Microsoft® Windows® rozwiązuje ten problem z protokołem rozpoznawania nazw równorzędnych (PNRP), bezpieczną, skalowalną i dynamiczną rejestracją nazw oraz protokołem rozpoznawania nazw, które zostały wcześniej opracowane dla systemu Windows XP, a następnie uaktualnione w™ systemu Windows Vista. Protokół PNRP działa bardzo inaczej niż tradycyjne systemy rozpoznawania nazw, otwierając nowe możliwości dla deweloperów aplikacji.  
  
 W przypadku protokołu PNRP nazwy elementów równorzędnych mogą być stosowane do komputera lub do poszczególnych aplikacji lub usług na komputerze. Rozpoznawanie nazw elementów równorzędnych obejmuje adres, port i prawdopodobnie rozszerzony ładunek. Zalety tego systemu obejmują odporność na uszkodzenia, brak wąskich gardeł i rozdzielczości nazw, które nigdy nie zwracają starych adresów; uczynienie protokołu doskonałym rozwiązaniem do lokalizowania użytkowników mobilnych.  
  
 Pod względem zabezpieczeń nazwy elementów równorzędnych mogą być publikowane jako zabezpieczone (chronione) lub niezabezpieczone (niechronione). Protokół PNRP używa kryptografii klucza publicznego do ochrony bezpiecznych nazw elementów równorzędnych przed fałszowaniem. zarówno komputery, jak i usługi mogą być nazwane przy użyciu protokołu PNRP.  
  
Protokół rozpoznawania nazw równorzędnych demonstruje następujące właściwości:  
  
- Rozpowszechniane i niemal całkowicie bezserwerowe. Serwery są wymagane tylko dla procesu uruchamiania.  
  
- Publikacja z bezpieczną nazwą bez zaangażowania stron trzecich. W przeciwieństwie do publikacji nazw DNS publikacja nazw PNRP jest natychmiastowa i bez kosztu finansowego.  
  
- Aktualizacje protokołu PNRP w czasie rzeczywistym, które uniemożliwiają rozpoznawanie starych adresów.  
  
- Rozpoznawanie nazw za pośrednictwem protokołu PNRP wykracza poza komputery, umożliwiając także rozpoznawanie nazw usług.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Przestrzeń nazw System .NET. PeerToPeer  
  
- Funkcja PNRP jest definiowana przez <xref:System.Net.PeerToPeer> przestrzeń nazw w .NET Framework w wersji 3,5. Zawiera zestaw typów, których można użyć do rejestrowania i rozpoznawania nazw elementów równorzędnych z dostępną usługą PNRP.  
  
- (Protokół PNRP i niestandardowe rozpoznawania elementów równorzędnych można utworzyć i utworzyć przy użyciu typów dostarczonych w <xref:System.ServiceModel.PeerResolvers> przestrzeni nazw).  
  
- Podstawowe typy używane do rejestrowania i rozpoznawania nazw z dostępną usługą PNRP są następujące:  
  
- <xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępną chmurę PNRP, w tym jej zakres.  
  
- <xref:System.Net.PeerToPeer.PeerName>: Definiuje nazwę elementu równorzędnego, który może służyć do rejestrowania i rozpoznawania elementów równorzędnych w chmurze.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>: Definiuje rekord w chmurze PNRP zawierający informacje o rejestracji dla elementu równorzędnego, który obejmuje punkty końcowe sieci, w których można skontaktować się z elementem równorzędnym.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje proces rejestracji dla nazwy elementu równorzędnego, w tym metody uruchamiania i zatrzymywania rejestracji nazw elementów równorzędnych.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazwy równorzędnej do jej punktów końcowych sieci, w tym metod synchronicznych i asynchronicznych do rozwiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Przykłady programowania sieciowego](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
