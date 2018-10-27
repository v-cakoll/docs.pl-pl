---
title: Pamięci podręczne PNRP
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 53df90a9bb3da90145ebe30bb274b4ff4950c00f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180968"
---
# <a name="pnrp-caches"></a>Pamięci podręczne PNRP
Elementu równorzędnego protokołu PNRP (Name Resolution Protocol) w pamięci podręcznej są kolekcji lokalnych punktów końcowych algorithmically wybranego elementu równorzędnego w elementu równorzędnego.  
  
## <a name="pnrp-cache-initialization"></a>Inicjowanie pamięci podręcznej PNRP  
 Aby zainicjować pamięci podręcznej PNRP, czyli kolekcji rekordów nazwy elementów równorzędnych, podczas uruchamiania węzła równorzędnego, węzeł można użyć następujących metod:  
  
-   Wpisy trwała pamięć podręczna, jakie były dostępne, gdy węzeł został zamknięty, są ładowane z magazynu danych na dysku twardym.  
  
-   Jeśli aplikacja używa infrastruktury współpracy P2P, informacje o współpracy jest dostępna w Contact Manager dla tego węzła.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Skalowanie rozpoznawania nazw równorzędnych z pamięcią podręczną wielopoziomowe  
 Aby zachować rozmiary pamięci podręczne PNRP małe, węzły równorzędne Użyj wielopoziomowe pamięci podręcznej, w której każdy poziom zawiera maksymalną liczbę wpisów. Każdy poziom w pamięci podręcznej reprezentuje mniejszy jedna dziesiąta część miejsca numer Identyfikator PNRP (2<sup>256</sup>). Najniższy poziom w pamięci podręcznej zawiera lokalnie zarejestrowany identyfikator PNRP i inne identyfikatory PNRP, który numerycznie znajdują się blisko go. Zgodnie z poziomu pamięci podręcznej jest wypełniany maksymalnie 20 wpisów, jest tworzony nowy niższego poziomu. Maksymalna liczba poziomów w pamięci podręcznej jest rzędu kilku log10 (całkowita liczba identyfikatory PNRP w chmurze). Na przykład w przypadku chmury globalnej z identyfikatorami PNRP 100 milionów istnieją nie więcej niż 8 (=log10(100,000,000)) poziomów w pamięci podręcznej i podobną liczbę przeskoków, aby rozwiązać Identyfikator PNRP podczas rozpoznawania nazw. Ten mechanizm pozwala uzyskać tabelę mieszania rozproszonej, dla którego dowolny identyfikator PNRP może zostać rozpoznana przez przekazywanie komunikatów żądania PNRP najbliższy elementów równorzędnych, aż do znalezienia elementu równorzędnego przy użyciu odpowiedniego CPA.  
  
 Aby upewnić się, rozpoznawanie wykonać, każdym węzłem dodaje wpis do najniższego poziomu pamięci podręcznej go floods kopię wejścia do wszystkich węzłów w ramach ostatniego poziomu pamięci podręcznej.  
  
 Wpisy w pamięci podręcznej są odświeżane wraz z upływem czasu. Wpisy w pamięci podręcznej, które są przestarzałe, są usuwane z pamięci podręcznej. Powoduje to, że tabelę skrótów rozproszonych identyfikatory PNRP opiera się na aktywnych punktów końcowych, w odróżnieniu od DNS, w której rekordy adresów i protokołu DNS zapewniają żadnej gwarancji, że węzeł skojarzonych z tym adresem aktywnie znajduje się w sieci.  
  
## <a name="other-pnrp-caches"></a>Inne pamięci podręczne PNRP  
 Innym trwałym magazynie danych jest lokalnej pamięci podręcznej.  Oprócz innych obiektów niezbędnych do działania PNRP może on zawierać rekordów skojarzonych z PNRP w chmurze lub współpracy sesji, która bezpiecznie publikowania i synchronizowane między wszystkie elementy członkowskie w chmurze. Tego replikowanego magazynu reprezentuje widok danych grupy, która powinna być taka sama dla wszystkich członków grupy. Technicznie rzecz biorąc, te obiekty nie są rekordy per se, ale raczej aplikacji obecności i dane obiektów przeznaczonych do lokalnej pamięci podręcznej. Korzystanie z chmury PNRP gwarantuje, że obiekty są przenoszone do wszystkich węzłów w sesji współpracy lub w chmurze PNRP.  Rekord replikacji między elementami członkowskimi chmury używa protokołu SSL w celu zapewnienia integralności danych i szyfrowania.  
  
 Gdy element równorzędny dołącza chmurę, nie automatycznie otrzymują lokalnej pamięci podręcznej danych z elementu równorzędnego hosta, do których one dołączyć; muszą oni subskrypcji na węźle równorzędnym hosta, aby otrzymywać aktualizacje w aplikacji, obecności i dane obiektu. Po początkowej synchronizacji elementów równorzędnych okresowo zsynchronizować ich replikowanych sklepami, aby upewnij się, że wszyscy członkowie grupy spójnie tego samego widoku.  Współpracy sesji lub aplikacje w ramach sesji współpracy mogą również wykonać tę samą funkcję.  
  
 Po sesji współpracy dla chmury, aplikacje mogą zarejestrować elementów równorzędnych i rozpocząć publikowanie ich informacji przy użyciu zabezpieczeń definiowane przez zakres chmury. Gdy element równorzędny dołącza chmurę, mechanizmy zabezpieczeń w chmurze są stosowane na węźle równorzędnym, nadając mu zakresu, w której chcesz wziąć udział.  Rekordy można opublikować bezpiecznie w zakresie chmury. Należy zauważyć, że zakres chmury nie może być taka sama jak zakres aplikacji współpracy.  
  
 Elementy równorzędne można zarejestrować zainteresowanie odbieranie obiektów z innymi elementami równorzędnymi. Gdy obiekt jest aktualizowany, aplikacji współpracy zostanie wysłane powiadomienie, a nowy obiekt jest przekazywany do wszystkich subskrybentów aplikacji. Na przykład elementu równorzędnego w grupie aplikacji rozmów można zarejestrować zainteresowanie odbieranie informacji o aplikacji, która będzie wysyłać je wszystkie rekordy rozmowy jako dane aplikacji.  Dzięki temu na monitorowanie działania rozmowy w chmurze.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer>
