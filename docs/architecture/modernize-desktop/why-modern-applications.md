---
title: Dlaczego warto korzystać z nowoczesnych aplikacji klasycznych
description: Zapoznaj się z technologiami klasycznymi, takimi jak Windows Forms, WPF i platformy UWP w nowoczesnym świecie.
ms.date: 09/16/2019
ms.openlocfilehash: f8b70ba9e0ee97a6e0938e3219ecd0d2324248ae
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423279"
---
# <a name="why-modern-desktop-applications"></a>Dlaczego warto korzystać z nowoczesnych aplikacji klasycznych

## <a name="introduction"></a>Wprowadzenie

### <a name="a-story-of-one-company"></a>Historia jednej firmy

Z powrotem na wczesnych wersjach 2000, jedna wielonarodowy firma rozpoczęła Tworzenie rozwiązania pulpitu rozproszonego w celu wymiany informacji między różnymi gałęziami firmy i wykonywania zoptymalizowanych operacji na scentralizowanych jednostkach. Wybrano dla nich strukturę nowej marki o nazwie Windows Forms (znana także jako WinForms). W ciągu lat projekt został rozdzielony do dojrzałych, dobrze przetestowanych i sprawdzonych aplikacji z setkami tysięcy wierszy kodu. Czas zakończony i .NET Framework 2,0 nie jest już gorącą nową technologią. Deweloperzy, którzy pracują nad tą aplikacją, mają dylematem. Chcą korzystać z najnowszego stosu technologii w ich rozwoju, a ich aplikacja wygląda i "działa" Modern. W tym samym czasie nie chcemy wyrzucać doskonałego produktu, który miał ponad 15 lat, i napisać całą aplikację od podstaw.

### <a name="your-story"></a>Twoja historia

Użytkownik może znaleźć się w tej samej łodzi, w której znajdują się aplikacje dla dorosłych Windows Forms lub Windows Presentation Foundation (WPF), które wykazały swoją niezawodność w latach. Prawdopodobnie chcesz nadal korzystać z tych aplikacji przez wiele lat. W tym samym czasie, ponieważ te aplikacje zostały zapisane jakiś czas temu, mogą nie mieć takich funkcji, jak nowoczesny wygląd, wydajność, integracja z nowymi urządzeniami i funkcjami platformy, i tak dalej, co daje im wrażenie "stara Tech". Istnieje inny problem, który może zainteresować Cię jako deweloper. Podczas pracy nad starszymi wersjami .NET Framework i obsługą aplikacji, które zostały przez Ciebie zapisaniu, może się zdarzyć, że nie uczysz się nowych technologii i nie masz ich w tworzeniu nowoczesnych umiejętności technicznych. Jeśli jest to Twój Scenariusz — ta książka jest dla Ciebie!

## <a name="desktop-applications-nowadays"></a>Aplikacje klasyczne obecnie

Przed zwiększeniem Internetu aplikacje klasyczne były głównym podejściem do kompilowania systemów oprogramowania. Deweloperzy mogą wybrać dowolny język programowania, taki jak COBOL, Pascal, VB6 lub C++. Jednak w przypadku, gdy opracowały małe narzędzia lub złożoną architekturę rozproszoną, były to wszystkie aplikacje klasyczne.

Następnie technologie internetowe zaczęły zdobywać rozwój świata i przetwarzać ponad więcej inżynierów z korzyściami, takimi jak łatwe wdrażanie i uproszczone procesy dystrybucji. Fakt, że po wdrożeniu aplikacji sieci Web w środowisku produkcyjnym wszyscy użytkownicy otrzymali aktualizacje automatyczne, mają ogromny wpływ na elastyczność oprogramowania.

Jednak infrastruktura internetowa, podstawowe protokoły i standardy, takie jak HTTP i HTML, nie zostały zaprojektowane do tworzenia złożonych aplikacji. W rzeczywistości najważniejsze nakłady programistyczne były przeznaczone tylko dla jednego celu: aby umożliwić aplikacjom sieci Web takie same możliwości, jak szybkie wprowadzanie danych i zarządzanie stanami.

Pomimo tego, że aplikacje sieci Web i mobilne są coraz bardziej wydajne, w przypadku niektórych zadań aplikacje klasyczne nadal przechowują liczbę w jednym miejscu pod względem wydajności i wydajności. Wyjaśniamy, dlaczego istnieją miliony deweloperów, którzy tworzą swoje projekty za pomocą WPF i WinForms, a ilość tych aplikacji stale rośnie.

Oto kilka powodów, dla których warto wybrać aplikacje klasyczne:

- Aplikacje klasyczne mają lepszą interakcję z komputerem użytkownika.
- Wydajność aplikacji klasycznych na potrzeby skomplikowanych obliczeń jest znacznie wyższa niż wydajność aplikacji sieci Web.
- Uruchamianie logiki niestandardowej na stronie klienta jest możliwe, ale znacznie trudniejsze w przypadku aplikacji sieci Web.
- Używanie wielowątkowości jest łatwiejsze i wydajniejsze w aplikacji klasycznej.
- Krzywa szkoleniowa do projektowania interfejsów użytkownika (interfejsów użytkownika) nie jest nagięta. I dla WinForms, jest całkowicie intuicyjne dzięki funkcji przeciągania i upuszczania w projektancie Windows Forms.
- Można łatwo rozpocząć kodowanie i testowanie algorytmów bez konieczności konfigurowania infrastruktury serwerów lub zadbać o problemy z łącznością, zapory i zgodność z przeglądarką.
- Debugowanie jest zaawansowane w porównaniu do debugowania sieci Web.
- Dostęp do urządzeń sprzętowych, takich jak aparaty fotograficzne, Bluetooth lub czytniki kart, jest łatwy.
- Ponieważ technologia była przez pewien czas niedostępna, istnieje wielu ekspertów i baza wiedzy dostępna do tworzenia aplikacji klasycznych.

Tak więc, jak widać, Programowanie dla komputerów stacjonarnych jest wspaniałe z wielu powodów. Technologia jest przedwcześnie i przetestowana, cykl programowania jest szybki, a debugowanie jest zaawansowane i raczej, aplikacje klasyczne mają mniej złożoność i ułatwiają rozpoczęcie pracy z programem.

Firma Microsoft oferuje wiele technologii klasycznych interfejsu użytkownika w ciągu lat od Win32 wprowadzonych w 1995 do platforma uniwersalna systemu Windows (platformy UWP), które zostały wydane w 2016.

![Technologie klasyczne firmy Microsoft](./media/why-modern-applications/microsoft-desktop-technologies.png)

Zgodnie z ankietą opublikowaną przez Telerik w kwietniu 2016 najpopularniejsze technologie tworzenia aplikacji klasycznych systemu Windows to Windows Forms, WPF i platformy UWP.

![Ankieta Telerika pokazująca Windows Forms, WPF i platformy UWP jako najpopularniejsze technologie klasyczne](./media/why-modern-applications/telerik-survey.png)

Możesz tworzyć dowolne z nich przy użyciu języka C# i Visual Basic, ale przyjrzyjmy się bliżej.

### <a name="windows-forms"></a>Windows Forms

Pierwszy wydano w 2002, Windows Forms jest platformą zarządzaną, a to najstarsza, najczęściej używana technologia oparta na aparacie interfejsu urządzenia graficznego (GDI) systemu Windows. Oferuje bezproblemowe środowisko przeciągania i upuszczania w celu opracowywania interfejsów użytkownika w programie Visual Studio.  W tym samym czasie Windows Forms korzysta z projektanta programu Visual Studio jako głównego sposobu tworzenia interfejsu użytkownika, więc Tworzenie składników wizualnych na podstawie kodu nie jest proste.

Poniższa lista zawiera podsumowanie głównych cech Windows Forms:

- Dojrzała technologia z wieloma przykładami i dokumentacją kodu.
- Zaawansowany i wydajny Projektant. Nie jest to wygodne do projektowania interfejsu użytkownika "z kodu".
- Łatwe i intuicyjne uczenie się dzięki funkcji przeciągania i upuszczania projektanta.
- Obsługiwane w dowolnej wersji systemu Windows.
- Obsługiwane przez program .NET Core 3,0 i jego nowsze wersje.

### <a name="wpf"></a>WPF

W oparciu o specyfikację języka XAML, WPF preferuje wyraźne rozdzielenie między interfejsem użytkownika i kodem. Język XAML oferuje takie możliwości, jak tworzenia szablonów, style i powiązania, które są odpowiednie do kompilowania dużych aplikacji. Podobnie jak Windows Forms, jest to struktura zarządzana, ale projekt jest modułowy i wielokrotnego użytku.

Oto główne funkcje platformy WPF:

- Dojrzała technologia.
- Projektant jest dostępny, ale deweloperzy zazwyczaj preferują Tworzenie projektu na podstawie kodu przy użyciu deklaratywnego języka XAML.
- Krzywa uczenia jest bardziej intensywna niż Windows Forms.
- Obsługiwane w dowolnej wersji systemu Windows.
- Obsługiwane przez program .NET Core 3,0 i jego nowsze wersje.

### <a name="uwp"></a>UWP

PLATFORMY UWP nie jest tylko platformą prezentacji, taką jak WPF i Windows Forms, ale również sama sama platforma. Ta platforma ma następujące:

- Własny zestaw interfejsów API (interfejs API środowisko wykonawcze systemu Windows).
- Nowy system wdrażania (MSIX)
- Nowoczesny model cyklu życia aplikacji (w przypadku niskiego zużycia baterii).
- Nowy system zarządzania zasobami (oparty na plikach PRI).

Platforma została utworzona w celu obsługi wszystkich rodzajów systemów wejścia (takich jak atrament, Touch, konsola do gier, mysz, klawiatura, urządzenia Gaze itd.) we wszystkich czynnikach z wydajnością i niskim zużyciu baterii. Z tego względu powłoka systemu operacyjnego Windows 10 używa części platformy platformy UWP.

![PLATFORMY UWP, struktura](./media/why-modern-applications/uwp-structure.png)

PLATFORMY UWP zawiera strukturę prezentacji, która jest oparta na języku XAML, podobnie jak WPF, ale ma pewne istotne różnice, takie jak:

- Aplikacje są wykonywane w kontenerach aplikacji. Kontenery aplikacji kontrolują zasoby, do których aplikacja platformy UWP może uzyskać dostęp.
- Obsługiwane tylko w systemie Windows 10.
- Aplikacje można wdrażać za Microsoft Store w celu łatwiejszego wdrażania.
- Zaprojektowana jako część interfejsu API środowisko wykonawcze systemu Windows.
- Zawiera rozbudowany zestaw wbudowanych kontrolek i dodatkowych kontrolek dostępnych za pomocą pakietów NuGet biblioteki interfejsu użytkownika firmy Microsoft (Biblioteka WinUI) aktualizowanych co kilka miesięcy.

## <a name="a-tale-of-two-platforms"></a>Wskaźnik dwóch platform

W ciągu ostatnich 20 lat, podczas gdy technologie pulpitu interfejsu użytkownika zostały rozrastane i są zgodne ze ścieżką Windows Forms do platformy UWP, sprzęt był również rozwijany z dużej ilości komputerów z małymi monitorami CRT do monitorów o wysokiej rozdzielczości DPI oraz lekkich tabletów i telefonów z różnymi technikami wprowadzania danych, takimi jak Touch i atramentem. Te zmiany spowodowały utworzenie dwóch różnych koncepcji: aplikacji klasycznej i nowoczesnej aplikacji. Nowoczesne aplikacje to takie, które uwzględniają różne czynniki formularzy urządzeń, różne metody wejścia i wyjścia oraz wykorzystują nowoczesne funkcje pulpitu podczas działania w modelu wykonywania w trybie piaskownicy. (Tradycyjnie) aplikacja klasyczna, z drugiej strony, to aplikacja, która wymaga stałego interfejsu użytkownika z wysoką gęstością formantów, które najlepiej sprawdzają się za pomocą myszy i klawiatury.

W poniższej tabeli opisano różnice między tymi dwoma koncepcjami:

|   | Aplikacja Modern | Aplikacja klasyczna |
| --- | --- | --- |
| Zabezpieczenia | Zamieszczono &amp; doskonałe podstawy wykonywania. Zaprojektowana od podstaw do poszanowania prywatności użytkowników, zarządzania cyklem życia baterii i skoncentrowania się na zachowaniu bezpieczeństwa urządzenia.  | &amp;Poziom zabezpieczeń administratora użytkownika. Masz natywny dostęp do folderów rejestru i dysków twardych. |
| Wdrożenie | Instalacja i aktualizacje są zarządzane przez platformę.   | Instalator MSI, aktualizacje niestandardowe &amp; . Tradycyjnie Źródło zarządzaniem mu towarzyszą dla deweloperów i menedżerów IT.  |
| Dystrybucja | Podpisane pakiety zaufanej dystrybucji &amp; . Dystrybucja jest przeprowadzana z zaufanego źródła, a nie z sieci Web.  | Sieć Web, program SCCM — &amp; dystrybucja niestandardowa. Brak kontroli nad tym, co jest zainstalowane, wpływa na cały komputer.   |
| Interfejs użytkownika | Nowoczesny interfejs użytkownika. Różne mechanizmy wejściowe, atrament, dotyk, konsola do gier, klawiatura, mysz itp.  | Windows Forms, WPF, MFC. Zaprojektowana dla myszy i klawiatury dla gęstego interfejsu użytkownika i aby uzyskać najbardziej produktywność z pulpitu.  |
| Dane | Pierwsze dane w chmurze — szczegółowe informacje. Źródło prawdy w chmurze. Szczegółowe informacje o tym, co się dzieje z Twoją aplikacją i jak działa.  | Dane lokalne. Tradycyjne aplikacje klasyczne zazwyczaj potrzebują niektórych danych lokalnych.  |
| Projekt | Zaprojektowana do ponownego użycia. Wielokrotne użycie na różnych platformach, frontonie i zapleczu, które są uruchamiane w wielu miejscach, jak to możliwe.  | Przeznaczone tylko dla komputerów stacjonarnych z systemem Windows  |

W ramach zobowiązania, aby zapewnić deweloperom najlepsze narzędzia do kompilowania aplikacji, firma Microsoft może uzyskać bardzo duże wysiłki w celu przeprowadzenia tych koncepcji lub nawet wypowiedzieć platformy, aby zapewnić deweloperom najlepsze rozwiązania. W tym celu firma Microsoft wykonała dwukierunkową pracę między obiema platformami.

![Dwukierunkowe wysiłki między nowoczesnymi aplikacjami aplikacji i klasycznymi](./media/why-modern-applications/bidirectional-effort.png)

1. Przenieś scenariusze aplikacji klasycznych na nowoczesne platformy aplikacji. Tradycyjny rozwój pulpitu jest nadal popularny, ponieważ zawiera on pewne scenariusze. Warto wziąć pod uwagę te typowe scenariusze dla komputerów stacjonarnych i dostosować je do nowoczesnej platformy klasycznej, aby zapewnić pełną obsługę platformy.

    ![Przenoszenie scenariuszy aplikacji klasycznych do nowoczesnej platformy aplikacji](./media/why-modern-applications/desktop-to-modern.png)

1. Przenieś nowoczesne funkcje aplikacji do aplikacji klasycznych. W przypadku istniejących aplikacji klasycznych, które wymagają sposobu korzystania z nowoczesnych możliwości bez konieczności ponownego pisania, funkcje z nowoczesnej platformy aplikacji są wypychane do aplikacji klasycznej.

    ![Przenoszenie nowoczesnych funkcji aplikacji do aplikacji klasycznych](./media/why-modern-applications/modern-to-desktop.png)

W tej książce skupmy się na drugiej części i pokazano, jak można wykonać modernizację istniejących aplikacji klasycznych.

## <a name="paths-to-modernization"></a>Ścieżki do modernizacji

Struktura tego przewodnika odzwierciedla trzy różne osie w celu wykonania modernizacji: nowoczesne funkcje, wdrażanie i instalację.

### <a name="modern-features"></a>Nowoczesne funkcje

Załóżmy, że masz działającą Windows Forms aplikację, której przedstawiciel handlowy korzysta z Twojej firmy, aby wypełnić zamówienie klienta. Nowe wymaganie jest dostępne w celu umożliwienia klientowi podpisania zamówienia przy użyciu pióra tabletu. Pismo odręczne jest natywne w współczesnych systemach operacyjnych i technologiach, ale nie było dostępne podczas opracowania aplikacji.

Ta ścieżka pokazuje, w jaki sposób można korzystać z nowoczesnych funkcji pulpitu w istniejącej aplikacji klasycznej.

### <a name="deployment"></a>Wdrożenie

Nowoczesne cykle programistyczne są podkreślane w celu zapewnienia elastyczności wdrożenia nowych wersji aplikacji dla każdego pojedynczego użytkownika. Ponieważ aplikacje Windows Forms i WPF opierają się na określonej wersji .NET Framework, które muszą znajdować się na komputerze, nie mogą korzystać z nowych funkcji .NET Framework wersji bez interwencji osób IT z ryzykiem związanym z innymi aplikacjami działającymi na tym samym komputerze. Ma ona ograniczoną liczbę innowacji dla deweloperów wymusza ich nieaktualne wersje .NET Framework.

Od momentu uruchomienia programu .NET Core 3,0 można wykorzystać nowe podejście do wdrażania wielu wersji programu .NET Core obok siebie i określić, która wersja platformy .NET Core powinna być docelowa. W ten sposób można użyć najnowszych funkcji w jednej aplikacji, bez obaw, że nie będzie można przerwać żadnych innych aplikacji.

### <a name="installation"></a>Instalacja

Aplikacje klasyczne zawsze polegają na pewnych procesach instalacji, zanim użytkownik będzie mógł ich używać. Ten fakt wprowadza do gry zestaw technologii, od MSI i ClickOnce do niestandardowych instalatorów, a nawet do wdrożenia XCOPY. Każda z tych metod dotyczy bardzo delikatnych problemów, ponieważ aplikacje muszą mieć możliwość dostępu do zasobów udostępnionych na komputerze. Czasami instalacja musi uzyskać dostęp do rejestru, aby wstawić lub zaktualizować nowe wartości klucza, czasami w celu zaktualizowania udostępnionych bibliotek DLL, do których odwołuje się główna aplikacja. Powoduje to ciągły kłopotliwej dla użytkowników, tworząc to postrzeganie, że po zainstalowaniu jakiejś aplikacji komputer nie będzie taki sam, nawet jeśli później zostanie odinstalowany.

W tej książce wprowadzimy nowy sposób instalowania aplikacji z programem MSIX, który rozwiązuje opisany wcześniej problem. Dowiesz się, jak można łatwo skonfigurować pakowanie, instalację i aktualizacje aplikacji.

>[!div class="step-by-step"]
>[Poprzedni](index.md) 
> [Dalej](whats-new-dotnet-core.md)
