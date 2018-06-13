---
title: 'Szczegóły usługi CustomPeerResolverService: rejestracje klienta'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 1f8b6f5ac3a41fdc7f817553693b0621ee0ea3de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494059"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Szczegóły usługi CustomPeerResolverService: rejestracje klienta
Każdy węzeł w siatce publikuje informacji o punkcie końcowym usługi rozpoznawania nazw za pomocą `Register` funkcji. Usługa rozpoznawania nazw przechowuje te informacje jako rekord rejestracji. Ten rekord zawiera unikatowy identyfikator (RegistrationID) oraz informacje o punkcie końcowym (PeerNodeAddress) dla węzła.  
  
## <a name="stale-records-and-expiration-time"></a>Starych rekordów i czas wygaśnięcia  
 Najlepiej, gdy węzeł opuści siatkę, zostanie wywołany `Unregister` funkcji, co powoduje, że usługa rozpoznawania nazw usunąć wpis rejestracji. Czasami węzłów zamknięty lub stać się niedostępne przed wywołaniem `Unregister`, zostawianie za rekord starych rejestracji.  
  
 Starych rekordów w usłudze rozpoznawania nazw może spowodować połączenia nie powiodło się. Jeśli węzeł podejmuje próbę nawiązania połączenia z siatki odbiera połączenie starych informacji z usługi rozpoznawania nazw, może to trwać dłużej sprzęgać pomyślnie siatkę. Stare rekordy również zajmują pamięć. Bez efektywne procesu oczyszczania pamięci podręcznej, używany do przechowywania rejestracji można ostatecznie przepełnienie i awarii usługi rozpoznawania nazw.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Oznacza każdego rekordu z czas wygaśnięcia (DateTime) i przechowuje te informacje jako część rekordu. Usługa używana czas wygaśnięcia starych rekordów. Należy to zrobić coś podobnego implementacji niestandardowych.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval i CleanupInterval  
 `RefreshInterval` Właściwość <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Określa, jak długo rejestracji rekordów ważność w tabeli odnośników rejestracji usługi. Czas przekazany do tej właściwości został przekazany dla danego rekordu, że rekord staje się przestarzała i została oznaczona do usunięcia.  
  
 `CleanupInterval` Właściwość <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> informuje, jak często usługa do wyszukiwania i usuwania starych rejestracji rekordów. `CleanupInterval` Powinien być ustawiony na czas większa niż lub równa `RefreshInterval` ustawić w usłudze.  
  
 Aby zaimplementować usługi rozpoznawania nazw, należy napisać funkcję obsługi usuwanie starych rejestracji rekordów. Istnieje kilka sposobów, aby to zrobić:  
  
-   **Okresowej konserwacji**: ustawianie czasomierza okresowo wyłączone, a następnie przejdź do Twojego magazynu danych, aby usunąć stare rekordy. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Korzysta z tej metody.  
  
-   **Usuwanie pasywnym**: zamiast aktywnie wyszukiwanie starych rekordów w regularnych odstępach czasu, identyfikowanie i usuwanie starych rekordów przeprowadzania usługi jest już inną funkcję. To może potencjalnie znacznie wydłużyć czas odpowiedzi na żądania od klientów programu rozpoznawania nazw, ale eliminuje potrzebę Czasomierz i może być bardziej efektywne w przypadku kilku węzłów oczekiwany pozostawić bez wywoływania elementu `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime i Odśwież  
 Gdy węzeł rejestruje z usługi rozpoznawania nazw, otrzymuje <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> obiektu z usługi. Ten obiekt zawiera `RegistrationLifetime` właściwość, która wskazuje do węzła, czas, jaki ma przed rejestracji wygasa i jest usuwane przez usługi rozpoznawania nazw. Jeśli na przykład `RegistrationLifetime` 2 minuty, węzeł musi wywołać `Refresh` za zapewnienie rekord pozostaje świeże i nie zostanie usunięta w obszarze 2 minuty. Gdy usługa rozpoznawania nazw odbiera `Refresh` żądań wyszukuje rekordu i resetuje czas wygaśnięcia. Odśwież zwraca <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> obiekt z `RegistrationLifetime` właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Mechanizmy rozpoznawania elementów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
