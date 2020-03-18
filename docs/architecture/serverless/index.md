---
title: 'Aplikacje bezserwerowe: architektura, wzorce i implementacja platformy Azure'
description: Przewodnik po architekturze bezserwerowej. Dowiedz się, kiedy, dlaczego i jak zaimplementować architekturę bezserwerową (w przeciwieństwie do Infrastruktury jako usługi [IaaS] lub Platforma jako usługa [PaaS]) dla aplikacji korporacyjnych.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 9dea7dbccb5c9e125f792e6a7287a7dd2fad26f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73093545"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Aplikacje bezserwerowe: architektura, wzorce i implementacja platformy Azure

![Zrzut ekranu przedstawiający okładkę e-booków aplikacji bez serwerów.](./media/index/serverless-apps-cover.jpg)

> POBIERZ dostępny pod adresem:<https://aka.ms/serverless-ebook>

OPUBLIKOWANA PRZEZ

Zespoły produktów Microsoft Developer Division, .NET i Visual Studio

Oddział Firmy Microsoft Corporation

One Microsoft Way

Redmond (Waszyngton) 98052-6399

Prawa autorskie © 2018 przez Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część treści tej książki nie może być powielana lub przekazywana w jakiejkolwiek formie lub w jakikolwiek sposób bez pisemnej zgody wydawcy.

Ta książka jest "tak jak jest" i wyraża poglądy i opinie autora. Poglądy, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Microsoft i znaki towarowe <https://www.microsoft.com> wymienione na stronie internetowej "Znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Mac i macOS są znakami towarowymi firmy Apple Inc.

Wszystkie inne znaki i logo są własnością ich właścicieli.

Autor:

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, Starszy Rzecznik Chmury, Microsoft Corp.

Współautorów:

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, Starszy Rzecznik Chmury, Microsoft Corp.

Edytory:

> **[Bill Wagner](https://twitter.com/billwagner)**, Starszy programista treści, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)**, Starszy programista treści, Microsoft Corp.

Uczestnicy i recenzenci:

> **[Steve Smith](https://twitter.com/ardalis)**, Właściciel, Ardalis Services.

## <a name="introduction"></a>Wprowadzenie

[Bezserwerowe](https://azure.microsoft.com/solutions/serverless/) jest ewolucja platform w chmurze w kierunku czystego kodu natywnego chmury. Bezserwerowe przybliża deweloperów do logiki biznesowej, jednocześnie izolując ich od problemów z infrastrukturą. Jest to wzorzec, który nie oznacza "nie ma serwera", ale raczej "mniej serwera". Kod bezserwerowy jest oparty na zdarzeniach. Kod może być wyzwalany przez cokolwiek z tradycyjnego żądania sieci Web HTTP do czasoatora lub wynik przekazywania pliku. Infrastruktura stojąca za bezserwerową pozwala na natychmiastową skalę, aby sprostać elastycznym wymaganiom i oferuje mikro-rozliczenia, aby naprawdę "płacić za to, czego używasz". Bezserwerowe wymaga nowego sposobu myślenia i podejścia do tworzenia aplikacji i nie jest właściwym rozwiązaniem dla każdego problemu. Jako programista musisz zdecydować:

- Jakie są plusy i minusy bezserwerowe?
- Dlaczego warto wziąć pod uwagę bezserwerowe dla własnych aplikacji?
- Jak można tworzyć, testować, wdrażać i obsługiwać kod bezserwerowy?
- Gdzie ma sens migrowanie kodu do bezserwerowego w istniejących aplikacjach i jaki jest najlepszy sposób na wykonanie tej transformacji?

## <a name="about-this-guide"></a>O tym przewodniku

Ten przewodnik koncentruje się na natywnych dla chmury rozwoju aplikacji, które używają bezużycia serwera. Książka podkreśla korzyści i ujawnia potencjalne wady tworzenia aplikacji bezserwerowych i zapewnia ankietę architektur bezserwerowych. Wiele przykładów tego, jak można używać bezserwerowych, jest zilustrowanych wraz z różnymi wzorcami projektowania bez serwerów.

W tym przewodniku wyjaśniono składniki platformy bezserwerowej platformy Azure i koncentruje się w szczególności na implementacji bezserwerowej przy użyciu [funkcji Azure .](https://docs.microsoft.com/azure/azure-functions/functions-overview) Dowiesz się o wyzwalacze i powiązania, a także jak zaimplementować aplikacje bezużycia serwera, które opierają się na stanie przy użyciu funkcji trwałych. Na koniec przykłady biznesowe i studia przypadków pomogą zapewnić kontekst i ramy odniesienia, aby ustalić, czy bezserwerowe jest właściwym podejściem dla projektów.

## <a name="evolution-of-cloud-platforms"></a>Ewolucja platform chmurowych

Bezserwerowe jest kulminacją kilku iteracji platform w chmurze. Ewolucja rozpoczęła się od fizycznego metalu w centrum danych i przebiegała przez Infrastrukturę jako usługę (IaaS) i Platformę jako usługę (PaaS).

![Ewolucja od lokalnego do bezserwerowego](./media/serverless-evolution-iaas-paas.png)

Przed chmurą istniała dostrzegalna granica między programami deweloperskimi a operacjami. Wdrożenie aplikacji oznaczało udzielenie odpowiedzi na niezliczone pytania, takie jak:

- Jaki sprzęt powinien być zainstalowany?
- W jaki sposób fizyczny dostęp do urządzenia jest zabezpieczony?
- Czy centrum danych wymaga zasilacza awaryjnego (UPS)?
- Gdzie są wysyłane kopie zapasowe magazynu?
- Czy powinna istnieć nadmiarowa moc?

Lista jest długa, a obciążenie było ogromne. W wielu sytuacjach działy IT były zmuszone do radzenia sobie z niesamowitymi odpadami. Odpady były spowodowane nadmierną alokacją serwerów jako maszyn zapasowych do odzyskiwania po awarii i serwerów rezerwowych, aby umożliwić skalowanie w życie. Na szczęście wprowadzenie technologii wirtualizacji (jak [Hyper-V)](/virtualization/hyper-v-on-windows/about/)z maszynami wirtualnymi (VM) dało początek infrastrukturze jako usłudze (IaaS). Zwirtualizowana infrastruktura umożliwiła operacjom skonfigurowanie standardowego zestawu serwerów jako szkieletu, co doprowadziło do elastycznego środowiska zdolnego do inicjowania obsługi administracyjnej unikatowych serwerów "na żądanie". Co ważniejsze, wirtualizacja ustawić scenę za pomocą chmury, aby zapewnić maszyny wirtualne "jako usługa." Firmy mogą łatwo wydostać się z biznesu martwiąc się o nadmiarowe zasilanie lub maszyny fizyczne. Zamiast tego skupili się na środowisku wirtualnym.

IaaS nadal wymaga dużego obciążenia, ponieważ operacje są nadal odpowiedzialne za różne zadania. Zadania te obejmują:

- Łatanie i tworzenie kopii zapasowych serwerów.
- Instalowanie pakietów.
- Aktualizowanie systemu operacyjnego.
- Monitorowanie aplikacji.

Kolejna ewolucja zmniejszyła obciążenie, udostępniając platformę jako usługę (PaaS). Dzięki paas dostawca chmury obsługuje systemy operacyjne, poprawki zabezpieczeń, a nawet wymagane pakiety do obsługi określonej platformy. Zamiast tworzenia maszyny Wirtualnej, a następnie konfigurowania .NET Framework i stojąc serwery Internetowych Usług Informacyjnych (IIS), deweloperzy po prostu wybrać "miejsce docelowe platformy", takich jak "aplikacja sieci web" lub "punkt końcowy interfejsu API" i wdrożyć kod bezpośrednio. Pytania dotyczące infrastruktury są ograniczone do:

- Jakie usługi rozmiaru są potrzebne?
- Jak usługi skalować w sposób skalowany w sposób skalowany w czasie (dodać więcej serwerów lub węzłów)?
- Jak usługi skalują się (zwiększają pojemność serwerów hostingowych lub węzłów)?

Bezserwerowe dalsze abstrakcje serwerów, koncentrując się na kod oparty na zdarzeniach. Zamiast platformy deweloperzy mogą skupić się na mikrousługi, która robi jedną rzecz. Dwa kluczowe pytania dotyczące tworzenia kodu bezserwerowego to:

- Co wyzwala kod?
- Do czego działa kod?

W wersji bez serwerowej infrastruktura jest abstrakcja. W niektórych przypadkach deweloper nie martwi się już o hosta w ogóle. Niezależnie od tego, czy wystąpienie usług IIS, Kestrel, Apache lub innego serwera sieci web jest uruchomione w celu zarządzania żądaniami sieci Web, deweloper koncentruje się na wyzwalaczu HTTP. Wyzwalacz zapewnia standardowy, międzyplatformowy ładunek dla żądania. Ładunek nie tylko upraszcza proces tworzenia, ale ułatwia testowanie, a w niektórych przypadkach sprawia, że kod jest łatwo przenośny na różnych platformach.

Inną cechą bezserwerowych jest mikro-rozliczeń. Często aplikacje sieci web hostują punkty końcowe interfejsu API sieci Web. W tradycyjnych implementacjach gołego metalu, IaaS, a nawet PaaS, zasoby do hostowania interfejsów API są opłacane w sposób ciągły. Oznacza to, że płacisz za hosta punktów końcowych, nawet jeśli nie są one dostępne. Często znajdziesz jeden interfejs API jest nazywany więcej niż inne, więc cały system jest skalowany w oparciu o obsługę popularnych punktów końcowych. Bezserwerowe umożliwia skalowanie każdego punktu końcowego niezależnie i płacić za użycie, więc nie są ponoszone żadne koszty, gdy interfejsy API nie są wywoływane. Migracja może w wielu okolicznościach znacznie zmniejszyć bieżące koszty obsługi punktów końcowych.

## <a name="what-this-guide-doesnt-cover"></a>Co ten przewodnik nie obejmuje

W tym przewodniku szczegółowo podkreślono podejścia do architektury i wzorce projektowe i nie jest dogłębne zagłębienie się w szczegóły implementacji funkcji Azure, [aplikacji logiki](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)lub innych platform bezserwerowych. Ten przewodnik nie obejmuje na przykład zaawansowanych przepływów pracy z aplikacjami logiki lub funkcji funkcji platformy Azure, takich jak konfigurowanie udostępniania zasobów między źródłami (CORS), stosowanie domen niestandardowych lub przekazywanie certyfikatów SSL. Te szczegóły są dostępne w [dokumentacji usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-reference)w trybie online.

### <a name="additional-resources"></a>Zasoby dodatkowe

- [Centrum architektury platformy Azure](https://docs.microsoft.com/azure/architecture/)
- [Najlepsze rozwiązania dla aplikacji w chmurze](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kto powinien skorzystać z przewodnika

Ten przewodnik został napisany dla deweloperów i architektów rozwiązań, którzy chcą tworzyć aplikacje dla przedsiębiorstw za pomocą platformy .NET, które mogą używać składników bezserwerowych lokalnie lub w chmurze. Jest to przydatne dla deweloperów, architektów i decydentów technicznych zainteresowanych:

- Zrozumienie zalet i wad rozwoju bezserwerowego
- Uczenie się, jak podejść do architektury bezserwerowej
- Przykładowe implementacje aplikacji bezserwerowych

## <a name="how-to-use-the-guide"></a>Jak korzystać z przewodnika

Pierwsza część tego przewodnika sprawdza, dlaczego bezserwerowe jest realną opcją, porównując kilka różnych metod architektury. Bada zarówno cykl życia technologii, jak i rozwoju, ponieważ wszystkie aspekty rozwoju oprogramowania mają wpływ na decyzje dotyczące architektury. Przewodnik następnie sprawdza przypadki użycia i wzorce projektu i zawiera implementacje odwołań przy użyciu funkcji azure. Każda sekcja zawiera dodatkowe zasoby, aby dowiedzieć się więcej o danym obszarze. Przewodnik kończy się zasobami na instruktaże i praktyczne badanie implementacji bezserwerowej.

## <a name="send-your-feedback"></a>Wyślij swoją opinię

Przewodnik i powiązane próbki stale ewoluują, więc Twoja opinia jest mile widziana! Jeśli masz uwagi dotyczące tego, jak można poprawić ten przewodnik, skorzystaj z sekcji opinii u dołu dowolnej strony zbudowanej na [problemach z githubem](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Dalej](architecture-approaches.md)
