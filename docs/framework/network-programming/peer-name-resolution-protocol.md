---
title: Protokół PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428223"
---
# <a name="peer-name-resolution-protocol"></a>Protokół PNRP
W środowiskach równorzędnych elementy równorzędne używają określonych systemów rozpoznawania nazw do rozpoznawania swoich lokalizacji sieciowych (adresów, protokołów i portów) z nazw lub innych typów identyfikatorów. W przeszłości rozpoznawanie nazw równorzędnych było skomplikowane przez z natury przejściową łączność, a także inne niedociągnięcia w systemie nazw domen (DNS).  
  
 Microsoft® Windows® Platforma sieci peer-to-peer rozwiązuje ten problem za pomocą protokołu PNRP (PnRP), bezpiecznego, skalowalnego i dynamicznego protokołu rejestracji nazw i rozpoznawania nazw opracowanego najpierw dla systemu Windows XP, a następnie uaktualnionego w Windows Vista™. PNRP działa zupełnie inaczej niż tradycyjne systemy rozpoznawania nazw, otwierając nowe, ekscytujące możliwości dla twórców aplikacji.  
  
 Za pomocą PNRP nazwy równorzędne mogą być stosowane do maszyny lub poszczególnych aplikacji lub usług na komputerze. Rozpoznawanie nazw elementów równorzędnych zawiera adres, port i ewentualnie rozszerzony ładunek. Zalety tego systemu obejmują odporność na uszkodzenia, brak wąskich gardeł i rozpoznawania nazw, które nigdy nie zwracają starych adresów; co protokół jest doskonałym rozwiązaniem dla lokalizowania użytkowników mobilnych.  
  
 Pod względem bezpieczeństwa nazwy równorzędne mogą być publikowane jako zabezpieczone (chronione) lub niezabezpieczone (niezabezpieczone). PNRP używa kryptografii klucza publicznego do ochrony bezpiecznych nazw elementów równorzędnych przed fałszowaniem; zarówno komputery, jak i usługi mogą być nazwane za pomocą PNRP.  
  
Protokół rozpoznawania nazw elementów równorzędnych pokazuje następujące właściwości:  
  
- Rozproszone i prawie całkowicie bezserwerowe. Serwery są wymagane tylko dla procesu boottrappingu.  
  
- Bezpieczne publikowanie nazw bez udziału osób trzecich. W przeciwieństwie do publikacji nazw DNS publikacja nazwy PNRP jest natychmiastowa i bez kosztów finansowych.  
  
- PnRP aktualizuje się w czasie rzeczywistym, co uniemożliwia rozpoznawanie starych adresów.  
  
- Rozpoznawanie nazw za pośrednictwem PNRP wykracza poza komputery, umożliwiając również rozpoznawanie nazw usług.  
  
## <a name="the-systemnetpeertopeer-namespace"></a>Obszar nazw System.Net.PeerToPeer  
  
- Funkcja PNRP jest definiowana przez obszar <xref:System.Net.PeerToPeer> nazw w wersji .NET Framework w wersji 3.5. Zawiera zestaw typów, które mogą służyć do rejestrowania i rozpoznawania nazw elementów równorzędnych za pomocą dostępnej usługi PNRP.  
  
- (PNRP i niestandardowe programy rozpoznawania nazw elementów równorzędnych można tworzyć i tworzyć wystąpienia przy użyciu typów podanych w obszarze <xref:System.ServiceModel.PeerResolvers> nazw).  
  
- Podstawowe typy używane do rejestrowania i rozpoznawania nazw za pomocą dostępnej usługi PNRP są następujące:  
  
- <xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępną chmurę PNRP, w tym jej zakres.  
  
- <xref:System.Net.PeerToPeer.PeerName>: Definiuje nazwę elementu równorzędnego, który może służyć do rejestrowania, a następnie rozwiązać element równorzędny w chmurze.  
  
- <xref:System.Net.PeerToPeer.PeerNameRecord>: Definiuje rekord w chmurze PNRP, który zawiera informacje rejestracyjne dla elementu równorzędnego, który obejmuje punkty końcowe sieci, w których można skontaktować się z elementem równorzędnym.  
  
- <xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje proces rejestracji nazwy elementu równorzędnego, w tym metody uruchamiania i zatrzymywania rejestracji nazw równorzędnych.  
  
- <xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazwy elementu równorzędnego do jego punktu końcowego sieci, w tym zarówno synchroniczne i asynchroniczne metody rozpoznawania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [Przykłady programowania sieciowego](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
