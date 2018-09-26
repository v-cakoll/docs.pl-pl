---
title: Elementu równorzędnego publikowanie i rozwiązywanie nazw
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 436c84c948a867acedf69af1bc7b3e78c308ce54
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113033"
---
# <a name="peer-name-publication-and-resolution"></a>Elementu równorzędnego publikowanie i rozwiązywanie nazw
## <a name="publishing-a-peer-name"></a>Nazwa elementu równorzędnego publikowania  
 Aby opublikować nowy identyfikator PNRP, peer wykonuje następujące działania:  
  
-   Wysyła komunikaty publikacji PNRP dla swoich sąsiadów pamięci podręcznej (elementów równorzędnych, które zostały zarejestrowane identyfikatory PNRP na najniższym poziomie pamięci podręcznej) w celu umieszczenia ich w pamięci podręcznej.  
  
-   Wybiera losową węzły w chmurze, które nie są jego sąsiadami, a następnie wysyła je żądań rozpoznawania nazw PNRP dla własnego identyfikatora P2P. Wynikowy procesu określania punktu końcowego inicjowania inicjuje pamięci podręcznych losowe węzłów w chmurze o identyfikatorze PNRP publikowania elementów równorzędnych.  
  
-  
  
 PNRP w wersji 2 węzłów nie opublikowano identyfikatory PNRP, jeśli tylko są one rozpoznawanie innych identyfikatorów P2P. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly = 1 wartość rejestru (typu REG_DWORD) określa, że elementy równorzędne tylko używać PNRP do rozpoznawania nazw, nigdy nie dla nazwy publikacji. Ta wartość rejestru można również skonfigurować za pomocą zasad grupy.  
  
## <a name="resolving-a-peer-name"></a>Rozpoznawanie nazwy elementów równorzędnych  
 Lokalizowanie innych elementów równorzędnych w protokole PNRP sieci lub w chmurze to proces obejmuje dwa etapy:  
  
1.  Określenie punktu końcowego  
  
2.  Protokół PNRP identyfikator rozwiązania  
  
 W fazie określenie punktu końcowego elementu równorzędnego, który próbuje rozpoznać Identyfikatora PNRP usługi na innym komputerze określa adres IPv6 ten komputer zdalny.  Komputer zdalny jest opublikowana lub jest skojarzony z Identyfikatorem PNRP komputera lub usługi.  
  
 Po potwierdzeniu, że zdalny punkt końcowy został zarejestrowany do chmury PNRP, żądanie elementu równorzędnego w fazie rozpoznawania Identyfikatora PNRP wysyła żądanie do tego punktu końcowego elementu równorzędnego dla Identyfikatora PNRP żądanej usługi. Punkt końcowy wysyła odpowiedź potwierdzenie Identyfikator PNRP usługi komentarz i maksymalnie 4 kilobajtów dodatkowe informacje, że żądanie komunikacji równorzędnej można użyć do komunikacji w przyszłości. Na przykład jeśli żądanego punktu końcowego jest serwerem gier, danych rekordu nazwę dodatkowego elementu równorzędnego może zawierać informacje o gry, poziom play i bieżącej liczby graczy.  
  
 W fazie określenie punktu końcowego PNRP używa proces iteracyjny do lokalizowania węzeł, który opublikowane jako identyfikator PNRP, w którym węźle wykonywanego rozpoznawania jest odpowiedzialny za skontaktowanie się z węzłów, które są kolejno bliżej docelowy identyfikator PNRP.  
  
 Aby wykonać rozpoznawanie nazw w PNRP, element równorzędny sprawdza, czy wpisy w jego własnej pamięci podręcznej wpisu, który jest zgodna z docelowym Identyfikator PNRP. Jeśli znaleziono element równorzędny wysyła komunikat żądania PNRP dla elementu równorzędnego i czeka na odpowiedź. Jeśli nie znaleziono wpisu dla Identyfikatora PNRP, elementu równorzędnego wysyła komunikat żądania PNRP na węźle równorzędnym, która odpowiada wpis, który ma identyfikator PNRP, który najlepiej pasuje do docelowego identyfikatora PNRP. Węzeł, który odbiera komunikat żądania PNRP sprawdza jego własnej pamięci podręcznej i wykonuje następujące czynności:  
  
-   Jeśli zostanie znaleziony Identyfikator PNRP, peer żądany punkt końcowy odpowiada bezpośrednio na żądanie elementu równorzędnego.  
  
-   Jeśli nie znaleziono Identyfikatora PNRP i Identyfikatorem PNRP w pamięci podręcznej znajduje się bliżej docelowy identyfikator PNRP, żądanego elementu równorzędnego wysyła odpowiedź na żądanie elementu równorzędnego zawierające adres IPv6 elementów równorzędnych, reprezentujący zapis identyfikatorem PNRP ściślej zgodna z docelowym Identyfikator PNRP. W odpowiedzi, korzystając z adresu IP, żądanie węzeł wysyła kolejną wiadomość PNRP żądania na adres IPv6 do odpowiedzi lub sprawdzić jego pamięci podręcznej.  
  
-   Nie znaleziono Identyfikatora PNRP, jeśli nie ma żadnego Identyfikatora PNRP w jego pamięci podręcznej, które znajduje się bliżej docelowy identyfikator PNRP, żądanego elementu równorzędnego wysyła żądanie elementu równorzędnego odpowiedź, która wskazuje na taki stan. Żądanie elementu równorzędnego następnie wybiera najbliższy Identyfikator PNRP.  
  
-  
  
 Żądanie elementu równorzędnego kontynuuje ten proces w z kolejnymi iteracjami ostatecznie lokalizowanie węzeł, który jest zarejestrowany identyfikator PNRP.  
  
 W ramach <xref:System.Net.PeerToPeer> przestrzeni nazw, istnieje relacja wiele do wielu między <xref:System.Net.PeerToPeer.PeerName> rekordy, które zawierają punkty końcowe i chmury PNRP lub siatki, w których komunikują. Istnieją zduplikowane lub nieaktualne wpisy lub wiele węzłów o takiej samej nazwie elementu równorzędnego, PNRP węzłów można uzyskać bieżące informacje przy użyciu <xref:System.Net.PeerToPeer.PeerNameResolver> klasy. <xref:System.Net.PeerToPeer.PeerNameResolver> Metody uprościć z perspektywy rekordy nazwy jednego elementu równorzędnego do wielu elementów równorzędnych i tego samego elementu równorzędnego jeden do wielu chmur, użyj nazwy pojedynczego elementu równorzędnego. Jest to podobne do zapytanie wykonywane przy użyciu tabeli relacyjnej sprzężenia. Po pomyślnym zakończeniu zwraca obiekt rozpoznawania <xref:System.Net.PeerToPeer.PeerNameRecordCollection> dla nazwy określonego elementu równorzędnego.  Na przykład nazwa elementu równorzędnego może mieć miejsce we wszystkich rekordach nazwa elementu równorzędnego w kolekcji, uporządkowane według chmury. Są to wystąpień nazwa elementu równorzędnego, którego dane pomocnicze może zostać wyświetlony przez aplikację na podstawie PNRP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer>
