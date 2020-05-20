---
title: Buforowanie w aplikacji natywnej dla chmury
description: Dowiedz się więcej na temat strategii buforowania w aplikacji natywnej w chmurze.
author: robvet
ms.date: 05/17/2020
ms.openlocfilehash: a109db59d7b2005ea97922eef07ae4869e4894a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614295"
---
# <a name="caching-in-a-cloud-native-app"></a>Buforowanie w aplikacji natywnej w chmurze

Zalety buforowania są zrozumiałe. Technika działa przez tymczasowe kopiowanie często używanych danych z magazynu danych zaplecza do *szybkiego magazynu* , który znajduje się bliżej aplikacji. Buforowanie jest często implementowane, gdzie...

- Dane pozostają względnie statyczne.
- Dostęp do danych jest powolny, szczególnie w porównaniu z szybkością pamięci podręcznej.
- Dane są uzależnione od wysokiego poziomu rywalizacji.

## <a name="why"></a>Dlaczego?

Zgodnie z opisem w [wytycznych dotyczących buforowania firmy Microsoft](https://docs.microsoft.com/azure/architecture/best-practices/caching)buforowanie może zwiększyć wydajność, skalowalność i dostępność dla poszczególnych mikrousług i całego systemu. Zmniejsza to opóźnienia i rywalizację o obsługę dużych ilości współbieżnych żądań do magazynu danych. W miarę jak ilość danych i liczba użytkowników zwiększają się, tym większe korzyści z buforowania.

Buforowanie jest najbardziej efektywne, gdy klient wielokrotnie odczytuje dane, które są niezmienne lub rzadko ulegają zmianom. Przykłady zawierają informacje referencyjne, takie jak informacje o produkcie i cenach lub udostępnione zasoby statyczne, które są kosztowne do skonstruowania.

Chociaż mikrousługi powinny być bezstanowe, rozproszona pamięć podręczna może obsługiwać współbieżny dostęp do danych stanu sesji, gdy jest to absolutnie wymagane.

Należy również rozważyć buforowanie, aby uniknąć powtarzających się obliczeń. Jeśli operacja przekształca dane lub wykonuje skomplikowane obliczenia, Buforuj wynik dla kolejnych żądań.

## <a name="caching-architecture"></a>Architektura buforowania

Natywne aplikacje w chmurze zwykle implementują rozproszoną architekturę pamięci podręcznej. Pamięć podręczna jest hostowana jako usługa do [tworzenia kopii zapasowych](./definition.md#backing-services)oparta na chmurze, oddzielona od mikrousług. Na rysunku 5-15 przedstawiono architekturę.

![Buforowanie w natywnej aplikacji w chmurze](media/caching-in-a-cloud-native-app.png)

**Rysunek 5-15**: buforowanie w natywnej aplikacji w chmurze

Na poprzedniej ilustracji należy zauważyć, jak pamięć podręczna jest niezależna i współdzielona przez mikrousługi. W tym scenariuszu pamięć podręczna jest wywoływana przez [bramę interfejsu API](./front-end-communication.md). Jak opisano w rozdziale 4, Brama służy jako fronton dla wszystkich żądań przychodzących. Rozproszonej pamięci podręcznej zwiększa czas odpowiedzi systemu przez zwrócenie danych w pamięci podręcznej, jeśli to możliwe. Ponadto oddzielenie pamięci podręcznej od usług pozwala na niezależne skalowanie w górę lub w poziomie w celu spełnienia zwiększonych wymagań w zakresie ruchu.

Powyższy rysunek przedstawia typowy wzorzec buforowania znany jako wzorzec z odkładaniem do [pamięci podręcznej](https://docs.microsoft.com/azure/architecture/patterns/cache-aside). W przypadku żądania przychodzącego należy najpierw wykonać zapytanie do pamięci podręcznej (krok \# 1) w celu uzyskania odpowiedzi. Jeśli ta wartość zostanie znaleziona, dane są zwracane natychmiast. Jeśli dane nie znajdują się w pamięci podręcznej (nazywanej [chybień pamięci podręcznej](https://www.techopedia.com/definition/6308/cache-miss)), są pobierane z lokalnej bazy danych w usłudze podrzędnej (krok \# 2). Następnie jest on zapisywana w pamięci podręcznej w celu przyszłego żądania (krok \# 3) i zwracany do obiektu wywołującego. Należy zwrócić uwagę na okresowe wykluczanie danych w pamięci podręcznej tak, aby system pozostały czasowo i spójny.

W miarę zwiększania współużytkowanej pamięci podręcznej może okazać się korzystne, aby mieć możliwość partycjonowania danych w wielu węzłach. Takie działanie może pomóc zminimalizować rywalizację i zwiększyć skalowalność. Wiele usług buforowania obsługuje możliwość dynamicznego dodawania i usuwania węzłów oraz ponownego równoważenia danych w różnych partycjach. Takie podejście zwykle obejmuje klastrowanie. Klastrowanie udostępnia kolekcję węzłów federacyjnych jako bezproblemową, pojedynczą pamięć podręczną. Wewnętrznie dane są jednak dystrybuowane między węzłami w ramach wstępnie zdefiniowanej strategii dystrybucji, która równoważy obciążenie.

## <a name="azure-cache-for-redis"></a>Azure Cache for Redis

[Pamięć podręczna systemu Azure dla usługi Redis](https://azure.microsoft.com/services/cache/) to bezpieczna usługa do buforowania danych i przesyłania komunikatów, która jest w pełni zarządzana przez firmę Microsoft. Używana jako oferta platformy jako usługi (PaaS), zapewnia wysoką przepływność i dostęp do danych o małym opóźnieniu. Usługa jest dostępna dla każdej aplikacji w ramach platformy Azure lub poza nią.

Usługa Azure cache for Redis zarządza dostępem do serwerów Redis Open Source hostowanych w centrach danych platformy Azure. Usługa działa jako fasada zapewniająca zarządzanie, kontrolę dostępu i bezpieczeństwo. Usługa natywnie obsługuje bogaty zestaw struktur danych, w tym ciągów, skrótów, list i zestawów. Jeśli aplikacja korzysta już z Redis, będzie działała tak, jakby była usługą Azure cache for Redis.

Pamięć podręczna systemu Azure dla Redis jest większa niż prosta pamięć podręczna. Dział IT może obsługiwać różne scenariusze rozszerzające architekturę mikrousług:

- Magazyn danych w pamięci
- Dystrybuowana nierelacyjna baza danych
- Broker komunikatów
- Serwer konfiguracji lub odnajdywania
  
W przypadku zaawansowanych scenariuszy kopia danych w pamięci podręcznej może być [utrwalona na dysku](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-how-to-premium-persistence). Jeśli zdarzenie katastrofalne wyłącza zarówno podstawową, jak i pamięć podręczną repliki, pamięć podręczną jest tworzona z najnowszej migawki.

Azure Redis Cache jest dostępny w wielu wstępnie zdefiniowanych konfiguracjach i warstwach cenowych.  [Warstwa Premium](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-premium-tier-intro) oferuje wiele funkcji na poziomie przedsiębiorstwa, takich jak klastrowanie, trwałość danych, replikacja geograficzna i izolacja sieci wirtualnej.

>[!div class="step-by-step"]
>[Poprzedni](relational-vs-nosql-data.md) 
> [Dalej](elastic-search-in-azure.md)
