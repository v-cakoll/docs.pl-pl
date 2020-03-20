---
title: Publikowanie i rozwiązywanie nazw elementów równorzędnych
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 4a0787972a61f5700d1e8728be96db8ef9ee749e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623202"
---
# <a name="peer-name-publication-and-resolution"></a>Publikowanie i rozwiązywanie nazw elementów równorzędnych

## <a name="publishing-a-peer-name"></a>Publikowanie nazwy elementu równorzędnego  

 Aby opublikować nowy identyfikator PNRP, element równorzędny wykonuje następujące czynności:  
  
- Wysyła komunikaty publikacji PNRP do sąsiadów pamięci podręcznej (elementy równorzędne, które zarejestrowały identyfikatory PNRP na najniższym poziomie pamięci podręcznej) w celu wysiewu ich pamięci podręcznej.  
  
- Wybiera losowe węzły w chmurze, które nie są jej sąsiadami i wysyła im żądania rozpoznawania nazw PNRP dla własnego identyfikatora P2P. Wynikowy proces określania punktu końcowego nasion buforów losowych węzłów w chmurze z identyfikatorem PNRP elementu równorzędnego publikowania.  
  
Węzły PNRP w wersji 2 nie publikują identyfikatorów PNRP, jeśli rozwiązują tylko inne identyfikatory P2P. Wartość rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly=1 (typ REG_DWORD) określa, że elementy równorzędne używają tylko PNRP do rozpoznawania nazw, nigdy do publikacji nazw. Tę wartość rejestru można również skonfigurować za pomocą zasad grupy.  
  
## <a name="resolving-a-peer-name"></a>Rozwiązywanie nazwy elementu równorzędnego

 Lokalizowanie innych wiązek rysów w sieci lub chmurze PNRP jest procesem składającym się z dwóch faz:  
  
1. Oznaczanie punktu końcowego  
  
2. Rozdzielczość ID PNRP  
  
 W fazie określania punktu końcowego element równorzędny, który próbuje rozpoznać identyfikator PNRP usługi na innym komputerze określa adres IPv6 tego zdalnego elementu równorzędnego.  Zdalny element równorzędny jest tym, który opublikował lub jest skojarzony z identyfikatorem PNRP komputera lub usługi.  
  
 Po potwierdzeniu, że zdalny punkt końcowy został zarejestrowany w chmurze PNRP, żądający element równorzędny w fazie rozpoznawania identyfikatorów PNRP wysyła żądanie do tego równorzędnego punktu końcowego dla identyfikatora PNRP żądanej usługi. Punkt końcowy wysyła odpowiedź potwierdzającą identyfikator PNRP usługi, komentarz i maksymalnie 4 kilobajtów dodatkowych informacji, które żądający element równorzędny może używać do przyszłej komunikacji. Jeśli na przykład żądanym punktem końcowym jest serwer gier, dodatkowe dane rekordu nazwy elementu równorzędnego mogą zawierać informacje o grze, poziomie gry i bieżącej liczbie graczy.  
  
 W fazie określania punktu końcowego PNRP używa iteracyjnego procesu lokalizowania węzła, który opublikował identyfikator PNRP, w którym węzeł wykonujący rozdzielczość jest odpowiedzialny za kontaktowanie się z węzłami, które są kolejno bliżej docelowego identyfikatora PNRP.  
  
 Aby wykonać rozpoznawanie nazw w PNRP, element równorzędny sprawdza wpisy we własnej pamięci podręcznej dla wpisu, który pasuje do docelowego identyfikatora PNRP. Jeśli zostanie znaleziony, element równorzędny wysyła komunikat żądania PNRP do elementu równorzędnego i czeka na odpowiedź. Jeśli wpis dla identyfikatora PNRP nie zostanie znaleziony, element równorzędny wysyła komunikat żądania PNRP do elementu równorzędnego, który odpowiada wpisowi, który ma identyfikator PNRP, który najbardziej pasuje do docelowego identyfikatora PNRP. Węzeł, który odbiera komunikat żądania PNRP sprawdza własną pamięć podręczną i wykonuje następujące czynności:  
  
- Jeśli zostanie znaleziony identyfikator PNRP, żądany element równorzędny punktu końcowego odpowiada bezpośrednio do żądającego elementu równorzędnego.  
  
- Jeśli identyfikator PNRP nie zostanie znaleziony, a identyfikator PNRP w pamięci podręcznej jest bliższy docelowemu identyfikatorowi PNRP, żądany element równorzędny wysyła odpowiedź do żądającego elementu równorzędnego zawierającego adres IPv6 elementu równorzędnego, który reprezentuje wpis z identyfikatorem PNRP, który bardziej odpowiada docelowemu identyfikatorowi PNRP. Za pomocą adresu IP w odpowiedzi, żądający węzeł wysyła inny komunikat żądania PNRP do adresu IPv6, aby odpowiedzieć lub sprawdzić jego pamięci podręcznej.  
  
- Jeśli identyfikator PNRP nie zostanie znaleziony i nie ma żadnych identyfikatorów PNRP w pamięci podręcznej, która jest bliżej docelowego identyfikatora PNRP, żądany element równorzędny wysyła żądającego elementu równorzędnego odpowiedź, która wskazuje ten warunek. Żądający element równorzędny następnie wybiera najbliższy identyfikator PNRP.  
  
Żądający element równorzędny kontynuuje ten proces z kolejnymi iteracjami, ostatecznie lokalizując węzeł, który zarejestrował identyfikator PNRP.  
  
 W <xref:System.Net.PeerToPeer> obszarze nazw istnieje wiele do wielu relacji <xref:System.Net.PeerToPeer.PeerName> między rekordami, które zawierają punkty końcowe i chmury PNRP lub siatki, w których komunikują. Gdy istnieją zduplikowane lub nieaktualne wpisy lub wiele węzłów o tej <xref:System.Net.PeerToPeer.PeerNameResolver> samej nazwie równorzędnej, węzły PNRP mogą uzyskać bieżące informacje przy użyciu klasy. Metody <xref:System.Net.PeerToPeer.PeerNameResolver> używają jednej nazwy elementu równorzędnego, aby uprościć perspektywę do jednego peer-to-many rekordów nazw równorzędnych i tego samego równorzędnego do wielu chmur. Jest to podobne do kwerendy wykonywanej przy użyciu sprzężenia tabeli relacyjnej. Po pomyślnym zakończeniu, obiekt <xref:System.Net.PeerToPeer.PeerNameRecordCollection> rozpoznawania nazw zwraca dla określonej nazwy elementu równorzędnego.  Na przykład nazwa elementu równorzędnego występuje we wszystkich rekordach nazw równorzędnych w kolekcji, uporządkowanych według chmury. Są to wystąpienia nazwy elementu równorzędnego, których dane pomocnicze mogą być wymagane przez aplikację opartą na PNRP.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer>
