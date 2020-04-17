---
title: Modele hostingu aplikacji Blazor
description: Dowiedz się, jak hostować aplikację Blazor, w tym w przeglądarce na WebAssembly lub na serwerze.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 77a022b01efba01038790c9601ea03f315a28fdf
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607935"
---
# <a name="blazor-app-hosting-models"></a>Modele hostingu aplikacji Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikacje Blazor mogą być hostowane w serwisach IIS, podobnie jak aplikacje ASP.NET Web Forms. Aplikacje Blazor mogą być również hostowane w jeden z następujących sposobów:

- Po stronie klienta w przeglądarce na WebAssembly.
- Po stronie serwera w aplikacji ASP.NET Core.

## <a name="blazor-webassembly-apps"></a>Aplikacje Blazor WebAssembly

Aplikacje Blazor WebAssembly są wykonywane bezpośrednio w przeglądarce w czasie wykonywania .NET opartym na webassembly. Aplikacje Blazor WebAssembly działają w podobny sposób jak frontonowe struktury JavaScript, takie jak Angular lub React. Jednak zamiast pisania JavaScript piszesz C#. Środowisko uruchomieniowe platformy .NET jest pobierane z aplikacją wraz z zestawem aplikacji i wszelkimi wymaganymi zależnościami. Nie są wymagane wtyczki przeglądarki ani rozszerzenia.

Pobrane zestawy są normalne zestawy .NET, jak można użyć w każdej innej aplikacji .NET. Ponieważ środowisko wykonawcze obsługuje program .NET Standard, można używać istniejących bibliotek .NET Standard za pomocą aplikacji Blazor WebAssembly. Jednak te zestawy będą nadal wykonywane w piaskownicy zabezpieczeń przeglądarki. Niektóre funkcje mogą <xref:System.PlatformNotSupportedException>rzucać , jak próba uzyskania dostępu do systemu plików lub otwarcie dowolnych połączeń sieciowych.

Po załadowaniu aplikacji środowisko uruchomieniowe .NET jest uruchamiane i wskazywki na zestaw aplikacji. Logika uruchamiania aplikacji jest uruchamiana, a składniki główne są renderowane. Blazor oblicza aktualizacje interfejsu użytkownika na podstawie renderowanych danych wyjściowych ze składników. Następnie zostaną zastosowane aktualizacje DOM.

![Zestaw WebAssembly Blazor](media/hosting-models/blazor-webassembly.png)

Aplikacje Blazor WebAssembly działają wyłącznie po stronie klienta. Takie aplikacje można wdrożyć w statycznych rozwiązaniach hostingowych witryn, takich jak Strony GitHub lub Hosting statycznej witryny Azure. .NET nie jest wymagane na serwerze w ogóle. Głębokie łączenie z częściami aplikacji zazwyczaj wymaga rozwiązania routingu na serwerze. Rozwiązanie routingu przekierowuje żądania do katalogu głównego aplikacji. Na przykład to przekierowanie może być obsługiwane przy użyciu reguł przepisywania adresów URL w usługach IIS.

Aby uzyskać wszystkie zalety blazora i pełnego stosu .NET web development, host aplikacji Blazor WebAssembly z ASP.NET Core. Za pomocą platformy .NET na kliencie i serwerze, można łatwo udostępniać kod i tworzyć aplikację przy użyciu jednego spójnego zestawu języków, struktur i narzędzi. Blazor zapewnia wygodne szablony do konfigurowania rozwiązania, które zawiera zarówno aplikację Blazor WebAssembly, jak i projekt hosta ASP.NET Core. Po utworzeniu rozwiązania utworzone pliki statyczne z aplikacji Blazor są hostowane przez aplikację ASP.NET Core z routingiem rezerwowym już skonfigurowanym.

## <a name="blazor-server-apps"></a>Aplikacje Blazor Server

Przypomnijmy, że z dyskusji na temat [architektury Blazora](architecture-comparison.md#blazor) wynika, że komponenty Blazora sprawiają, że ich wyjście jest pośrednie, `RenderTree`zwane . Struktura Blazor następnie porównuje to, co zostało renderowane z tym, co było wcześniej renderowane. Różnice są stosowane do dom. Składniki Blazora są oddzielone od sposobu stosowania ich renderowanego wyjścia. W związku z tym same składniki nie muszą działać w tym samym procesie, co proces aktualizacji interfejsu użytkownika. W rzeczywistości nie muszą nawet działać na tej samej maszynie.

W aplikacjach Blazor Server składniki są uruchamiane na serwerze, a nie po stronie klienta w przeglądarce. Zdarzenia interfejsu użytkownika występujące w przeglądarce są wysyłane do serwera za pośrednictwem połączenia w czasie rzeczywistym. Zdarzenia są wywoływane do poprawnych wystąpień składnika. Render składników i obliczony identyfikator interfejsu użytkownika jest serializowany i wysyłany do przeglądarki, gdzie jest stosowany do dom.

![Serwer Blazor](media/hosting-models/blazor-server.png)

Model hostingu Blazor Server może brzmieć znajomo, jeśli <xref:System.Web.UI.UpdatePanel> używasz ASP.NET AJAX i formantu. Formant `UpdatePanel` obsługuje stosowanie częściowych aktualizacji strony w odpowiedzi na zdarzenia wyzwalacza na stronie. Po wyzwoleniu `UpdatePanel` żąda częściowej aktualizacji, a następnie stosuje ją bez konieczności odświeżania strony. Stan interfejsu użytkownika jest zarządzany `ViewState`przy użyciu . Aplikacje Blazor Server różnią się nieco tym, że aplikacja wymaga aktywnego połączenia z klientem. Ponadto cały stan interfejsu użytkownika jest obsługiwany na serwerze. Oprócz tych różnic, oba modele są koncepcyjnie podobne.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Jak wybrać odpowiedni model hostingu Blazor

Jak opisano w [docs modelu hostingowego Blazor,](/aspnet/core/blazor/hosting-models)różne modele hostingowe Blazor mają różne kompromisy.

Model hostingu Blazor WebAssembly ma następujące zalety:

- Nie ma zależności po stronie serwera .NET. Aplikacja działa w pełni po pobraniu do klienta.
- Zasoby i możliwości klienta są w pełni wykorzystywane.
- Praca jest odciążona z serwera do klienta.
- Serwer sieci web ASP.NET Core nie jest wymagany do hosta aplikacji. Możliwe są scenariusze wdrażania bez serwera (na przykład obsługa aplikacji z sieci CDN).

Wady modelu hostingowego Blazor WebAssembly to:

- Możliwości przeglądarki ograniczają aplikację.
- Wymagany jest sprzęt i oprogramowanie klienta (na przykład obsługa webassembly).
- Rozmiar pobierania jest większy, a ładowanie aplikacji trwa dłużej.
- Obsługa środowiska uruchomieniowego i narzędzi .NET jest mniej dojrzała. Na przykład istnieją ograniczenia w obsłudze i debugowaniu [.NET Standard.](../../standard/net-standard.md)

Z drugiej strony model hostingu serwera Blazor oferuje następujące korzyści:

- Rozmiar pobierania jest znacznie mniejszy niż aplikacja po stronie klienta, a aplikacja ładuje się znacznie szybciej.
- Aplikacja w pełni wykorzystuje możliwości serwera, w tym korzystanie z dowolnych interfejsów API zgodnych z rdzeniem .NET.
- .NET Core na serwerze jest używany do uruchamiania aplikacji, więc istniejące narzędzia .NET, takie jak debugowanie, działa zgodnie z oczekiwaniami.
- Obsługiwane są cienkie klienty. Na przykład aplikacje po stronie serwera działają z przeglądarkami, które nie obsługują webassembly i na urządzeniach z ograniczeniami zasobów.
- Baza kodu aplikacji .NET/C#, w tym kod składnika aplikacji, nie jest obsługiwana klientom.

Minusami modelu hostingowego Serwera Blazor są:

- Większe opóźnienie interfejsu użytkownika. Każda interakcja użytkownika obejmuje przeskok sieciowy.
- Nie ma obsługi w trybie offline. Jeśli połączenie klienta nie powiedzie się, aplikacja przestanie działać.
- Skalowalność jest wyzwaniem dla aplikacji z wieloma użytkownikami. Serwer musi zarządzać wieloma połączeniami klientów i obsługiwać stan klienta.
- Do obsługi aplikacji wymagany jest serwer ASP.NET Core. Scenariusze wdrażania bezserwerowe nie są możliwe. Na przykład nie można obsługiwać aplikacji z sieci CDN.

Poprzednia lista kompromisów może być zastraszająca, ale twój model hostingu można zmienić później. Niezależnie od wybranego modelu hostingowego Blazor, model *komponentu*jest taki sam . Zasadniczo te same składniki mogą być używane z każdym modelem hostingu. Kod aplikacji nie ulegnie zmianie; jednak jest dobrą praktyką, aby wprowadzić abstrakcje tak, aby składniki pozostają hosting modelu niezależnego od modelu. Abstrakcje umożliwiają aplikacji łatwiej przyjąć inny model hostingu.

## <a name="deploy-your-app"></a>Wdrażanie aplikacji

aplikacje ASP.NET formularzy sieci Web są zazwyczaj hostowane w serwisach IIS na komputerze lub klastrze systemu Windows Server. Aplikacje Blazor mogą również:

- Hostować w serwisach IIS jako pliki statyczne lub jako aplikacja ASP.NET Core.
- Wykorzystaj ASP.NET elastyczność Core, aby być hostowana na różnych platformach i infrastrukturze serwerów. Na przykład, można hostować aplikacji Blazor przy użyciu [Nginx](/aspnet/core/host-and-deploy/linux-nginx) lub [Apache](/aspnet/core/host-and-deploy/linux-apache) na Linuksie. Aby uzyskać więcej informacji na temat publikowania i wdrażania aplikacji Blazor, zobacz dokumentację usługi Blazor [Hosting i wdrażanie.](/aspnet/core/host-and-deploy/blazor/)

W następnej sekcji przyjrzymy się, jak skonfigurowane są projekty aplikacji Blazor WebAssembly i Blazor Server.

>[!div class="step-by-step"]
>[Poprzedni](architecture-comparison.md)
>[następny](project-structure.md)
