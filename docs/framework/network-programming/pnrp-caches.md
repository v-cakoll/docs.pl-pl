---
title: "Pamięci podręczne PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270068d9-1b6b-4eb9-9e14-e02326bb88df
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 919a789b1ae3e5900fe8bd79f5c8b127d81bb2e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pnrp-caches"></a>Pamięci podręczne PNRP
Pamięci podręcznych protokołu PNRP (Name Resolution) elementu równorzędnego są kolekcjami lokalnymi algorithmically wybranego elementu równorzędnego punktów końcowych w elementu równorzędnego.  
  
## <a name="pnrp-cache-initialization"></a>Inicjowanie pamięci podręcznej PNRP  
 Aby zainicjować pamięci podręcznej PNRP lub kolekcja rekordu nazw elementów równorzędnych, po uruchomieniu węzła równorzędnego, węzłem można użyć następujących metod:  
  
-   Wpisy trwałej pamięci podręcznej, które były dostępne, gdy węzeł została zamknięta są ładowane z magazynu danych na dysku twardym.  
  
-   Jeśli aplikacja używa infrastruktury współpracy P2P, informacje o współpracy jest dostępna w Menedżerze kontaktu dla tego węzła.  
  
## <a name="scaling-peer-name-resolution-with-a-multi-level-cache"></a>Skalowanie rozpoznawania nazw równorzędnych z wielopoziomowe pamięci podręcznej  
 Aby zachować małych rozmiarów buforów PNRP, węzły równorzędne Użyj wielopoziomowe pamięci podręcznej, w którym każdy poziom zawiera maksymalną liczbę wpisów. Każdy poziom w pamięci podręcznej reprezentuje mniejszy dziesiątego jedną część miejsca numer Identyfikator PNRP (2<sup>256</sup>). Na najniższym poziomie w pamięci podręcznej zawiera lokalnie zarejestrowany identyfikator PNRP i innych PNRP identyfikatory numeryczne bliski go. Zgodnie z poziomu pamięci podręcznej jest wypełniony maksymalnie 20 wpisów, jest tworzony nowy niższego poziomu. Maksymalna liczba poziomów w pamięci podręcznej jest rzędu log10 (całkowita liczba identyfikatorów PNRP w chmurze). Na przykład dla globalnych chmury chronionej za pomocą 100 milionów identyfikatorów PNRP, nie ma nie więcej niż 8 (=log10(100,000,000)) poziomy w pamięci podręcznej i podobne liczbę przeskoków w celu rozpoznania identyfikator PNRP podczas rozpoznawania nazw. Mechanizm ten umożliwia dla tabeli rozproszonej wyznaczania wartości skrótu, dla którego można rozwiązać przekazywania komunikatów żądania PNRP najbliższy równorzędnej, aż do znalezienia równorzędnego z odpowiedniego CPA dowolnego Identyfikator PNRP.  
  
 Aby upewnić się, czy rozdzielczość może zostać ukończony, zawsze węzła dodaje wpis do najniższego poziomu swojej pamięci podręcznej, jego floods kopię zapisu do wszystkich węzłów w pamięci podręcznej ostatniego poziomu.  
  
 Wpisy w pamięci podręcznej są odświeżane w czasie. Wpisy w pamięci podręcznej, które są przestarzałe, są usuwane z pamięci podręcznej. Wynik jest, że tablicy skrótów rozproszonej identyfikatorów PNRP opiera się na aktywnych punktów końcowych, w odróżnieniu od DNS, w którym rekordy adresu i protokołu DNS zapewniają ma gwarancji, że węzeł skojarzony z adresem aktywnie znajduje się w sieci.  
  
## <a name="other-pnrp-caches"></a>Inne pamięci podręcznych PNRP  
 Inny magazyn danych jest lokalnej pamięci podręcznej.  Oprócz innych obiektów niezbędnych do działania usługi PNRP mogą one obejmować rekordy skojarzone z PNRP chmury lub współpracy sesji bezpiecznie publikowana i synchronizowane między wszystkich członków z chmury. Ten magazyn replikowanych reprezentuje widok danych grupy, która powinna być taka sama dla wszystkich członków grupy. Z technicznego punktu widzenia te obiekty nie są rekordy per se, ale raczej aplikacji, obecności i przeznaczonych dla lokalnej pamięci podręcznej danych obiektu. Korzystanie z chmury PNRP gwarantuje, że obiekty są przenoszone do wszystkich węzłów w sesji współpracy lub w chmurze usługi PNRP.  Rekord replikacji między elementami członkowskimi chmury używa protokołu SSL w celu zapewnienia szyfrowania i integralność danych.  
  
 Gdy element równorzędny dołącza chmurę, nie automatycznie otrzymują lokalnej pamięci podręcznej danych z elementu równorzędnego hostów, do których one dołączyć; mają one subskrybować równorzędnej hosta otrzymywać aktualizacje w aplikacji, obecności i dane obiektu. Po początkowej synchronizacji elementów równorzędnych okresowo zsynchronizować ich replikowanych magazynów, aby upewnić się, czy wszyscy członkowie grupy spójnie mieć tego samego widoku.  Współpraca z sesji lub aplikacji w ramach sesji współpracy może także przeprowadzić tej samej funkcji.  
  
 Po sesji współpracy dla chmury, aplikacje można zarejestrować elementów równorzędnych i rozpocząć publikowanie informacji o ich przy użyciu zabezpieczeń określają zakres chmury. Gdy elementu równorzędnego dołącza chmurę, mechanizmy zabezpieczeń dla chmury są stosowane do elementów równorzędnych, nadanie mu zakresu, w którym do udziału.  Rekordy można opublikować bezpiecznie w zakresie chmury. Należy pamiętać, że zakres chmury nie może być taka sama jak zakres aplikacji współpracy.  
  
 Elementy równorzędne można zarejestrować zainteresowanie odbierania obiektów z innych elementów równorzędnych. Gdy zaktualizowano obiekt aplikacji współpracy jest powiadamiany, a nowy obiekt jest przekazywana do wszystkich subskrybentów aplikacji. Na przykład elementu równorzędnego w grupie aplikacji rozmów można zarejestrować zainteresowanie odbieranie informacji o aplikacji, która będzie wysyłać go wszystkie rekordy rozmów jako dane aplikacji.  Dzięki temu monitorowania aktywności rozmów w chmurze.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer>
