---
title: Scenariusze routingu
ms.date: 03/30/2017
helpviewer_keywords:
- rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: 458b67de57be2bd0847ceccbc8a3aebd3b025f64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="routing-scenarios"></a>Scenariusze routingu
Usługa routingu jest w dużym stopniu dostosowywane, może być trudne do projektowania wydajne logiki routingu, podczas tworzenia nowej konfiguracji od początku.  Istnieje jednak kilka typowych scenariuszy, które należy wykonać w większości konfiguracji usługa routingu. Gdy te scenariusze mogą jednak nie dotyczyć bezpośrednio do określonej konfiguracji, zrozumienie, jak można skonfigurować usługi routingu w celu obsługi tych scenariuszy będzie pomocy można w opis usługi routingu.  
  
## <a name="common-scenarios"></a>Typowe scenariusze  
 Jest to najbardziej podstawowa funkcja usługi Routing agregacji wiele miejsce docelowe punktów końcowych, aby zmniejszyć liczbę punktów końcowych ujawniony dla aplikacji klienckich, a następnie użyj filtry komunikatów do kierowania każdy komunikat do poprawnego miejsca docelowego. Komunikaty mogą być kierowane na podstawie wymagań przetwarzania logiczną lub fizyczną, takie jak typ wiadomości, które muszą być przetwarzane przez określonej usługi lub odpowiednio do potrzeb działalności dowolnego, takie jak dostarczanie priorytet przetwarzania komunikatów z określonego źródła. W poniższej tabeli wymieniono niektóre typowe scenariusze oraz gdy są one napotkał:  
  
|Scenariusz|Kiedy używać|  
|--------------|--------------|  
|Przechowywanie wersji usługi|Wymagana jest obsługa wielu wersji usługi lub może wdrożyć usługę zaktualizowane w przyszłości|  
|Partycjonowanie danych usługi|Usługa musi partycji na wielu hostach|  
|Aktualizacja dynamiczna|Należy ponownie skonfigurować dynamicznie logiki routingu w czasie wykonywania, aby obsługiwać Zmienianie wdrożenia usługi|  
|Multiemisji|Konieczne jest wysłanie co komunikat do wielu punktów końcowych|  
|Mostkowanie protokołu|Komunikaty za pośrednictwem protokołu transportu jednego i docelowy punkt końcowy używa innego protokołu|  
|Obsługa błędów|Konieczne jest zapewnienie odporności na awarie sieci i łączności|  
  
> [!NOTE]
>  Wiele scenariuszy, przedstawione są specyficzne dla określonych potrzeb biznesowych lub przetwarzania wymagania, planowanie obsługują aktualizacji dynamicznych i przy użyciu obsługi błędów można często uważane jako najlepsze rozwiązania umożliwiają modyfikowanie logiki routingu w czasie wykonywania i odzyskanie przejściowych awarii sieci lub komunikacji.  
  
### <a name="service-versioning"></a>Przechowywanie wersji usługi  
 Po wprowadzeniu nowej wersji usługi, często muszą zachować poprzedniej wersji, dopóki wszyscy klienci mają są przenoszone do nowej usługi. Jest to szczególnie krytyczne, gdy usługa jest wymagany dni, tygodnie lub miesiące nawet do ukończenia procesu długotrwałe. Zazwyczaj wymaga wykonania nowy adres punktu końcowego dla nowej usługi przy zachowaniu oryginalnej punktu końcowego dla wcześniejszych wersji.  
  
 W przypadku użycia usługi routingu mogą uwidaczniać jeden punkt końcowy do odbierania wiadomości z aplikacji klienckich, a następnie kierować każdy komunikat do wersji prawidłowe usługi na podstawie zawartości komunikatu. Najbardziej podstawowa implementacja obejmuje dodawanie niestandardowego nagłówka do komunikat, który wskazuje wersję usługi, która komunikat jest przetwarzany przez. Usługa routingu umożliwia XPathMessageFilter Sprawdź każdy komunikat obecność niestandardowy nagłówek i kierowania wiadomości do odpowiedniego docelowego punktu końcowego.  
  
 Aby uzyskać instrukcje, służący do tworzenia konfiguracji przechowywanie wersji usługi, zobacz [jak: przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md). Na przykład za pomocą XPathMessageFilter do wyznaczania tras wiadomościom oparte na niestandardowy nagłówek, zobacz [filtry zaawansowane](../../../../docs/framework/wcf/samples/advanced-filters.md) próbki.  
  
### <a name="service-data-partitioning"></a>Partycjonowanie danych usługi  
 Podczas projektowania środowisku rozproszonym, często jest pożądane, aby rozłożyć obciążenie na wielu komputerach, aby zapewnić wysoką dostępność, zmniejsz obciążenie na poszczególnych komputerach, lub w celu zapewnienia zasobów dedykowanych dla konkretnego podzestawu wiadomości. Gdy usługa routingu nie zastępuje dedykowane rozwiązania do równoważenia obciążenia, możliwość wykonywania routingu na podstawie zawartości może służyć do przesyłania wiadomości w przeciwnym razie podobne do określonych miejsc docelowych. Na przykład masz wymagane do przetwarzania komunikatów z określonego klienta niezależnie od komunikatów odebranych z innych klientów.  
  
 Pozwala utworzyć dane usługi, partycjonowanie konfiguracji znajduje się [jak: partycjonowanie danych usługi](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md). Na przykład za pomocą filtrów do partycji danych na podstawie adresu URL i niestandardowe nagłówki, zobacz [filtry zaawansowane](../../../../docs/framework/wcf/samples/advanced-filters.md) próbki.  
  
### <a name="dynamic-routing"></a>Routingu dynamicznego  
 Często jest pożądane, aby zmodyfikować konfigurację routingu do zmieniających się potrzeb biznesowych, takich jak dodawanie trasy do nowszej wersji usług, zmiana kryteriów routingu lub zmiana docelowego punktu końcowego określonego komunikatu, który kieruje filtr do zaspokojenia. Usługa routingu umożliwia tym za pośrednictwem <xref:System.ServiceModel.Routing.RoutingExtension>, co pozwala zapewnić nową konfigurację w czasie wykonywania. Nowa konfiguracja aktywne natychmiast, ale wpływa tylko na wszelkich nowych sesji przetworzone przez usługę routingu.  
  
 Używane do implementowania routingu dynamicznego kroki opisane w artykule [jak: Aktualizacja dynamiczna](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md). Na przykład przy użyciu routingu dynamicznego, zobacz [dynamiczna ponowna konfiguracja](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md) próbki.  
  
### <a name="multicast"></a>Multiemisji  
 Gdy routing wiadomości, zazwyczaj należy routingu każdy komunikat do jednego określonego miejsca docelowego punktu końcowego.  Jednak czasami konieczne może być kierować kopia wiadomości do wielu punktów końcowych docelowego. Aby przeprowadzić routing multiemisji, muszą być spełnione następujące warunki:  
  
-   Kształtu kanału nie może być "żądanie-odpowiedź" (mimo że może być jednokierunkowe lub dupleksowy,), ponieważ żądanie odpowiedź ma, że tylko jedną odpowiedź może zostać odebrany przez aplikację klienta w odpowiedzi na żądanie.  
  
-   Wiele filtrów musi zwracać **true** podczas oceniania wiadomości.  
  
 Jeśli te warunki są spełnione, każdy docelowy punkt końcowy jest skojarzony z filtrem, która zwraca wartość true, zostanie wyświetlony kopia wiadomości.  
  
### <a name="protocol-bridging"></a>Mostkowanie protokołu  
 Gdy routing wiadomości między niepodobnych protokołów SOAP, usługa routingu używa interfejsów API WCF Aby przekonwertować wiadomości z jednego protokołu. Występuje to automatycznie, kiedy widoczne punktów końcowych usługi w przy użyciu usługi routingu innego protokołu niż punktów końcowych klienta, który wiadomości są kierowane do. Istnieje możliwość wyłączyć to zachowanie, jeśli nie są standardowe; używanych protokołów Jednakże następnie należy podać własne mostkowanie kodu.  
  
 . Na przykład do tłumaczenia wiadomości między protokołami za pomocą usługi routingu, zobacz [mostkowanie i obsługa błędów](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) próbki.  
  
### <a name="error-handling"></a>Obsługa błędów  
 W środowisku rozproszonym nie jest rzadko mogą wystąpić przejściowych awarii sieci lub komunikacji. Bez usługi pośredniczącej, takich jak usługa routingu obciążenie obsługi tych błędów znajduje się w aplikacji klienta. Jeśli aplikacja kliencka nie obejmuje konkretnej logiki, aby ponowić próbę, w przypadku awarii sieci lub błędami komunikacji i wiedzę na temat alternatywnych lokalizacji, użytkownika może wystąpić sytuacje, w którym komunikat składa się wiele razy zanim zostanie pomyślnie przetworzone przez usługę docelowego. Może to prowadzić do niezadowolenie klienta z aplikacji, jak mogą być uważane jako niepewna.  
  
 Usługa routingu podejmuje próbę naprawienia tego scenariusza, podając błąd niezawodne możliwości obsługi komunikatów, które występują sieci lub błędy związane z komunikacji. Tworzenie listy punktów końcowych możliwe miejsce docelowe i kojarzenie tej listy z każdym filtr komunikatu, należy usunąć pojedynczy punkt awarii poniesionych przez tylko jeden możliwe miejsce docelowe. W przypadku awarii usługa routingu będzie podejmować próby dostarczenie wiadomości do następnego punktu końcowego na liście, dopóki dostarczyć wiadomości, wystąpi błąd komunikacji z systemem innym niż, lub wykorzystał wszystkie punkty końcowe.  
  
 Procedura służąca do konfigurowania obsługi błędów, w sekcji [jak: obsługa błędów](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md). Na przykład wdrażania obsługi błędów zobacz [mostkowanie i obsługa błędów](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) i [zaawansowane obsługi błędu](../../../../docs/framework/wcf/samples/advanced-error-handling.md) próbek.  
  
### <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Instrukcje: partycjonowanie danych usługi](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Instrukcje: aktualizacja dynamiczna](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Instrukcje: obsługa błędów](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
