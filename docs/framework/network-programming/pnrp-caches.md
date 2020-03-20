---
title: Pamięci podręczne PNRP
ms.date: 03/30/2017
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
ms.openlocfilehash: 3ed3e11e702c8933b500421de5654b212cdd80d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "64622991"
---
# <a name="pnrp-caches"></a>Pamięci podręczne PNRP
Bufory protokołu PNRP (190) są lokalnymi kolekcjami algorytmicznie wybranych punktów końcowych elementów równorzędnych obsługiwanych w elementów równorzędnych.  
  
## <a name="pnrp-cache-initialization"></a>Inicjowanie pamięci podręcznej PNRP  
 Aby zainicjować pamięć podręczną PNRP lub kolekcję rekordów nazw elementów równorzędnych, po uruchomieniu węzła równorzędnego węzeł może użyć następujących metod:  
  
- Trwałe wpisy pamięci podręcznej, które były obecne po zamknięciu węzła są ładowane z magazynu dysku twardego.  
  
- Jeśli aplikacja korzysta z infrastruktury współpracy P2P, informacje o współpracy są dostępne w Menedżerze kontaktów dla tego węzła.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Skalowanie rozpoznawania nazw elementów równorzędnych za pomocą pamięci podręcznej wielopoziomowej  
 Aby zachować rozmiary pamięci podręcznych PNRP małe, węzły równorzędne użyć pamięci podręcznej wielopoziomowej, w którym każdy poziom zawiera maksymalną liczbę wpisów. Każdy poziom w pamięci podręcznej reprezentuje jedną dziesiątą mniejszą część miejsca numeru identyfikatora PNRP (2<sup>256</sup>). Najniższy poziom w pamięci podręcznej zawiera lokalnie zarejestrowany identyfikator PNRP i inne identyfikatory PNRP, które są numerycznie blisko niego. Ponieważ poziom pamięci podręcznej jest wypełniony maksymalnie 20 wpisami, tworzony jest nowy niższy poziom. Maksymalna liczba poziomów w pamięci podręcznej jest w kolejności log10(Całkowita liczba identyfikatorów PNRP w chmurze). Na przykład dla chmury globalnej z 100 milionów identyfikatorów PNRP, nie ma więcej niż 8 (=log10(100,000,000)) poziomy w pamięci podręcznej i podobną liczbę przeskoków, aby rozwiązać identyfikator PNRP podczas rozpoznawania nazw. Mechanizm ten umożliwia tabelę mieszania rozproszonego, dla której można rozwiązać dowolny identyfikator PNRP, przesyłając dalej komunikaty żądania PNRP do najbliższego elementu równorzędnego, dopóki nie zostanie znaleziony element równorzędny z odpowiednim CPA.  
  
 Aby upewnić się, że rozdzielczość może zakończyć, za każdym razem, gdy węzeł dodaje wpis do najniższego poziomu pamięci podręcznej, zalewa kopię wpisu do wszystkich węzłów w obrębie ostatniego poziomu pamięci podręcznej.  
  
 Wpisy pamięci podręcznej są odświeżane w czasie. Wpisy pamięci podręcznej, które są przestarzałe są usuwane z pamięci podręcznej. W rezultacie tabela mieszania rozproszonych identyfikatorów PNRP jest oparta na aktywnych punktach końcowych, w przeciwieństwie do dns, w którym rekordy adresów i protokół DNS nie dają żadnej gwarancji, że węzeł skojarzony z adresem jest aktywnie w sieci.  
  
## <a name="other-pnrp-caches"></a>Inne pamięci podręczne PNRP  
 Innym trwałym magazynem danych jest lokalna pamięć podręczna.  Oprócz innych obiektów potrzebnych do działania PNRP może zawierać rekordy skojarzone z chmurą PNRP lub sesją współpracy, która jest bezpiecznie publikowana i synchronizowana między wszystkimi członkami chmury. Ten magazyn replikowany reprezentuje widok danych grupy, który powinien być taki sam dla wszystkich członków grupy. Technicznie te obiekty nie są rekordy per se, ale raczej aplikacji, obecności i danych obiektów przeznaczonych dla lokalnej pamięci podręcznej. Użycie chmury PNRP zapewnia, że obiekty są propagowane do wszystkich węzłów w sesji współpracy lub chmurze PNRP.  Replikacja rekordów między członkami chmury używa SSL w celu zapewnienia szyfrowania i integralności danych.  
  
 Gdy element równorzędny łączy się z chmurą, nie odbiera automatycznie danych lokalnej pamięci podręcznej od elementu równorzędnego hosta, do którego się dołączają; muszą subskrybować element równorzędny hosta, aby otrzymywać aktualizacje w danych aplikacji, obecności i obiektu. Po początkowej synchronizacji elementy równorzędne okresowo ponownie synchronizować swoje replikowane magazyny, aby upewnić się, że wszyscy członkowie grupy konsekwentnie mają ten sam widok.  Sesja współpracy lub aplikacje w ramach sesji współpracy mogą również pełnić tę samą funkcję.  
  
 Po rozpoczęciu sesji współpracy dla chmury aplikacje mogą rejestrować elementy równorzędne i rozpocząć publikowanie swoich informacji przy użyciu zabezpieczeń zdefiniowanych przez zakres chmury. Gdy element równorzędny łączy się z chmurą, mechanizmy zabezpieczeń dla chmury są stosowane do elementu równorzędnego, nadając mu zakres, w którym można uczestniczyć.  Jego rekordy mogą być następnie publikowane bezpiecznie w zakresie chmury. Należy zauważyć, że zakres chmury może nie być taki sam jak zakres aplikacji współpracy.  
  
 Elementy równorzędne mogą rejestrować zainteresowanie odbieraniem obiektów od innych rysów. Po zaktualizowaniu obiektu aplikacja współpracy jest powiadamiany i nowy obiekt jest przekazywany do wszystkich subskrybentów aplikacji. Na przykład peer w aplikacji czatu grupowego może zarejestrować zainteresowanie otrzymywaniem informacji o aplikacji, która wyśle wszystkie rekordy czatu jako dane aplikacji.  Dzięki temu może monitorować aktywność czatu w chmurze.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer>
