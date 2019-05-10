---
title: 'Szczegóły usługi CustomPeerResolverService: Rejestracje klienta'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 3d1e1c6493da54bc3ae0e74a33985da59382ea52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619780"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Szczegóły usługi CustomPeerResolverService: Rejestracje klienta
Każdy węzeł w siatce publikuje swoje informacje o punkcie końcowym usługi rozpoznawania nazw za pośrednictwem `Register` funkcji. Usługa rozpoznawania nazw przechowuje te informacje jako rekord rejestracji. Ten rekord zawiera unikatowy identyfikator (identyfikator), a informacje o punkcie końcowym (PeerNodeAddress) dla węzła.  
  
## <a name="stale-records-and-expiration-time"></a>Stare rekordy i czas wygaśnięcia  
 Najlepiej, gdy węzeł opuści siatkę, jego wywoła `Unregister` funkcji, która powoduje, że usługa rozpoznawania nazw usunąć wpis rejestracji. Czasami węzłów zamknięty lub stać się niedostępne, przed wywołaniem `Unregister`, opuścić za rekord starych rejestracji.  
  
 Starych rekordów w usłudze rozpoznawania nazw może spowodować połączenia zakończone niepowodzeniem. Jeśli węzeł podejmuje próbę nawiązania siatki otrzyma informacje o połączeniu starych z usługi rozpoznawania nazw, może potrwać dłużej pomyślnie dołączyć siatkę. Stare rekordy skorzystać z pamięci. Bez wydajny proces oczyszczania pamięci podręcznej, używane do przechowywania rejestracji po pewnym czasie można overflow i awarii usługi rozpoznawania nazw.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Oznacza każdy rekord z czasem wygaśnięcia (Data/godzina) i przechowuje te informacje jako część rekordu. Usługa korzysta z czasu wygaśnięcia do identyfikowania starych rekordów. Niestandardowe implementacje powinien zrobić coś podobnego.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval i CleanupInterval  
 `RefreshInterval` Właściwość <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> definiuje, jak długo rejestracji rekordów flagi card_authenticate_ w tabeli odnośników rejestracji usługi. Czas przekazany do tej właściwości został przekazany do danego rekordu, że rekord staje się nieaktualne i jest oznaczona do usunięcia.  
  
 `CleanupInterval` Właściwość <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> informuje, jak często usługa do wyszukiwania i usuwania starych rejestracji rekordów. `CleanupInterval` Powinna być ustawiona na czas, większa niż lub równa `RefreshInterval` ustawić w usłudze.  
  
 Aby zaimplementować usługi rozpoznawania nazw, należy napisać funkcję obsługi do usuwania przestarzałych rejestracji rekordów. Istnieje kilka sposobów, aby to zrobić:  
  
- **Okresowej konserwacji**: Należy skonfigurować czasomierz go okresowo i przechodzą przez swoim magazynem danych, aby usunąć stare rekordy. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Korzysta z tej metody.  
  
- **Usuwanie pasywnym**: Zamiast aktywnie wyszukiwanie starych rekordów w regularnych odstępach czasu, można zidentyfikować i usuwania starych rekordów, gdy usługa działa już inna funkcja. To może spowodować spowolnienie czas odpowiedzi na żądania od klientów programu rozpoznawania nazw, ale eliminuje to potrzebę czasomierza i bardziej wydajne, jeśli kilka węzły są oczekiwane, aby pozostawić bez wywoływania `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime i odświeżanie  
 Gdy węzeł rejestruje się za pomocą usługi rozpoznawania nazw, otrzymuje <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> obiektu z usługi. Ten obiekt zawiera `RegistrationLifetime` właściwości, które wskazuje na węzeł, czas, jaki ma przed rejestracją wygaśnie i zostanie usunięty w usłudze rozpoznawania nazw. Jeśli na przykład `RegistrationLifetime` to 2 minuty, węzeł musi wywołać `Refresh` w mniej niż 2 minut zapewnienie rekord pozostaje od nowa i nie zostanie usunięta. Po odebraniu usługi rozpoznawania nazw `Refresh` żądań wyszukuje rekord i resetuje czas wygaśnięcia. Odśwież zwraca <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> obiekt z `RegistrationLifetime` właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Mechanizmy rozpoznawania elementów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
