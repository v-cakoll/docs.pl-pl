---
title: Publikowanie nazw elementów równorzędnych i rozwiązanie
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4e64f1293da18823166883a869ac6377908c9e72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="peer-name-publication-and-resolution"></a>Publikowanie nazw elementów równorzędnych i rozwiązanie
## <a name="publishing-a-peer-name"></a>Nazwa elementu równorzędnego publikowania  
 Aby opublikować nowy identyfikator PNRP, peer wykonuje następujące działania:  
  
-   Wysyła komunikaty publikacji PNRP dla swoich sąsiadów pamięci podręcznej (elementów równorzędnych zarejestrowanych identyfikatorów PNRP na najniższym poziomie pamięci podręcznej) do umieszczenia ich w pamięci podręcznej.  
  
-   Wybiera węzły losowe w chmurze, które nie są jej sąsiadami i wysyła je żądań rozpoznawania nazw PNRP dla własnego identyfikatora P2P. Wynikowa procesu określania punktu końcowego nasion pamięci podręczne losowe węzłów w chmurze o identyfikatorze publikowania elementów równorzędnych PNRP.  
  
-  
  
 Węzły w wersji 2 PNRP nie publikować identyfikatorów PNRP, jeśli są one tylko rozpoznawanie innych identyfikatorów P2P. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly = 1 wartość rejestru (typ: REG_DWORD) określa, że elementy równorzędne tylko używać PNRP do rozpoznawania nazw, nigdy nie dla nazwy publikacji. Ta wartość rejestru można również skonfigurować za pomocą zasad grupy.  
  
## <a name="resolving-a-peer-name"></a>Rozpoznawanie nazwy elementu równorzędnego  
 Lokalizowanie innych elementów równorzędnych w protokole PNRP sieci lub w chmurze jest procesem, które składają się z dwóch faz:  
  
1.  Określenie punktu końcowego  
  
2.  Usługa PNRP identyfikator rozwiązania  
  
 W fazie określenie punktu końcowego elementu równorzędnego, który próbuje rozpoznać Identyfikatora PNRP usługi na innym komputerze określa ten komputer zdalny adres IPv6.  Komputer zdalny jest opublikowana lub jest skojarzony z Identyfikatorem PNRP komputera lub usługi.  
  
 Po potwierdzeniu, że zdalny punkt końcowy został zarejestrowany w chmurze usługi PNRP, żądanie elementu równorzędnego w fazie rozpoznawania Identyfikator PNRP wysyła żądanie do tego punktu końcowego elementu równorzędnego dla Identyfikatora PNRP żądanej usługi. Punkt końcowy wysyła odpowiedź potwierdzenie Identyfikator PNRP usługi komentarz, oraz maksymalnie 4 kilobajtów dodatkowe informacje, że żądanie elementu równorzędnego można używać do komunikacji w przyszłości. Na przykład jeśli żądanego punktu końcowego jest serwerem gier, dane rekordu nazwa dodatkowego elementu równorzędnego mogą zawierać informacje o gry, poziom play, a bieżąca liczba odtwarzaczy.  
  
 W fazie określenie punktu końcowego PNRP używa procesem iteracyjnym do lokalizowania węzeł, który jest opublikowany Identyfikator PNRP, w którym węzeł rozpoznawania jest odpowiedzialny za skontaktowanie się z węzłów, które są kolejno bliżej docelowy identyfikator PNRP.  
  
 Przeprowadzać rozpoznawania nazw w protokole PNRP, peer sprawdza wpisy w bufor wpisu, który jest zgodna z docelowym Identyfikator PNRP. Jeśli znaleziono element równorzędny wysyła komunikat żądania PNRP dla elementu równorzędnego i czeka na odpowiedź. Jeśli wpis dla Identyfikatora PNRP nie zostanie znaleziony, element równorzędny wysyła komunikat żądania PNRP dla elementu równorzędnego umożliwiająca wpisu, który ma identyfikator PNRP, najlepiej pasujący element docelowy identyfikator PNRP. Węzeł, który odbiera komunikat żądania PNRP sprawdza własnej pamięci podręcznej i wykonuje następujące czynności:  
  
-   Jeśli zostanie znaleziony Identyfikator PNRP, peer żądanego punktu końcowego odpowiada bezpośrednio na żądanie elementu równorzędnego.  
  
-   Nie znaleziono Identyfikatora PNRP, Identyfikatora PNRP w pamięci podręcznej jest bliżej docelowy identyfikator PNRP żądanego elementu równorzędnego wysyła odpowiedź na żądanie elementu równorzędnego zawierający adres IPv6 elementu równorzędnego reprezentujący wpisu z Identyfikatorem PNRP bardziej ściśle zgodna z docelowym Identyfikator PNRP. Przy użyciu adresu IP, w odpowiedzi, węzeł żądania wysyła kolejną wiadomość PNRP żądania na adres IPv6 do odpowiedzi lub zbadać pamięci podręcznej.  
  
-   Nie znaleziono Identyfikatora PNRP, jeśli nie ma żadnych Identyfikator PNRP w swojej pamięci podręcznej zbliżonej do docelowej Identyfikator PNRP, żądanego elementu równorzędnego wysyła żądanie elementu równorzędnego odpowiedzi, który wskazuje na taki stan. Żądanie elementu równorzędnego następnie wybiera najbliższy Identyfikator PNRP.  
  
-  
  
 Z kolejnych iteracji, proces jest kontynuowany wysyłającego żądanie elementu równorzędnego po pewnym czasie lokalizowanie węzeł, który jest zarejestrowany identyfikator PNRP.  
  
 W ramach <xref:System.Net.PeerToPeer> przestrzeni nazw, istnieje relacja wiele do wielu między <xref:System.Net.PeerToPeer.PeerName> rekordy, które zawierają punkty końcowe i chmur PNRP lub siatki, w których komunikują się. Gdy istnieją zduplikowane lub przestarzałych wpisów lub wiele węzłów o tej samej nazwie elementu równorzędnego, węzły PNRP mogą uzyskać bieżące informacje przy użyciu <xref:System.Net.PeerToPeer.PeerNameResolver> klasy. <xref:System.Net.PeerToPeer.PeerNameResolver> Metody upraszczanie z perspektywy jednej równorzędnej peer do wielu rekordów i tego samego równorzędnej jeden do wielu chmur przy użyciu nazwę pojedynczego elementu równorzędnego. Efekt jest podobny do zapytania wykonywane przy użyciu sprzężenia relacyjne tabeli. Po pomyślnym zakończeniu zwraca obiekt rozpoznawania <xref:System.Net.PeerToPeer.PeerNameRecordCollection> nazwę określonego elementu równorzędnego.  Na przykład nazwa elementu równorzędnego wystąpiłyby we wszystkich rekordach nazwa elementu równorzędnego w kolekcji, uporządkowanych według chmury. Są to wystąpień nazwa elementu równorzędnego, którego dane pomocnicze zażąda aplikacją opartą na protokole PNRP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer>
