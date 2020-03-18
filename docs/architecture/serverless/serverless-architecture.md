---
title: Architektura bezserwerowa — aplikacje bezserwerowe
description: Eksploracja różnych architektur i aplikacji obsługiwanych przez architektury bezserwerowe, w tym aplikacje internetowe, urządzenia przenośne i IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522408"
---
# <a name="serverless-architecture"></a>Architektura bezserwerowa

Istnieje wiele podejść do korzystania z architektur [bezserwerowych.](https://azure.com/serverless) W tym rozdziale omówiono przykłady typowych architektur, które integrują bezserwerowe. Obejmuje również obawy, które mogą stanowić dodatkowe wyzwania lub wymagają dodatkowego rozważenia podczas implementowania bezserwerowych. Na koniec przedstawiono kilka przykładów projektu, które ilustrują różne przypadki użycia bez użycia bez użycia bez użycia serwera.

Hosty bezserwerowe często używają istniejącej warstwy opartej na kontenerach lub PaaS do zarządzania wystąpieniami bezserwerowymi. Na przykład usługa Azure Functions jest oparta na [usłudze Azure App Service](https://docs.microsoft.com/azure/app-service/). Usługa app service służy do skalowania w sposób skalowania w sposób skalowania w czasie wykonywania i zarządzania czasem wykonywania kodu usługi Azure Functions. W przypadku funkcji opartych na systemie Windows host działa jako PaaS i skaluje środowisko uruchomieniowe .NET. W przypadku funkcji opartych na systemie Linux host korzysta z kontenerów.

![Architektura funkcji platformy Azure](./media/azure-functions-architecture.png)

WebJobs Core zapewnia kontekst wykonywania dla funkcji. Language Runtime uruchamia skrypty, wykonuje biblioteki i obsługuje strukturę dla języka docelowego. Na przykład Node.js jest używany do uruchamiania funkcji JavaScript i .NET Framework jest używany do uruchamiania funkcji C#. Więcej informacji na temat opcji języka i platformy dowiesz się w dalszej części tego rozdziału.

Niektóre projekty mogą korzystać z podjęcia "all-in" podejście do bezserwerowych. Aplikacje, które w dużym stopniu opierają się na mikrousługach może zaimplementować wszystkie mikrousług przy użyciu technologii bezserwerowej. Większość aplikacji jest hybrydowa, po projekcie n-warstwowym i używa bezserwerowej dla składników, które mają sens, ponieważ składniki są modułowe i niezależnie skalowalne. Aby ułatwić zrozumienia tych scenariuszy, w tej sekcji przechodzi przez niektóre typowe przykłady architektury, które używają bezserwerowe.

## <a name="full-serverless-back-end"></a>Pełny serwerowy back end

Pełny serwerowy zaplecze jest idealny dla kilku typów scenariuszy, szczególnie podczas tworzenia nowych lub "zielonych pól" aplikacji. Aplikacja z dużą powierzchnią interfejsów API może korzystać z implementacji każdego interfejsu API jako funkcji bezserwerowej. Aplikacje, które są oparte na architekturze mikrousług są kolejnym przykładem, który może być zaimplementowany jako pełny zaplecza bez użycia serwera. Mikrousług komunikować się za pomocą różnych protokołów ze sobą. Konkretne scenariusze obejmują:

- Produkty SaaS oparte na interfejsie API (przykład: procesor płatności finansowych).
- Aplikacje oparte na komunikatach (przykład: rozwiązanie do monitorowania urządzeń).
- Aplikacje skoncentrowane na integracji między usługami (np. aplikacja do rezerwacji linii lotniczych).
- Procesy uruchamiane okresowo (na przykład: oczyszczanie bazy danych oparte na czasomierze).
- Aplikacje koncentruje się na transformacji danych (przykład: import wyzwalane przez przekazywanie plików).
- Wyodrębnij procesy przekształcania i ładowania (ETL).

Istnieją inne, bardziej szczegółowe przypadki użycia, które są omówione w dalszej części tego dokumentu.

## <a name="monoliths-and-starving-the-beast"></a>Monolity i "głodującbestia"

Typowym wyzwaniem jest migracja istniejącej aplikacji monolityczne do chmury. Najmniej ryzykowne podejście jest "lift and shift" całkowicie na maszynach wirtualnych. Wiele sklepów woli wykorzystać migrację jako okazję do modernizacji swojej bazy kodu. Praktyczne podejście do migracji nazywa się "głodem bestii". W tym scenariuszu monolit jest migrowany "tak jak jest", aby rozpocząć. Następnie wybrane usługi są modernizowane. W niektórych przypadkach podpis usługi jest identyczny z oryginałem: po prostu jest hostowany jako funkcja. Klienci są aktualizowane, aby korzystać z nowej usługi, a nie monolitu punktu końcowego. W międzyczasie kroki, takie jak replikacja bazy danych, umożliwiają mikrousług do hosta własnego magazynu, nawet wtedy, gdy transakcje są nadal obsługiwane przez monolit. Po pewnym czasie wszyscy klienci są migrowane do nowych usług. Monolit jest "głodowy" (jego usługi nie są już nazywane), dopóki nie zostanie zastąpiona cała funkcjonalność. Połączenie bezserwerowych i serwerów proxy może ułatwić znaczną część tej migracji.

![Migracja monolitu bez serwerów](./media/serverless-monolith-migration.png)

Aby dowiedzieć się więcej na temat tego podejścia, obejrzyj klip wideo: [Przenieś aplikację do chmury za pomocą bezserwerowych funkcji platformy Azure](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Aplikacje internetowe

Aplikacje sieci Web są świetnymi kandydatami do aplikacji bezserwerowych. Obecnie istnieją dwa typowe podejścia do aplikacji sieci web: oparte na serwerze i oparte na kliencie (takie jak aplikacja jednostronicowa lub SPA). Aplikacje sieci Web oparte na serwerze zazwyczaj używają warstwy pośredniczowca do wystawiania wywołań interfejsu API w celu renderowania interfejsu sieci Web. Aplikacje SPA wykonywać wywołania interfejsu API REST bezpośrednio z przeglądarki. W obu scenariuszach bezserwerowe może pomieścić pośredniczenia lub żądania interfejsu API REST, zapewniając logikę biznesową niezbędne. Wspólną architekturą jest wstawanie lekkiego statycznego serwera sieci web. Aplikacja jednostronicowa (SPA) obsługuje zasoby HTML, CSS, JavaScript i inne zasoby przeglądarki. Aplikacja sieci web następnie łączy się z zaplecza mikrousług.

## <a name="mobile-back-ends"></a>Mobilne tylne końce

Paradygmat oparty na zdarzeniach aplikacji bezserwerowych sprawia, że są idealne jako mobilne zaplecze. Urządzenie przenośne wyzwala zdarzenia i kod bezserwerowy jest wykonywany w celu zaspokojenia żądań. Korzystanie z modelu bezużycia serwera umożliwia deweloperom zwiększenie logiki biznesowej bez konieczności wdrażania pełnej aktualizacji aplikacji. Podejście bezserwerowe umożliwia również zespołom udostępnianie punktów końcowych i równoległą pracę.

Deweloperzy mobilni mogą tworzyć logikę biznesową, nie stając się ekspertami po stronie serwera. Tradycyjnie aplikacje mobilne połączone z usługami lokalnymi. Tworzenie warstwy usług wymagało zrozumienia platformy serwerowej i paradygmatu programowania. Deweloperzy pracowali z operacjami, aby aprowizować serwery i odpowiednio je skonfigurować. Czasami dni, a nawet tygodnie zostały poświęcone na budowę potoku wdrażania. Wszystkie te wyzwania są rozwiązywane przez bezserwerowe.

Bezserwerowe abstrakcje zależności po stronie serwera i umożliwia deweloperowi skupić się na logice biznesowej. Na przykład deweloper mobilny, który tworzy aplikacje przy użyciu struktury JavaScript, może również tworzyć funkcje bezserwerowe w języku JavaScript. Host bezserwerowy zarządza systemem operacyjnym, wystąpieniem Node.js hostowanym kodem, zależnościami pakietów i nie tylko. Deweloper otrzymuje prosty zestaw danych wejściowych i standardowy szablon dla wyjść. Następnie mogą skupić się na budowaniu i testowaniu logiki biznesowej. W związku z tym są w stanie korzystać z istniejących umiejętności do tworzenia logiki zaplecza dla aplikacji mobilnej bez konieczności uczenia się nowych platform lub stać się "deweloperem po stronie serwera".

![Bezserwerowy mobilny back end](./media/serverless-mobile-backend.png)

Większość dostawców chmury oferuje produkty bezserwerowe oparte na urządzeniach przenośnych, które upraszczają cały cykl rozwoju urządzeń mobilnych. Produkty mogą zautomatyzować inicjowanie obsługi administracyjnej baz danych w celu utrwaciania danych, obsługi problemów devops, zapewnienia kompilacji i struktur testowania opartych na chmurze oraz możliwości skryptowania procesów biznesowych przy użyciu preferowanego języka dewelopera. Po mobile-centric podejście bezserwerowe może usprawnić proces. Bezserwerowe usuwa ogromne obciążenie aprowizacji, konfigurowania i utrzymywania serwerów dla zaplecza mobilnego.

## <a name="internet-of-things-iot"></a>Internet rzeczy (IoT)

IoT odnosi się do obiektów fizycznych, które są połączone w sieć. Są one czasami określane jako "podłączone urządzenia" lub "inteligentne urządzenia". Wszystko, od samochodów i automatów, może być połączone i wysyłać informacje, począwszy od inwentaryzacji, po dane z czujników, takie jak temperatura i wilgotność. W przedsiębiorstwie IoT zapewnia ulepszenia procesów biznesowych poprzez monitorowanie i automatyzację. Dane IoT mogą być wykorzystywane do regulowania klimatu w dużym magazynie lub śledzenia zapasów w łańcuchu dostaw. IoT może wyczuć wycieki substancji chemicznych i wezwać straż pożarną po wykryciu dymu.

Ogromna ilość urządzeń i informacji często dyktuje architekturze stertej zdarzeniami, aby wysyłać i przetwarzać wiadomości. Serverless to idealne rozwiązanie z kilku powodów:

- Włącza skalowanie wraz ze wzrostem liczby urządzeń i danych.
- Umożliwia dodawanie nowych punktów końcowych do obsługi nowych urządzeń i czujników.
- Ułatwia niezależne przechowywanie wersji, dzięki czemu deweloperzy mogą aktualizować logikę biznesową dla określonego urządzenia bez konieczności wdrażania całego systemu.
- Odporność i mniej przestojów.

Wszechobecność IoT spowodowała, że kilka produktów bez serwerów koncentruje się w szczególności na problemach z IoT, takich jak [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Bezserwerowe automatyzuje zadania, takie jak rejestracja urządzeń, wymuszanie zasad, śledzenie, a nawet wdrażanie kodu na urządzeniach *na brzegu .* Krawędź odnosi się do urządzeń, takich jak czujniki i siłowniki, które są podłączone do Internetu, ale nie jest to aktywna część Internetu.

>[!div class="step-by-step"]
>[Poprzedni](architecture-approaches.md)
>[następny](serverless-architecture-considerations.md)
