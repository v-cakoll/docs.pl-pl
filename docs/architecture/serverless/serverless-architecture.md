---
title: Architektura bezserwerowa — aplikacje bezserwerowe
description: Eksploracja różnych architektur i aplikacji, które są obsługiwane przez architektury bezserwerowe, w tym aplikacje sieci Web, urządzenia przenośne i IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522408"
---
# <a name="serverless-architecture"></a>Architektura bezserwerowa

Istnieje wiele metod korzystania z architektur [bezserwerowych](https://azure.com/serverless) . W tym rozdziale przedstawiono przykłady typowych architektur, które integrują bezserwerowo. Obejmuje to również problemy, które mogą powodować dodatkowe wyzwania lub wymagać dodatkowej uwagi podczas implementowania bezserwerowego. Na koniec przedstawiono kilka przykładów projektowania, które ilustrują różne przypadki użycia serwera.

Hosty bezserwerowe często używają istniejącej warstwy opartej na kontenerze lub PaaS do zarządzania wystąpieniami bezserwerowymi. Na przykład Azure Functions jest oparta na [Azure App Service](https://docs.microsoft.com/azure/app-service/). App Service jest używany do skalowania wystąpień i zarządzania środowiskiem uruchomieniowym, które wykonuje Azure Functions kodzie. W przypadku funkcji opartych na systemie Windows Host działa jako PaaS i skaluje środowisko uruchomieniowe platformy .NET. W przypadku funkcji opartych na systemie Linux Host wykorzystuje kontenery.

![Architektura Azure Functions](./media/azure-functions-architecture.png)

Rdzeń WebJobs zawiera kontekst wykonywania funkcji. Środowisko uruchomieniowe języka uruchamia skrypty, wykonuje biblioteki i obsługuje platformę dla języka docelowego. Na przykład program Node. js służy do uruchamiania funkcji języka JavaScript, a .NET Framework jest używany do uruchamiania C# funkcji. Więcej informacji o opcjach języka i platformy można znaleźć w dalszej części tego rozdziału.

Niektóre projekty mogą korzystać z metody "All-in" do bezserwerowego. Aplikacje, które opierają się na mikrousługach, mogą wdrożyć wszystkie mikrousługi przy użyciu technologii bezserwerowej. Większość aplikacji jest hybrydowych, po jednowarstwowym zaprojektowaniu i korzystaniu z serwera dla składników, które mają sens, ponieważ składniki są modularne i niezależnie skalowalne. Aby pomóc w tym scenariuszu, w tej sekcji omówiono niektóre typowe przykłady architektury, które używają bezserwerowego.

## <a name="full-serverless-back-end"></a>Pełne zaplecze bezserwerowe

Pełny zaplecza bezserwerowego jest idealnym rozwiązaniem dla kilku typów scenariuszy, szczególnie podczas tworzenia nowych lub "zielonych pól". Aplikacja o dużym obszarze interfejsów API może korzystać z implementacji każdego interfejsu API jako funkcji bezserwerowej. Aplikacje, które są oparte na architekturze mikrousług, są kolejnym przykładem, który można zaimplementować jako pełny zaplecza bezserwerowego. Mikrousługi komunikują się między sobą za pośrednictwem różnych protokołów. Określone scenariusze obejmują:

- SaaS produkty oparte na interfejsie API (przykład: procesor płatności finansowych).
- Aplikacje sterowane komunikatami (przykład: rozwiązanie do monitorowania urządzeń).
- Aplikacje ukierunkowane na integrację usług (przykład: aplikacja do rezerwacji linii lotniczych).
- Procesy, które są uruchamiane okresowo (przykład: Oczyszczanie bazy danych oparte na czasomierzu).
- Aplikacje ukierunkowane na Przekształcanie danych (przykład: import wyzwolony przez przekazywanie plików).
- Wyodrębnij procesy transformacji i ładowania (ETL).

Istnieją inne, bardziej szczegółowe przypadki użycia, które zostały omówione w dalszej części tego dokumentu.

## <a name="monoliths-and-starving-the-beast"></a>Monolitów i "blokują Beast"

Typowym wyzwaniem jest Migrowanie istniejącej aplikacji monolitycznej do chmury. Najmniej ryzykownym podejściem jest "podniesienie i przesunięcie" w całości na maszynach wirtualnych. Wiele sklepów preferuje korzystanie z migracji jako okazję do modernizacji bazy kodu. Praktyczne podejście do migracji nazywa się "blokują The Beast". W tym scenariuszu monolitu jest migrowany "AS IS", aby zacząć od. Następnie wybrane usługi są nowoczesne. W niektórych przypadkach podpis usługi jest identyczny z oryginałem: jest on po prostu obsługiwany jako funkcja. Klienci są uaktualniani do korzystania z nowej usługi, a nie punktu końcowego monolitu. W przypadku pośrednich kroków, takich jak replikacja bazy danych, umożliwiają mikrousługom hostowanie własnych magazynów nawet wtedy, gdy transakcje są nadal obsługiwane przez monolitu. Na koniec wszyscy klienci są migrowani do nowych usług. Monolitu jest "Starved" (usługi nie są już wywoływane), dopóki wszystkie funkcje nie zostaną zastąpione. Połączenie bezserwerowych i serwerów proxy może ułatwić większość tej migracji.

![Migracja monolitu bezserwerowa](./media/serverless-monolith-migration.png)

Aby dowiedzieć się więcej na temat tego podejścia, Obejrzyj wideo: [Przenieś swoją aplikację do chmury, korzystając z Azure Functions bezserwerowych](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Aplikacje internetowe

Aplikacje sieci Web są doskonałymi kandydatami dla aplikacji bezserwerowych. Obecnie istnieją dwa popularne podejścia do aplikacji sieci Web: oparte na serwerze i klientach (takie jak aplikacja jednostronicowa lub SPA). Aplikacje sieci Web oparte na serwerze zwykle wykorzystują warstwę oprogramowania pośredniczącego do wystawiania wywołań interfejsu API w celu renderowania interfejsu użytkownika sieci Web. Aplikacje SPA powodują wywołania interfejsu API REST bezpośrednio z przeglądarki. W obu scenariuszach bezserwerowy może obsługiwać oprogramowanie pośredniczące lub żądanie interfejsu API REST, dostarczając niezbędną logikę biznesową. Wspólna architektura polega na rozdzieleniu uproszczonego statycznego serwera sieci Web. Aplikacja jednostronicowa (SPA) służy do obsługi języka HTML, CSS, JavaScript i innych zasobów przeglądarki. Aplikacja internetowa nawiązuje połączenie z zapleczem mikrousług.

## <a name="mobile-back-ends"></a>Zaplecza mobilne

Model oparty na zdarzeniach aplikacji bezserwerowych sprawia, że są one idealne dla zaplecza mobilnego. Urządzenie przenośne wyzwala zdarzenia i wykonuje kod bezserwerowy, aby spełnić żądania. Korzystając z modelu bezserwerowego, deweloperzy mogą ulepszyć logikę biznesową bez konieczności wdrażania pełnej aktualizacji aplikacji. Podejście bezserwerowe umożliwia również zespołom Udostępnianie punktów końcowych i równoległe działanie.

Deweloperzy aplikacji mobilnych mogą tworzyć logikę biznesową, nie będąc ekspertami po stronie serwera. Tradycyjnie aplikacje mobilne połączone z usługami lokalnymi. Utworzenie warstwy usług wymaga poznania platformy serwera i modelu programowania. Deweloperzy pracowali przy użyciu operacji w celu udostępniania serwerów i konfigurowania ich odpowiednio. Czasami kilka dni lub nawet tygodni zostały poświęcone na kompilowanie potoku wdrożenia. Wszystkie te wyzwania są rozwiązywane przez serwer.

Bezserwerowe abstrakcyjne zależności po stronie serwera i umożliwia deweloperom skoncentrowanie się na logice biznesowej. Na przykład deweloper mobilny, który tworzy aplikacje przy użyciu struktury JavaScript, może również tworzyć funkcje bezserwerowe z JavaScript. Host bezserwerowy zarządza systemem operacyjnym, wystąpieniem środowiska Node. js do hostowania kodu, zależności pakietów i nie tylko. Deweloper jest udostępniany prosty zestaw danych wejściowych i standardowy szablon dla danych wyjściowych. Następnie mogą skupić się na tworzeniu i testowaniu logiki biznesowej. Z tego względu mogą korzystać z istniejących umiejętności do kompilowania logiki zaplecza dla aplikacji mobilnej bez konieczności uczenia się nowych platform ani do "dewelopera po stronie serwera".

![Zaplecze urządzenia przenośnego bezserwerowego](./media/serverless-mobile-backend.png)

Większość dostawców chmury oferuje przenośne produkty bezserwerowe, które upraszczają cały cykl rozwoju aplikacji mobilnych. Produkty mogą zautomatyzować Inicjowanie obsługi baz danych w celu utrwalenia danych, obsłużyć DevOps problemy, zapewnić kompilacje oparte na chmurze i platformy testowania oraz możliwość tworzenia skryptów procesów firmy przy użyciu preferowanego języka dewelopera. Zastosowanie bezserwerowego podejścia opartego na urządzeniach przenośnych może usprawnić proces. Bezserwerowe eliminuje ogromne obciążenie, Konfigurowanie i konserwowanie serwerów na potrzeby zaplecza mobilnego.

## <a name="internet-of-things-iot"></a>Internet rzeczy (IoT)

IoT odnosi się do obiektów fizycznych, które są połączone ze sobą. Są one czasami określane jako "urządzenia połączone" lub "urządzenia inteligentne". Wszystko z samochodów i maszyn sprzedaży może być połączone i wysyłać informacje od spisu do danych czujników, takich jak temperatury i wilgotność. W przedsiębiorstwie IoT oferuje udoskonalenia procesów firmy poprzez monitorowanie i automatyzację. Dane IoT mogą służyć do regulowania klimatu w dużych magazynach lub śledzenia spisu za pomocą łańcucha dostaw. IoT może wykrywać wycieki chemiczne i wywoływać dział pożaru w przypadku wykrycia dymu.

Zawiera ilość urządzeń i informacji często wymusza architekturę opartą na zdarzeniach, aby kierować i przetwarzać komunikaty. Bezserwerowy jest idealnym rozwiązaniem z kilku powodów:

- Umożliwia skalowanie w miarę wzrostu ilości urządzeń i danych.
- Służy do dodawania nowych punktów końcowych w celu obsługi nowych urządzeń i czujników.
- Ułatwia niezależne przechowywanie wersji, dzięki czemu deweloperzy mogą aktualizować logikę biznesową dla określonego urządzenia bez konieczności wdrażania całego systemu.
- Odporność i mniej przestojów.

W efekcie usługi IoT wystąpiły różne produkty bezserwerowe, które koncentrują się na obawach IoT, takich jak [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Bezserwerowy automatyzuje zadania, takie jak rejestrowanie urządzeń, wymuszanie zasad, śledzenie i nawet Wdrażanie kodu na urządzeniach na *brzegu*. Brzeg odnosi się do urządzeń, takich jak czujniki i siłowniky, które są połączone z, ale nie z aktywną częścią, Internetu.

>[!div class="step-by-step"]
>[Poprzedni](architecture-approaches.md)
>[Następny](serverless-architecture-considerations.md)
