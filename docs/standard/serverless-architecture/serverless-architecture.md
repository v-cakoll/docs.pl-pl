---
title: Architektura bezserwerowa — aplikacje niekorzystające z serwera
description: Badań różnych architektur oraz aplikacje, które są obsługiwane przez architektury bezserwerowe, w tym aplikacje sieci web, mobilnych i IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f22f8b9894a23e5920adb2af3fdf02bce2877d7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150306"
---
# <a name="serverless-architecture"></a>Architektura bezserwerowa

Dostępnych jest wiele metod, aby przy użyciu architektur bezserwerowych. W tym rozdziale przedstawiono przykłady typowych architektur, które integrują się bez użycia serwera. Obejmuje ona również kwestie, które mogą stanowić wyzwania dodatkowe lub wymagają dodatkowych brany pod uwagę podczas implementowania bez użycia serwera. Na koniec kilka przykładów projektu są pod warunkiem, które ilustrują, różne przypadki użycia bez użycia serwera.

Bez użycia serwera hostów często używają istniejącego opartych na kontenerach lub warstwy PaaS do zarządzania wystąpieniami bez użycia serwera. Na przykład, na podstawie usługi Azure Functions [usługi Azure App Service](https://docs.microsoft.com/azure/app-service/). Usługa App Service umożliwia skalowanie w poziomie wystąpienia i zarządzanie nimi środowiska uruchomieniowego, który jest wykonywany kod usługi Azure Functions. W przypadku funkcji z systemem Windows działa hosta jako PaaS i skaluje się poza środowisko uruchomieniowe platformy .NET. Dla funkcji opartych na systemie Linux host korzysta z kontenerów.

![Architektura usługi Azure Functions](./media/azure-functions-architecture.png)

Podstawowe zadania Webjob udostępnia kontekst wykonania dla funkcji. Środowisko uruchomieniowe języka uruchamia skrypty, wykonuje bibliotek i obsługuje framework dla języka docelowego. Na przykład środowisko Node.js jest używane do uruchamiania funkcji języka JavaScript i .NET Framework jest używany do uruchamiania funkcji języka C#. Dowiesz się więcej na temat opcji języka i platformy dalej w tym rozdziale.

Niektóre projekty mogą korzystać z Przenosimy podejścia "całości opartą" bez użycia serwera. Aplikacje, które w dużym stopniu polegają na mikrousługi może wdrożyć wszystkie mikrousługi korzystające z technologii bezserwerowej. Większość aplikacji jest hybrydowych, następującego projektu N-warstwowa i składników, które mają sens, ponieważ składniki programu są moduły i skalowalnego niezależnie przy użyciu bezserwerowej. Aby poznać te scenariusze, w tej sekcji przedstawiono typowe przykłady architektury używających bez użycia serwera.

## <a name="full-serverless-back-end"></a>Pełne bez użycia serwera zaplecza

Pełne bezserwerowe zaplecze jest idealny dla kilka typów scenariuszy, szczególnie w przypadku tworzenia nowego lub aplikacje "green field". Aplikacji za pomocą dużej powierzchni interfejsów API może korzystać z wdrażania każdy interfejs API jako funkcję niewymagającą użycia serwera. Aplikacje, które są oparte na architekturze mikrousług są inny przykład, w którym można zaimplementować jako pełna bez użycia serwera zaplecza. Mikrousługi komunikują się za pośrednictwem różnych protokołów, które ze sobą. Konkretne scenariusze obejmują:

* Oparte na interfejsie API produktów SaaS (przykład: procesor płatności finansowe).
* Opartych na wiadomościach aplikacji (przykład: urządzenie rozwiązanie do monitorowania).
* Aplikacje koncentruje się na integrację między usługami (przykład: aplikacja rezerwacji linii lotniczych).
* Procesy okresowe uruchamianie (przykład: czyszczenie oparte na czasomierzu bazy danych).
* Aplikacje koncentruje się na przekształcania danych (przykład: Importuj wyzwolone przez przekazywanie pliku).
* Wyodrębnij procesów transformacji i ładowania (ETL).

Istnieją inne, bardziej szczegółowe przypadki użycia, które zostały omówione w dalszej części tego dokumentu.

## <a name="monoliths-and-starving-the-beast"></a>Monolitycznych projektów i "blokują beast"

Typowe wyzwania jest migracja istniejącej aplikacji monolitycznych w chmurze. Co najmniej ryzykowne podejściem jest metodą "lift and shift" całkowicie na maszynach wirtualnych. Preferuj wielu sklepach na potrzeby migracji jako możliwość poczynienia modernizuj swoje bazy kodu. Praktyczne podejście do migracji jest nazywany "blokują beast". W tym scenariuszu monolitu jest migrowane "is" zaczynać. Następnie są zmodernizowane wybranych usług. W niektórych przypadkach podpis usługi jest taka sama jak oryginalny: po prostu jest obsługiwany w funkcji. Klienci zostaną zaktualizowani do użycia nową usługę, a nie punktu końcowego monolitu. W międzyczasie czynności, takie jak replikacja bazy danych, Włącz mikrousług, co umożliwia hostowanie własnych magazynu nawet wtedy, gdy transakcje są nadal obsługiwane przez monolitu. Po pewnym czasie wszyscy klienci są migrowane do nowych usług. Monolityczna jest "przetrzymywany" (jego usługi nie jest już wywoływana) do momentu wszystkie funkcje zostały zastąpione. Kombinacja bez użycia serwera i serwery proxy może ułatwić znaczną część tej migracji.

![Migracja monolitu bez użycia serwera](./media/serverless-monolith-migration.png)

Aby dowiedzieć się więcej na temat tego podejścia, Obejrzyj klip wideo: [Udostępnij swoją aplikację w chmurze przy użyciu bezserwerowej usługi Azure Functions](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Aplikacje internetowe

Aplikacje sieci Web są doskonałymi kandydatami do aplikacji bez użycia serwera. Istnieją dwie metody wspólne aplikacje sieci web już dzisiaj: opartych na serwerze i opartych na klienta (na przykład aplikacja jednostronicowa lub SPA). Aplikacje oparte na serwerze sieci web zazwyczaj korzystają warstwa oprogramowania pośredniczącego do wysyłania wywołania interfejsu API do renderowania interfejsu użytkownika sieci web. SPA aplikacji wykonywanie wywołań interfejsu API REST bezpośrednio z przeglądarki. W obu przypadkach bez użycia serwera może obsłużyć żądania interfejsu API REST lub oprogramowanie pośredniczące, udostępniając logikę biznesową niezbędne. Architektura jest do wdrożenia serwera uproszczone statyczną sieci web. Jednej strony aplikacji (SPA) służy HTML, CSS, JavaScript i inne zasoby przeglądarki. Aplikacja internetowa łączy się następnie z zapleczem mikrousług.

## <a name="mobile-back-ends"></a>Zaplecza aplikacji mobilnych

Paradygmat oparte na zdarzeniach, bezserwerowe aplikacje sprawia, że ich idealne jako mobilnych zaplecza. Urządzenie przenośne wyzwala zdarzenia i wykonuje kod bez użycia serwera, do spełnienia żądania. Korzystając z zalet modelu bez użycia serwera pozwala deweloperom na rozszerzanie logiki biznesowej bez konieczności wdrażania aktualizacji pełnej aplikacji. Bez użycia serwera podejście również umożliwia zespołom udostępnianie punktów końcowych i działają równolegle.

Przenośne deweloperzy mogą tworzyć logiki biznesowej bez staje się ekspertami po stronie serwera. Tradycyjnie aplikacje mobilne połączone usługami lokalnymi. Tworzenie warstwy usług wymagane informacje o platformie server paradygmat programowania. Deweloperzy pracowano operacje, aby aprowizować serwery i odpowiednio je skonfigurować. Czasami dni lub nawet tygodnie spędzono na tworzeniu potoku wdrożenia. Wszystkie te wyzwania dotyczą bez użycia serwera.

Aplikacje niewymagające użycia serwera przenosi zależności po stronie serwera i umożliwia deweloperom skoncentrowanie się na logice biznesowej. Na przykład dla deweloperów aplikacji mobilnych, który tworzy aplikacje przy użyciu platformy JavaScript, można tworzyć funkcje niewymagające użycia serwera za pomocą języka JavaScript oraz. Bez użycia serwera hosta zarządza systemu operacyjnego, wystąpienie programu Node.js do hostowania kodu, zależności pakietów i nie tylko. Deweloper jest udostępniana prosty zestaw danych wejściowych i standardowego szablonu dla danych wyjściowych. Następnie mogli skoncentrować się na tworzenie i testowanie logiki biznesowej. Są one mogli używać swoich umiejętności do tworzenia logiki zaplecza dla aplikacji mobilnej bez konieczności Dowiedz się, nowe platformy i stają się "deweloperów po stronie serwera."

![Kończy zaplecza bez użycia serwera aplikacji mobilnych](./media/serverless-mobile-backend.png)

Większość dostawców rozwiązań w chmurze oferują mobile produktów opartych na bez użycia serwera, które upraszczają całego przenośnych cyklu życia. Produkty mogą zautomatyzować aprowizację baz danych w celu utrwalenia danych, obsługa dotyczy metodyki DevOps, oparte na chmurze kompilacji i testowania, struktur i możliwość procesów biznesowych skryptu przy użyciu projektanta preferowanego języka. Następujące podejście bez użycia serwera skoncentrowane na telefon komórkowy może uprościć proces. Aplikacje niewymagające użycia serwera usuwa ogromną obciążenie inicjowania obsługi, konfigurowania i utrzymywania serwerów zaplecza mobilnego.

## <a name="internet-of-things-iot"></a>Internet rzeczy (IoT)

IoT odnosi się do obiektów fizycznych, które są połączone. Są one nazywane "podłączonych urządzeń" i "inteligentnych urządzeń". Wszystko — od samochodów i automaty mogą być połączone i wysyłanie informacji od magazynu danych czujników, takich jak temperatury i wilgotności. W przedsiębiorstwie IoT oferuje ulepszenia procesów biznesowych za pośrednictwem monitorowania i automatyzacji. Dane IoT mogą służyć do regulowania klimatu w magazynie dużych lub śledzenie stanu magazynu za pomocą łańcucha dostaw. IoT można sens wycieki chemicznych, a następnie skontaktować się z działem fire po wykryciu dymu.

Znaczne zmniejszenie ilości urządzeń i informacji często mówią, architektura sterowana zdarzeniami trasy i przetwarzania komunikatów. Bez użycia serwera to idealne rozwiązanie z kilku powodów:

* Umożliwia skalowanie jako wolumin zwiększa urządzeń i danych.
* Obsługuje dodawanie nowych punktów końcowych do obsługi nowych urządzeń i czujników.
* Ułatwia niezależnie od wersji, dzięki czemu deweloperzy mogą zaktualizować logikę biznesową dla określonego urządzenia bez konieczności wdrażania całego systemu.
* Odporność i minus Przestój.

Wszechobecność IoT spowodowało kilka produktów bez użycia serwera koncentrujących się szczególnie na obaw IoT, takich jak [usługi Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Aplikacje niewymagające użycia serwera automatyzuje zadania, takie jak rejestracji urządzeń, wymuszanie zasad zostaje wyłączone, śledzenia i nawet wdrożenie kodu do urządzeń *krawędzi*. Krawędź odnosi się do urządzenia, na przykład czujniki i elementy wykonawcze, które są podłączone do, ale active część z Internetu.

>[!div class="step-by-step"]
>[Poprzednie](architecture-approaches.md)
>[dalej](serverless-architecture-considerations.md)