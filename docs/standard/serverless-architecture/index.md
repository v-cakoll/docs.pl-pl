---
title: 'Aplikacje niewymagające użycia serwera: Architektura, wzorce i implementacji platformy Azure'
description: 'Przewodnik dotyczący architektury bezserwerowej. Dowiedz się, kiedy, dlaczego i jak zaimplementować architekturę bezserwerową (w przeciwieństwie do infrastruktury jako usługi [IaaS] lub platforma jako usługa [PaaS]) w twoich aplikacjach firmowych.'
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 6/26/2018
---

# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Aplikacje niewymagające użycia serwera: Architektura, wzorce i implementacji platformy Azure

![Zrzut ekranu pokazujący cover książki elektronicznej aplikacje niewymagające użycia serwera.](./media/index/serverless-apps-cover.jpg)

> Pobierz dostępne pod adresem: <https://aka.ms/serverless-ebook>

OPUBLIKOWANE PRZEZ

Zespoły produktu Microsoft Developer Division, .NET i Visual Studio

Dzielenie firmy Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 Microsoft Corporation

Wszelkie prawa zastrzeżone. Nie części zawartości tej książki może odtworzyć lub przenoszone w jakiejkolwiek formie lub za pomocą jakichkolwiek środków bez pisemnej zgody wydawcy.

Ten podręcznik jest dostarczany "jako — jest" i wyraża, widoki i opinie od autora. Widoki, opinie i informacje wyrażone w tym podręczniku, w tym adresy URL i inne odnośniki do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przedstawione przykłady znajdują się wyłącznie do celów informacyjnych i są fikcyjne. Nie rzeczywiste skojarzenia ani powiązania nie są zamierzone ani powinny być zakładane.

Firma Microsoft i znaków towarowych, opisane w temacie <https://www.microsoft.com> na stronie sieci Web "Znakami" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i z systemem macOS są znakami towarowymi firmy Apple Inc.

Wszystkie inne znaki i logo są własnością ich prawnych właścicieli.

Autor:

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, Sr. Cloud Developer Advocate, APEX, Microsoft Corp.

Współautor:

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, Cloud Developer Advocate II, APEX, Microsoft Corp.

Edytory:

> **[Bill Wagnera](https://twitter.com/billwagner)**, starszy zawartości dla deweloperów, WIERZCHOŁKU, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)**, starszy zawartości dla deweloperów, WIERZCHOŁKU, Microsoft Corp.

Uczestnicy i osób dokonujących przeglądu:

> **[Steve Smith](https://twitter.com/ardalis)**, właściciel, Ardalis usług.

## <a name="introduction"></a>Wprowadzenie

[Bez użycia serwera](https://azure.microsoft.com/solutions/serverless/) stanowi ewolucyjne rozwinięcie funkcji platformach w chmurze w kierunku kodu natywnego w chmurze. Aplikacje niewymagające użycia serwera udostępnia deweloperom bliżej logiki biznesowej podczas izolacji je z uwagi infrastrukturze. Jest to wzorzec, który nie oznacza "nie server" ale raczej "mniej serwera." Kod bezserwerowy jest oparte na zdarzeniach. Kod może zostać wyzwolone przez coś z tradycyjnych żądania sieci web HTTP czasomierz lub wynik przekazywania pliku. Infrastruktura za bez użycia serwera umożliwia natychmiastowe skalowanie do spełnienia wymagań elastyczne i oferuje micro rozliczeń, aby naprawdę "płatność za rzeczywiste użycie." Aplikacje niewymagające użycia serwera wymaga nowy sposób myślenia i podejścia do tworzenia aplikacji i nie jest właściwe rozwiązanie dla każdego problemu. Jako deweloper musi określić:

* Co to są zalet i wad bez użycia serwera?
* Dlaczego należy rozważyć bez użycia serwera na potrzeby własnych aplikacji?
* Jak można możesz kompilacji, testowania, wdrażania i utrzymywać kod bez użycia serwera?
* Gdzie ma to sens migrację kodu do bezserwerowego w istniejących aplikacji i co to jest najlepszym sposobem, aby wykonać to przekształcenie?

## <a name="about-this-guide"></a>Przewodnik — informacje

Ten przewodnik koncentruje się na chmurze natywnych aplikacji, które używają bez użycia serwera. Książka prezentuje korzyści i ujawnia potencjalne niedogodności związanych z tworzeniem aplikacji bez użycia serwera i zawiera Przegląd architektur bez użycia serwera. Wiele przykładów jak bezserwerowe mogą służyć przedstawiono wraz z różnych wzorców projektowych bez użycia serwera.

W tym przewodniku opisano składniki platformy Azure, bez użycia serwera oraz koncentruje się szczegółowe informacje dotyczące wdrożenia bez użycia serwera za pomocą [usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview). Poznasz wyzwalaczy i powiązań oraz jak wdrożyć aplikacje bezserwerowe, które zależą od stanu przy użyciu funkcje trwałe. Na koniec firm przykłady i analizy przypadków ułatwi zrozumienie kontekstu i odniesienia do określenia czy jest to bezserwerowe jest właściwe podejście dla Twoich projektów.

## <a name="evolution-of-cloud-platforms"></a>Ewolucja platformy chmury

Bez użycia serwera jest culmination kilku iteracji cloud platform. Rozwój rozpoczęło się o fizyczne bez systemu operacyjnego w centrum danych i wykazała postępów za pomocą infrastruktury jako usługi (IaaS) oraz platforma jako usługa (PaaS).

![Ewolucja ze środowiska lokalnego do bez użycia serwera](./media/serverless-evolution-iaas-paas.png)

Przed chmury zauważalny granic istniał między środowiskami deweloperskim i operacji. Wdrażanie aplikacji przeznaczony na udzielenie odpowiedzi na pytania wiele takich jak:

* Jaki sprzęt, należy zainstalować?
* W jaki sposób dostęp fizyczny do maszyny chronione?
* Centrum danych wymaga awaryjny (UPS)?
* Gdzie są wysyłane kopie zapasowe magazynu
* Powinna istnieć nadmiarowe zasilanie?

Lista przechodzi i czasu obciążenie. W wielu sytuacjach działom IT zostały zmuszeni do czynienia z niezwykłą strat. Strata związana została z powodu nadmiernego alokowania miejsca serwerów jako kopii zapasowej maszyny na potrzeby odzyskiwania i gotowości serwery po awarii umożliwiające skalowalnego w poziomie. Na szczęście wprowadzenie technologii wirtualizacji (np. [funkcji Hyper-V](/virtualization/hyper-v-on-windows/about/)) przy użyciu maszyn wirtualnych (VM) spowodowały infrastruktura jako usługa (IaaS). Infrastruktury zwirtualizowanej dozwolone operacje, aby skonfigurować standardowy zestaw serwerów jako sieć szkieletową tego systemu, co prowadzi do elastyczne środowisko zdolne do obsługi unikatowych serwerów "na żądanie." Co ważniejsze, wirtualizacji przygotowanie się do używania w chmurze w celu zapewnienia maszyn wirtualnych "jako"usługa. Firmom łatwe można pobrać działalność o nadmiarowe zasilanie lub komputerów fizycznych. Zamiast tego są koncentruje się na środowisku wirtualnym.

IaaS nadal wymaga duże obciążenie, ponieważ operacje jest odpowiedzialny za dla różnych zadań. Te zadania obejmują:

* Stosowanie poprawek i tworzenie kopii zapasowych serwerów.
* Instalowanie pakietów.
* Aktualizowanie systemu operacyjnego.
* Monitorowanie aplikacji.

Kolejny etap ewolucji mniejsze obciążenie, zapewniając platformę jako usługę (PaaS). Dzięki temu dostawcy chmury obsługuje systemy operacyjne, poprawki zabezpieczeń i nawet pakiety wymagane do obsługi określonej platformy. Zamiast tworzenia maszyny Wirtualnej, a następnie skonfigurowanie programu .NET Framework i stałego serwery usług Internet Information Services (IIS), deweloperzy po prostu wybierz opcję "target platformy" np. "aplikacja sieci web" lub "Punkt końcowy interfejsu API" i wdrażanie kodu bezpośrednio. Pytania dotyczące infrastruktury zostały ograniczone do:

* Jakie usługi rozmiar są potrzebne?
* Jak usługi skalowania w poziomie (Dodawanie większej liczby serwerów lub węzły)?
* Jak usługi skalowania w górę (zwiększyć pojemność hostingu, serwerów lub węzły)?

Bez użycia serwera dodatkowe serwery Abstract, koncentrując się na kodzie oparte na zdarzeniach. Zamiast to platforma deweloperzy mogą skoncentrować się na mikrousługach, który wykonuje jedną z rzeczy. Są dwa ważne pytania dotyczące tworzenia kodu bez serwera:

* Wyzwalacze kod?
* Do czego służy ten kod?

Przy użyciu bezserwerowej, infrastruktura jest wyodrębniony. W niektórych przypadkach deweloper nie jest już worries o hoście wcale. Czy wystąpienia usług IIS, Kestrel, Apache lub inny serwer sieci web jest uruchomiona w celu zarządzania żądaniami sieci web, deweloper koncentruje się na wyzwalacz HTTP. Wyzwalacz oferuje standardowe, Międzyplatformowe ładunku żądania. Ładunek nie tylko upraszcza proces tworzenia, ale ułatwia tworzenie, testowanie i w niektórych przypadkach sprawia, że kod przenośny łatwo między platformami.

Kolejną funkcją operacji jest micro rozliczeń. Jest to częsty problem w aplikacji sieci web do punktów końcowych interfejsu API sieci Web hosta. W tradycyjnych komputerów bez systemu operacyjnego, IaaS i nawet implementacji PaaS, zasoby, które mają hostować interfejsy API są opłacony stale. Oznacza to, że płaci się do obsługi punktów końcowych, nawet wtedy, gdy nie są wykorzystywane. Często można znaleźć jednego wywołania interfejsu API bardziej niż inne, dzięki czemu cały system jest skalowany w oparciu o obsłudze popularnych punktów końcowych. Aplikacje niewymagające użycia serwera umożliwia niezależne skalowanie obu elementów każdy punkt końcowy, a opłata za użycie, dzięki czemu żadnych kosztów są naliczane, gdy nie są wywoływane za pośrednictwem interfejsów API. Migracja może w wielu sytuacjach znacznie zmniejszyć bieżące koszty w celu obsługi punktów końcowych.

## <a name="what-this-guide-doesnt-cover"></a>Co ten przewodnik nie obejmuje

Ten przewodnik specjalnie kładzie nacisk na metody dotyczące architektury i projektowania wzorców i nie jest szczegółowo omówi szczegóły implementacji usługi Azure Functions [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps), lub na innych platformach bez użycia serwera. Ten przewodnik nie obejmuje na przykład zaawansowanych przepływów pracy za pomocą aplikacji logiki lub funkcji usługi Azure Functions, takich jak konfigurowanie udostępniania zasobów między źródłami (CORS), stosując domen niestandardowych lub przekazywanie certyfikatów SSL. Te informacje są dostępne za pośrednictwem online [dokumentacji usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-reference).

### <a name="additional-resources"></a>Dodatkowe zasoby

* [Centrum architektury platformy Azure](https://docs.microsoft.com/azure/architecture/)
* [Najlepsze rozwiązania dotyczące aplikacji w chmurze](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kto powinien używać przewodnik

Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, którzy chcą tworzyć aplikacje dla przedsiębiorstw przy użyciu platformy .NET, która może używać bez użycia serwera składników w środowisku lokalnym lub w chmurze. Warto techniczne inne osoby podejmujące decyzje zainteresowani, architektów i deweloperów:

* Informacje o zaletach i wadach deweloperskie bez serwera
* Jak podejście do architektury bezserwerowej
* Przykładowe implementacje aplikacje niewymagające użycia serwera

## <a name="how-to-use-the-guide"></a>Jak korzystać z przewodnikiem

Pierwsza część tego przewodnika sprawdza Dlaczego bez użycia serwera jest wygodną opcją, porównując różne podejścia innej architektury. Sprawdza, czy technologii i rozwoju cyklu życia, ponieważ wszystkie aspektami opracowywania oprogramowania mają wpływ decyzji architektury. Przewodnik sprawdza następnie przypadki użycia i wzorców projektowania i zawiera odwołanie do implementacji przy użyciu usługi Azure Functions. Każda sekcja zawiera dodatkowe zasoby, aby dowiedzieć się więcej o określonym obszarze. Przewodnik kończy się z zasobami na potrzeby przewodniki i praktyczne eksploracji implementacji bez użycia serwera.

## <a name="send-your-feedback"></a>Wyślij opinię

Wskazówki i przykłady są stale ewoluuje, dzięki czemu Twoja opinia jest przyjęte! Jeśli masz komentarze na temat sposobu ten przewodnik można zwiększyć, użyj sekcji opinii u dołu każdej strony w oparciu [problemy usługi GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](architecture-approaches.md)