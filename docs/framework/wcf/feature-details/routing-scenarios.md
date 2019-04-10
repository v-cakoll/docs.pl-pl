---
title: Scenariusze routingu
ms.date: 03/30/2017
helpviewer_keywords:
- rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: fa5d588211cfe40cde9e9db3161a931e3287cd39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223830"
---
# <a name="routing-scenarios"></a>Scenariusze routingu
Usługa routingu jest w dużym stopniu dostosowywane, może być wyzwaniem wymagającym projektować wydajne logikę routingu, tworząc nową konfigurację od podstaw.  Istnieje jednak kilka typowych scenariuszy, które należy wykonać w większości konfiguracji usługa routingu. Te scenariusze mogą nie dotyczą bezpośrednio do określonej konfiguracji, zrozumienie, jak można skonfigurować do obsługi tych scenariuszy, usługa routingu będzie pomocy można zrozumieć usługa routingu.  
  
## <a name="common-scenarios"></a>Typowe scenariusze  
 Jest to najbardziej podstawowa funkcja usługi Routing Agreguj wiele docelowych punktów końcowych w celu zmniejszenia liczby punktów końcowych dostępne dla aplikacji klienckich, a następnie użyj filtry komunikatów przekierowywać każdy komunikat do odpowiedniego miejsca docelowego. Wiadomości mogą być przesyłane na podstawie wymagań przetwarzania logiczny lub fizyczny, takich jak typ komunikatu, który musi być przetwarzane przez określonej usługi lub na podstawie potrzeb biznesowych dowolnego np priorytet przetwarzania komunikatów z określonego źródła. W poniższej tabeli wymieniono niektóre typowe scenariusze i po ich napotkaniu:  
  
|Scenariusz|Kiedy używać|  
|--------------|--------------|  
|Przechowywanie wersji usługi|Wymagana jest obsługa wielu wersji usługi lub mogą wdrażać usługi zaktualizowane w przyszłości|  
|Partycjonowanie danych usługi|Należy tworzyć partycje usługi na wielu hostach|  
|Aktualizacja dynamiczna|Należy ponownie skonfigurować dynamicznie logikę routingu w czasie wykonywania w celu obsługi zmieniających wdrożenia usług|  
|Multiemisji|Konieczne jest wysłanie jednego komunikatu do wielu punktów końcowych|  
|Mostkowanie protokołu|Odbieranie komunikatów za pośrednictwem protokołu transportu jeden, a docelowy punkt końcowy korzysta inny protokół|  
|Obsługa błędów|Należy podać odporność na awarie sieci i problemy z komunikacją|  
  
> [!NOTE]
>  Chociaż wiele scenariuszy prezentowane są specyficzne dla niektórych wymagań biznesowych lub wymagań dotyczących przetwarzania, planowania do obsługi aktualizacji dynamicznych i korzystanie z obsługi błędów można często uznawany za jako najlepsze rozwiązania w zakresie umożliwiają modyfikowanie logikę routingu w czasie wykonywania i odzyskiwanie po niepowodzeniach przejściowy sieci i komunikacji.  
  
### <a name="service-versioning"></a>Przechowywanie wersji usługi  
 Wprowadzając nową wersję usługi często należy zachować poprzednią wersję, aż wszyscy klienci zostały przeniesione do nowej usługi. Jest to szczególnie istotne, jeśli usługa jest proces długotrwałych, który trwa dni, tygodni lub nawet miesięcy. Zwykle wymaga to wdrażanie nowego adresu punktu końcowego dla nowej usługi przy zachowaniu oryginalnej punktu końcowego dla wcześniejszych wersji.  
  
 Za pomocą usługi routingu, należy udostępnić jeden punkt końcowy, aby odbierać komunikaty z aplikacji klienckich, a następnie kierować każdy komunikat do wersji prawidłowe usługi na podstawie zawartości komunikatu. Najbardziej podstawowa implementacja polega na dodawanie niestandardowego nagłówka do komunikat, który wskazuje wersję usługi, która wiadomość ma zostać przetworzony przez. Usługa routingu umożliwia XPathMessageFilter sprawdzić każdy komunikat na obecność niestandardowy nagłówek i kierowanie komunikat do odpowiedniego miejsca docelowego punktu końcowego.  
  
 Użyty do utworzenia konfiguracji przechowywanie wersji usługi kroki opisane w artykule [How to: Przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).
  
### <a name="service-data-partitioning"></a>Partycjonowanie danych usługi  
 Podczas projektowania środowisku rozproszonym, często jest pożądane, aby rozłożyć obciążenie związane z przetwarzaniem na wielu komputerach w celu zapewnienia wysokiej dostępności, zmniejsz obciążenie na pojedynczych komputerach lub w celu udostępnienia dedykowanych zasobów dla określonych podzestawów wiadomości. Gdy usługa routingu nie zastępuje dedykowane rozwiązania do równoważenia obciążenia, możliwość wykonywania routingu na podstawie zawartości może służyć do przesyłania wiadomości w przeciwnym razie podobne do określonych miejsc docelowych. Na przykład masz wymaganie przetwarzania komunikatów z określonego klienta, niezależnie od komunikatów odebranych z innych klientów.  
  
 Użyty do utworzenia partycji konfiguracji usługi dane kroki opisane w artykule [How to: Partycjonowanie danych usługi](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md).  
  
### <a name="dynamic-routing"></a>Routing dynamiczny  
 Często jest pożądane modyfikowanie konfiguracji routingu w celu zaspokojenia zmieniających się potrzeb biznesowych, takich jak dodawanie trasy do nowszej wersji usługi, zmiana kryteriów routingu lub zmianę docelowego punktu końcowego szczegółowy komunikat o błędzie, który filtr przekierowuje do. Usługa routingu umożliwia tym za pośrednictwem <xref:System.ServiceModel.Routing.RoutingExtension>, który pozwala na dostarczenie nowej RoutingConfiguration w czasie wykonywania. Nowa konfiguracja zaczyna obowiązywać natychmiast, ale ma wpływ tylko na wszystkie nowe sesje przetworzone przez usługę Routing.  
  
 Używany do implementowania routingu dynamicznego kroki opisane w artykule [How to: Aktualizacja dynamiczna](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md).
  
### <a name="multicast"></a>Multiemisji  
 Gdy routing komunikatów, zazwyczaj można routingu każdy komunikat do jednego określonego miejsca docelowego punktu końcowego.  Jednak czasami konieczne może być kierować kopię wiadomości do wielu docelowych punktów końcowych. Aby przeprowadzić routing multiemisji, muszą być spełnione następujące warunki:  
  
-   Kształtu kanału nie może być "żądanie-odpowiedź" (chociaż może on być jednokierunkowe lub dupleksowy,), ponieważ "żądanie-odpowiedź" określającemu, że tylko jedną odpowiedź może zostać odebrana przez aplikację klienta w odpowiedzi na żądanie.  
  
-   Wiele filtrów musi zwracać **true** podczas oceniania wiadomości.  
  
 Jeśli te warunki są spełnione, każdy docelowy punkt końcowy, który jest skojarzony z filtrem, który zwraca wartość true, otrzyma kopię wiadomości.  
  
### <a name="protocol-bridging"></a>Mostkowanie protokołu  
 Gdy routing wiadomości między różnych protokołów SOAP, usługa routingu używa interfejsów API WCF, aby przekonwertować komunikatu z jednego protokołu. Dzieje się automatycznie po udostępniane punkty końcowe: usługa w przy użyciu usługi Routing niż punkty końcowe: klient, który wiadomości są kierowane do innego protokołu. Istnieje możliwość wyłączyć to zachowanie, jeśli używanych protokołów nie są standardowe; Jednakże następnie należy podać własne mostkowanie kodu.
  
### <a name="error-handling"></a>Obsługa błędów  
 W środowisku rozproszonym nie jest niczym niezwykłym występują przejściowe awarie sieci lub komunikacji. Bez pośredniczącej usługi takie jak usługa routingu ciężar obsługi tych błędów znajduje się w aplikacji klienckiej. Jeśli aplikacja kliencka zawiera logikę specyficzną dla, aby ponowić próbę w przypadku sieci lub problemy z komunikacją i wiedzy na temat alternatywnych lokalizacji, użytkownik może wystąpić sytuacje, w którym komunikatu musi zostać przesłany wielokrotnie zanim zostanie pomyślnie przetworzone przez usługę docelowego. Może to prowadzić do klientów głównym powodem niezadowolenia z aplikacją, jako może być traktowany jako wiarygodne.  
  
 Usługa routingu próbuje rozwiązać w tym scenariuszu, udostępniając błędów grubych funkcje obsługi komunikatów, które występują w sieci lub błędy związane z komunikacji. Tworząc listę możliwych docelowych punktów końcowych i kojarzenie tej listy z każdego filtr komunikatów, należy usunąć pojedynczy punkt awarii poniesione przez posiadanie tylko jednego możliwe miejsca docelowego. W przypadku awarii usługa routingu podejmie próbę dostarczenie wiadomości do następnego punktu końcowego na liście, dopóki nie został dostarczony komunikat, wystąpi błąd bez komunikacji, lub wszystkie punkty końcowe zostały wyczerpane.  
  
 Używane do konfigurowania obsługi błędów kroki opisane w artykule [How to: Obsługa błędów](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md).
  
### <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Instrukcje: Partycjonowanie danych usługi](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Instrukcje: Aktualizacja dynamiczna](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Instrukcje: Obsługa błędów](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
