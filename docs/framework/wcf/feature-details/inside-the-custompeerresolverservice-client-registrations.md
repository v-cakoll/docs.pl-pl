---
title: 'Szczegóły usługi CustomPeerResolverService: rejestracje klienta'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: ce694408edbb40309d1750be49b8414ebcbce3f7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596841"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Szczegóły usługi CustomPeerResolverService: rejestracje klienta
Każdy węzeł siatki publikuje informacje o punkcie końcowym w usłudze rozpoznawania nazw za pomocą `Register` funkcji. Usługa rozpoznawania nazw zapisuje te informacje jako rekord rejestracji. Ten rekord zawiera unikatowy identyfikator (Identyfikator rejestracji) i informacje o punkcie końcowym (PeerNodeAddress) dla węzła.  
  
## <a name="stale-records-and-expiration-time"></a>Stare rekordy i czas wygaśnięcia  
 Najlepiej, gdy węzeł opuszcza siatkę, wywoła `Unregister` funkcję, co spowoduje usunięcie wpisu rejestracji przez usługę rozpoznawania nazw. Czasami węzły są zamykane lub stają się niedostępne przed wywołaniem `Unregister` , pozostawiając poza nieodświeżonym rekordem rejestracji.  
  
 Nieodświeżone rekordy w usłudze rozpoznawania nazw mogą prowadzić do nieudanych połączeń. Jeśli węzeł próbujący połączyć się z siatką otrzymuje stare informacje o połączeniu z usługi rozpoznawania nazw, może to potrwać dłużej. Stare rekordy również zajmują pamięć. Bez skutecznego procesu oczyszczania pamięć podręczna służąca do przechowywania rejestracji może ostatecznie przekroczyć i spowodować awarię usługi rozpoznawania.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>Oznacza każdy rekord z czasem wygaśnięcia (DateTime) i zapisuje te informacje jako część rekordu. Usługa używa czasu wygaśnięcia do identyfikowania starych rekordów. Implementacje niestandardowe powinny być podobne.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval i CleanupInterval  
 `RefreshInterval`Właściwość <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> określa, jak długo rekordy rejestracji są prawidłowe w tabeli odnośników rejestracji usługi. Gdy ilość czasu podanego dla tej właściwości została przekazana dla danego rekordu, ten rekord jest przestarzały i jest oznaczony do usunięcia.  
  
 `CleanupInterval`Właściwość <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> informuje usługę, jak często wyszukiwanie i usuwanie starych rekordów rejestracji. `CleanupInterval`Należy ustawić wartość czasu większą niż lub równą `RefreshInterval` ustawionej w usłudze.  
  
 Aby zaimplementować własną usługę rozpoznawania nazw, należy napisać funkcję konserwacji w celu usunięcia starych rekordów rejestracji. Można to zrobić na kilka sposobów:  
  
- **Okresowa konserwacja**: Ustaw czasomierz, który będzie okresowo wyłączany, i przejdź przez magazyn danych, aby usunąć stare rekordy. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>Używa tego podejścia.  
  
- **Pasywne usuwanie**: zamiast aktywnie wyszukiwania starych rekordów w regularnych odstępach czasu można identyfikować i usuwać stare rekordy, gdy usługa już wykonuje inną funkcję. Może to potencjalnie spowolnić czas odpowiedzi na żądania od klientów programu rozpoznawania nazw, ale eliminuje konieczność czasomierza i może być bardziej wydajny, jeśli oczekuje się, że kilka węzłów zostanie pozostawionych bez wywoływania `Unregister` .  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime i Odśwież  
 Gdy węzeł rejestruje się za pomocą usługi rozpoznawania nazw, otrzymuje <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> obiekt z usługi. Ten obiekt ma `RegistrationLifetime` Właściwość, która wskazuje na węzeł, ile czasu ma przed wygaśnięciem rejestracji i który zostanie usunięty przez usługę rozpoznawania nazw. Jeśli na przykład `RegistrationLifetime` jest to 2 minuty, węzeł musi wywołać `Refresh` w ciągu 2 minut, aby upewnić się, że rekord pozostanie świeży i nie zostanie usunięty. Gdy usługa rozpoznawania nazw odbiera `Refresh` żądanie, wyszukuje rekord i resetuje czas wygaśnięcia. Funkcja Refresh zwraca <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> obiekt z `RegistrationLifetime` właściwością.  
  
## <a name="see-also"></a>Zobacz też

- [Mechanizmy rozpoznawania elementów równorzędnych](peer-resolvers.md)
