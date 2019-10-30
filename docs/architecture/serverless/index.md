---
title: 'Aplikacje bezserwerowe: architektura, wzorce i implementacja platformy Azure'
description: Przewodnik dotyczący architektury bezserwerowej. Dowiedz się, kiedy i w jaki sposób zaimplementować architekturę bezserwerową (w przeciwieństwie do infrastruktury jako usługi [IaaS] lub platformy jako usługi [PaaS]) dla aplikacji dla przedsiębiorstw.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 9dea7dbccb5c9e125f792e6a7287a7dd2fad26f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093545"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Aplikacje bezserwerowe: architektura, wzorce i implementacja platformy Azure

![Zrzut ekranu przedstawiający centrum poczty elektronicznej aplikacji bezserwerowych.](./media/index/serverless-apps-cover.jpg)

> Pobieranie dostępne o: <https://aka.ms/serverless-ebook>

OPUBLIKOWANO PRZEZ

Zespoły deweloperów firmy Microsoft, .NET i Visual Studio

Dział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2018 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre przykłady opisane w niniejszym dokumencie są dostępne tylko dla ilustracji i są fikcyjne. Żadne prawdziwe skojarzenie lub połączenie nie jest zamierzone ani nie powinno zostać wywnioskowane.

Firma Microsoft i znaki towarowe wymienione w <https://www.microsoft.com> na stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.

Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.

Tworzone

> **[Jeremy Likness](https://twitter.com/jeremylikness)** , starszy ambasador w chmurze, Microsoft Corp.

Trybu

> **[Cecil Phillip](https://twitter.com/cecilphillip)** , starszy ambasador w chmurze, Microsoft Corp.

Edytory

> **[Bill Wagner](https://twitter.com/billwagner)** , Starszy programista ds. zawartości, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)** , Starszy programista ds. zawartości, Microsoft Corp.

Uczestnicy i recenzenci:

> **[Steve Smith](https://twitter.com/ardalis)** , Owner, Ardalis Services.

## <a name="introduction"></a>Wprowadzenie

[Bezserwerowy](https://azure.microsoft.com/solutions/serverless/) to ewolucja platform w chmurze w kierunku czystego natywnego kodu w chmurze. Bezserwerowe serwery zapewniają deweloperom bliższą logikę biznesową, jednocześnie izolując ich od obaw związanych z infrastrukturą. Jest to wzorzec, który nie implikuje "No Server", ale raczej "Less Server". Kod bezserwerowy jest sterowany zdarzeniami. Kod może być wyzwalany przez dowolne elementy od tradycyjnego żądania sieci Web HTTP do czasomierza lub wynik przekazywania pliku. Infrastruktura za bezserwerową umożliwia natychmiastowe skalowanie w celu spełnienia elastycznych wymagań i oferuje szeroką rozliczenie za użycie. Bezserwerowy wymaga nowego sposobu podejścia do tworzenia aplikacji i nie jest odpowiednim rozwiązaniem dla każdego problemu. Jako programista musisz wybrać:

- Jakie są zalety i wady bezserwerowe?
- Dlaczego należy wziąć pod uwagę bezserwerowe aplikacje?
- Jak można kompilować, testować, wdrażać i obsługiwać kod bezserwerowy?
- Gdzie warto przeprowadzić migrację kodu do aplikacji bezserwerowej w istniejących aplikacjach i jak najlepiej wykonać tę transformację?

## <a name="about-this-guide"></a>Informacje o tym przewodniku

Ten przewodnik koncentruje się na natywnym programowaniu aplikacji, które używają bezserwerowego programu. Książka wyróżnia korzyści i ujawnia potencjalne wady tworzenia aplikacji bezserwerowych i udostępnia Przegląd architektury bezserwerowej. Wiele przykładów wykorzystania bezserwerowego można zobaczyć wraz z różnymi wzorcami projektowymi bez użycia serwera.

W tym przewodniku objaśniono składniki platformy bezserwerowej platformy Azure i koncentruje się na implementacji bezserwerowej przy użyciu [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview). Zapoznaj się z wyzwalaczami i powiązaniami oraz sposobem implementacji aplikacji bezserwerowych, które są zależne od stanu przy użyciu funkcji trwałych. Na koniec przykłady biznesowe i analizy przypadków ułatwią dostarczenie kontekstu i ramki odniesienia, aby określić, czy bezserwerowy jest właściwym podejściem do projektów.

## <a name="evolution-of-cloud-platforms"></a>Ewolucja platform w chmurze

Bezserwerowy jest culmination kilku iteracji platformy w chmurze. Ewolucja rozpoczęła się z materiałem fizycznym w centrum danych i postępuje za pomocą infrastruktury jako usługi (IaaS) i platformy jako usługi (PaaS).

![Ewolucja w środowisku lokalnym do bezserwerowego](./media/serverless-evolution-iaas-paas.png)

Przed chmurą istniała różnica między programowaniem a operacją. Wdrożenie aplikacji, która odpowiada na pytania wyposażono, takie jak:

- Jakiego sprzętu należy zainstalować?
- Jak bezpieczny jest fizyczny dostęp do maszyny?
- Czy centrum danych wymaga zasilacza awaryjnego (UPS)?
- Gdzie są wysyłane kopie zapasowe magazynu?
- Czy istnieje nadmiarowa moc?

Ta lista jest włączona, a obciążenie było ogromne. W wielu sytuacjach działy IT były zmuszeni do postępowania z niezwykłą ilością odpadów. Przyczyną jest nadmierne przydzielanie serwerów jako maszyn zapasowych na potrzeby odzyskiwania po awarii i serwerów rezerwy, aby umożliwić skalowanie w poziomie. Na szczęście wprowadzenie technologii wirtualizacji (takich jak [Funkcja Hyper-V](/virtualization/hyper-v-on-windows/about/)) z Virtual Machines (maszyny wirtualne) spowodowało powstanie infrastruktury jako usługi (IaaS). Zwirtualizowana infrastruktura umożliwia wykonywanie operacji w celu skonfigurowania standardowego zestawu serwerów jako szkieletu, co prowadzi do elastycznego środowiska z możliwością aprowizacji unikatowych serwerów na żądanie. Co ważniejsze, wirtualizacja ustawia etap korzystania z chmury w celu zapewnienia maszyn wirtualnych "jako usługi". Firmy mogą łatwo uzyskać informacje o nadmiarowych maszynach lub komputerach fizycznych. Zamiast tego koncentrują się na środowisku wirtualnym.

IaaS nadal wymaga dużego nakładu pracy, ponieważ operacje są nadal odpowiedzialne za różne zadania. Te zadania obejmują:

- Stosowanie poprawek i tworzenie kopii zapasowych serwerów.
- Instalowanie pakietów.
- Utrzymywanie Aktualności systemu operacyjnego.
- Monitorowanie aplikacji.

Kolejna ewolucja obniżyć koszty dzięki udostępnieniu platformy jako usługi (PaaS). W przypadku usługi PaaS dostawca chmury obsługuje systemy operacyjne, poprawki zabezpieczeń, a nawet pakiety wymagane do obsługi określonej platformy. Zamiast tworzyć maszyny wirtualne, a następnie konfigurować .NET Framework i stałe serwery Internet Information Services (IIS), deweloperzy po prostu wybierają "obiekty docelowe platformy", takie jak "aplikacja sieci Web" lub "punkt końcowy interfejsu API" i bezpośrednio wdrażają kod. Pytania dotyczące infrastruktury są ograniczone do:

- Jakie usługi rozmiaru są potrzebne?
- Jak są skalowane usługi (Dodaj więcej serwerów lub węzłów)?
- Jak są skalowane usługi (zwiększyć pojemność serwerów hostingu lub węzłów)?

Serwerowe bardziej abstrakcyjne serwery, koncentrując się na kodzie sterowanym zdarzeniami. Zamiast platformy deweloperzy mogą skupić się na mikrousłudze, która wykonuje jedną czynność. Dwa kluczowe pytania dotyczące kompilowania kodu bezserwerowego są następujące:

- Co wyzwala kod?
- Do czego służy kod?

Bez serwera, infrastruktura jest abstrakcyjna. W niektórych przypadkach deweloperzy nie będą już martw o hoście. Niezależnie od tego, czy wystąpienie usług IIS, Kestrel, Apache lub innego serwera sieci Web jest uruchomione do zarządzania żądaniami sieci Web, deweloper koncentruje się na wyzwalaczu HTTP. Wyzwalacz zawiera standardowy, międzyplatformowy ładunek dla żądania. Ładunek nie tylko upraszcza proces opracowywania, ale ułatwia testowanie i w niektórych przypadkach sprawia, że kod jest łatwo przenośny między platformami.

Inna funkcja bezserwerowa to bardzo rozliczenia. Często aplikacje sieci Web mogą hostować punkty końcowe interfejsu API sieci Web. W tradycyjnych tradycyjnym systemie IaaS i nawet implementacjach PaaS zasoby do hostowania interfejsów API są płatne w sposób ciągły. Oznacza to, że płacisz będzie hostować punkty końcowe nawet wtedy, gdy nie są dostępne. Często znajdziesz jeden interfejs API o nazwie więcej niż inne, więc cały system jest skalowany w oparciu o obsługę popularnych punktów końcowych. Funkcja bezserwerowa umożliwia niezależne skalowanie każdego punktu końcowego i płatność za użycie, więc żadne koszty nie są naliczane, gdy interfejsy API nie są wywoływane. Migracja może w wielu przypadkach znacząco obniżyć koszty związane z punktami końcowymi.

## <a name="what-this-guide-doesnt-cover"></a>Czym nie obejmuje ten przewodnik

W tym przewodniku szczegółowo omówiono podejścia do architektury i wzorce projektowe i nie jest głębokie szczegółowe w szczegółach implementacji Azure Functions, [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)lub innych platform bezserwerowych. Ten przewodnik nie obejmuje na przykład zaawansowanych przepływów pracy z Logic Appsami lub funkcjami Azure Functions, takimi jak Konfigurowanie udostępniania zasobów między źródłami (CORS), stosowanie domen niestandardowych lub przekazywanie certyfikatów SSL. Te szczegóły są dostępne w [dokumentacji Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-reference)online.

### <a name="additional-resources"></a>Dodatkowe zasoby

- [Centrum architektury platformy Azure](https://docs.microsoft.com/azure/architecture/)
- [Najlepsze rozwiązania dla aplikacji w chmurze](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kto powinien korzystać z przewodnika

Ten przewodnik został utworzony dla deweloperów i architektów rozwiązań, którzy chcą kompilować aplikacje dla przedsiębiorstw przy użyciu platformy .NET, które mogą korzystać ze składników bezserwerowych w środowisku lokalnym lub w chmurze. Jest to przydatne dla deweloperów, architektów i decyzji technicznych zainteresowanych:

- Zrozumienie specjalistów i wad tworzenia bezserwerowego
- Nauka podejścia do architektury bezserwerowej
- Przykładowe implementacje aplikacji bezserwerowych

## <a name="how-to-use-the-guide"></a>Jak korzystać z przewodnika

W pierwszej części tego przewodnika sprawdzono, dlaczego serwer jest opłacalną opcją, porównując kilka różnych metod architektury. Bada ona zarówno cykl życia technologii, jak i programowania, ponieważ wszystkie aspekty opracowywania oprogramowania mają wpływ na decyzje architektury. Przewodnik bada przypadki użycia i wzorce projektowe i zawiera implementacje odwołań przy użyciu Azure Functions. Każda sekcja zawiera dodatkowe zasoby, aby dowiedzieć się więcej na temat określonego obszaru. Przewodnik zawiera zasoby dla przewodników i praktycznej eksploracji implementacji bezserwerowej.

## <a name="send-your-feedback"></a>Wyślij opinię

Przewodnik i powiązane przykłady są stale rozwijane, więc Twoje opinie są gotowe! Jeśli masz komentarze dotyczące sposobu, w jaki można ulepszyć ten przewodnik, Skorzystaj z sekcji opinia w dolnej części strony utworzonej w witrynie [GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](architecture-approaches.md)
