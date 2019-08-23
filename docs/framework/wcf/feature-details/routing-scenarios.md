---
title: Scenariusze routingu
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: 334e9fe7ca6931f87c75023f3322638b36001b6a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923065"
---
# <a name="routing-scenarios"></a>Scenariusze routingu
Mimo że usługa routingu jest wysoce dostosowywana, może być wyzwaniem do projektowania wydajnej logiki routingu podczas tworzenia nowej konfiguracji od podstaw.  Istnieje jednak kilka typowych scenariuszy, w których obowiązują większość konfiguracji usługi routingu. Chociaż te scenariusze mogą nie dotyczyć konkretnej konfiguracji, zrozumienie, w jaki sposób usługa routingu może być skonfigurowana do obsługi tych scenariuszy, pomoże Ci w zrozumieniu usługi routingu.  
  
## <a name="common-scenarios"></a>Typowe scenariusze  
 Najbardziej podstawowym zastosowaniem usługi routingu jest agregowanie wielu docelowych punktów końcowych w celu zmniejszenia liczby punktów końcowych narażonych na aplikacje klienckie, a następnie użycie filtrów komunikatów do kierowania poszczególnych komunikatów do właściwych miejsc docelowych. Komunikaty mogą być kierowane na podstawie wymagań związanych z przetwarzaniem logicznym lub fizycznym, takich jak typ komunikatu, który musi być przetwarzany przez określoną usługę lub na podstawie dowolnych potrzeb firmy, takich jak zapewnienie priorytetowego przetwarzania komunikatów z określonego źródła. W poniższej tabeli wymieniono niektóre typowe scenariusze i czas ich wystąpienia:  
  
|Scenariusz|Użyj, gdy|  
|--------------|--------------|  
|Przechowywanie wersji usługi|Musisz obsługiwać wiele wersji usługi lub w przyszłości wdrożyć zaktualizowaną usługę|  
|Partycjonowanie danych usługi|Należy podzielić na partycje usługi na wielu hostach|  
|Aktualizacja dynamiczna|Należy dynamicznie ponownie skonfigurować logikę routingu w środowisku uruchomieniowym w celu obsługi zmieniających się wdrożeń usług|  
|Multicast|Należy wysłać jeden komunikat do wielu punktów końcowych|  
|Mostkowanie protokołów|Odbierasz komunikaty za pośrednictwem jednego protokołu transportowego, a docelowy punkt końcowy używa innego protokołu|  
|Obsługa błędów|Należy zapewnić odporność na awarie sieci i błędy komunikacji|  
  
> [!NOTE]
> Wiele z przedstawionych scenariuszy jest specyficznych dla pewnych potrzeb lub wymagań związanych z wymaganiami biznesowymi, dlatego Planowanie obsługi aktualizacji dynamicznych i korzystanie z obsługi błędów może być uważane za najlepsze rozwiązania, ponieważ umożliwiają one modyfikowanie logiki routingu w czasie wykonywania i odzyskiwanie po przejściowych błędach sieci i komunikacji.  
  
### <a name="service-versioning"></a>Przechowywanie wersji usługi  
 Podczas wprowadzania nowej wersji usługi należy zachować poprzednią wersję do momentu przejścia wszystkich klientów do nowej usługi. Jest to szczególnie ważne, jeśli usługa jest długotrwałym procesem, który pobiera dni, tygodnie lub nawet miesiące do ukończenia. Zwykle wymaga to zaimplementowania nowego adresu punktu końcowego dla nowej usługi przy zachowaniu oryginalnego punktu końcowego dla poprzedniej wersji.  
  
 Korzystając z usługi routingu, można uwidocznić jeden punkt końcowy do odbierania komunikatów z aplikacji klienckich, a następnie skierować każdy komunikat do odpowiedniej wersji usługi na podstawie zawartości komunikatu. Najbardziej podstawowa implementacja obejmuje dodanie niestandardowego nagłówka do wiadomości, która wskazuje wersję usługi, przez którą wiadomość ma być przetwarzana. Usługa routingu może używać XPathMessageFilter, aby sprawdzić każdy komunikat dla obecności niestandardowego nagłówka i skierować komunikat do odpowiedniego docelowego punktu końcowego.  
  
 Aby uzyskać instrukcje dotyczące tworzenia konfiguracji wersji usługi, zobacz [How to: Przechowywanie wersji](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)usługi.
  
### <a name="service-data-partitioning"></a>Partycjonowanie danych usługi  
 Podczas projektowania środowiska rozproszonego często pożądane jest rozłożenie obciążenia przetwarzania na wielu komputerach w celu zapewnienia wysokiej dostępności, zmniejszenia obciążenia przetwarzania na poszczególnych komputerach lub zapewnienia dedykowanych zasobów dla określonego podzestawu komunikatów. Chociaż usługa routingu nie zastępuje dedykowanego rozwiązania do równoważenia obciążenia, jego zdolność do wykonywania routingu opartego na zawartości może służyć do kierowania podobnych komunikatów do określonych miejsc docelowych. Na przykład może istnieć wymóg przetworzenia komunikatów od określonego klienta osobno od komunikatów odebranych od innych klientów.  
  
 Aby uzyskać instrukcje dotyczące tworzenia konfiguracji partycjonowania danych usługi, zobacz [How to: Partycjonowanie](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)danych usługi.  
  
### <a name="dynamic-routing"></a>Routing dynamiczny  
 Często należy zmodyfikować konfigurację routingu w celu zaspokojenia zmieniających się potrzeb firmy, takich jak dodawanie trasy do nowszej wersji usługi, zmiana kryteriów routingu lub zmiana docelowego punktu końcowego określonego komunikatu, do którego filtr trasy. Usługa routingu umożliwia wykonywanie tych czynności za pomocą programu <xref:System.ServiceModel.Routing.RoutingExtension>, co pozwala na zapewnienie nowego zastosowano w czasie wykonywania. Nowa konfiguracja zacznie obowiązywać natychmiast, ale ma wpływ tylko na wszystkie nowe sesje przetwarzane przez usługę routingu.  
  
 Aby zapoznać się z instrukcjami dotyczącymi implementacji dynamicznego routingu [, zobacz How to: Aktualizacja](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)dynamiczna.
  
### <a name="multicast"></a>Multicast  
 Podczas routingu wiadomości, zazwyczaj kierowanie poszczególnych komunikatów do jednego określonego docelowego punktu końcowego.  Czasami może być konieczne kierowanie kopii wiadomości do wielu docelowych punktów końcowych. Aby możliwe było przeprowadzenie routingu multiemisji, muszą być spełnione następujące warunki:  
  
- Kształt kanału nie może być odpowiedzią na żądanie (chociaż może być jednokierunkowa lub dupleks), ponieważ aplikacja kliencka może odebrać tylko jedną odpowiedź w odpowiedzi na żądanie.  
  
- Podczas oceny komunikatu wiele filtrów musi zwrócić **wartość true** .  
  
 Jeśli te warunki są spełnione, każdy docelowy punkt końcowy, który jest skojarzony z filtrem zwracającym wartość true, otrzyma kopię komunikatu.  
  
### <a name="protocol-bridging"></a>Mostkowanie protokołów  
 Podczas routingu komunikatów między niepodobnymi protokołami SOAP usługa routingu używa interfejsów API WCF do konwersji komunikatów z jednego protokołu na drugi. Jest to wykonywane automatycznie, gdy punkty końcowe usługi udostępniane przez usługę routingu używają innego protokołu niż punkty końcowe klienta, do których są kierowane komunikaty. To zachowanie można wyłączyć, jeśli używane protokoły nie są standardowe. należy jednak podać własny kod łączący.
  
### <a name="error-handling"></a>Obsługa błędów  
 W środowisku rozproszonym nierzadko występują błędy w sieci lub komunikacji. Bez usługi pośredniczącej, takiej jak usługa routingu, obciążenie związane z obsługą takich błędów znajduje się w aplikacji klienckiej. Jeśli aplikacja kliencka nie zawiera konkretnej logiki do ponawiania próby w przypadku awarii sieci lub komunikacji oraz znajomości lokalizacji alternatywnych, użytkownik może napotkać scenariusze, w których komunikat musi zostać przesłany wiele razy przed pomyślnym przetwarzane przez usługę docelową. Może to prowadzić do niezadowolenia klientów w przypadku aplikacji, ponieważ mogą one być postrzegane jako niezawodne.  
  
 Usługa routingu próbuje naprawić ten scenariusz, zapewniając niezawodne funkcje obsługi błędów dla komunikatów, które napotykają błędy sieci lub komunikacji. Tworząc listę możliwych docelowych punktów końcowych i kojarząc tę listę z każdym filtrem komunikatów, należy usunąć single point of failure poniesione przez posiadanie tylko jednego możliwego miejsca docelowego. W przypadku awarii usługa routingu podejmie próbę dostarczenia komunikatu do następnego punktu końcowego na liście, dopóki nie zostanie dostarczony komunikat, wystąpił błąd braku komunikacji lub wszystkie punkty końcowe zostały wyczerpane.  
  
 Aby uzyskać instrukcje dotyczące konfigurowania obsługi błędów, zobacz [How to: Obsługa](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)błędów.
  
### <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Instrukcje: Partycjonowanie danych usługi](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Instrukcje: Aktualizacja dynamiczna](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Instrukcje: Obsługa błędów](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
