---
title: Wprowadzenie do .NET Framework
description: Zacznij korzystać z platformy .NET, czyli środowiska wykonawczego środowiska uruchomieniowego, które zarządza aplikacjami. Zawiera środowisko uruchomieniowe języka wspólnego (CLR) i szeroką bibliotekę klas.
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: b6ad74d2984443a3b8345c2261996e7ab30acdff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621655"
---
# <a name="get-started-with-net-framework"></a>Wprowadzenie do .NET Framework

.NET Framework to środowisko wykonawcze środowiska uruchomieniowego, które zarządza aplikacjami przeznaczonymi .NET Framework. Obejmuje środowisko uruchomieniowe języka wspólnego, które zapewnia zarządzanie pamięcią i inne usługi systemowe oraz szeroką bibliotekę klas, która umożliwia programistom korzystanie z niezawodnego, niezawodnego kodu dla wszystkich głównych obszarów tworzenia aplikacji.

> [!NOTE]
> .NET Framework jest dostępna tylko w systemach Windows. [Platformy .NET Core](../../core/index.yml) można używać do tworzenia i uruchamiania aplikacji w systemach Windows, MacOS i Linux.

## <a name="what-is-net-framework"></a>Co to jest .NET Framework?

.NET Framework to zarządzane środowisko wykonawcze dla systemu Windows, które oferuje różne usługi dla uruchomionych aplikacji. Składa się z dwóch głównych składników: środowiska uruchomieniowego języka wspólnego (CLR), który jest aparatem wykonywania obsługującym aplikacje działające i Biblioteka klas .NET Framework, która udostępnia bibliotekę przetestowanego kodu do wielokrotnego użytku, który deweloperzy mogą wywoływać z własnych aplikacji. Usługi, które .NET Framework zapewniają uruchamianie aplikacji, to m.in.:

- Zarządzanie pamięcią. W wielu językach programowania programiści są odpowiedzialni za przydzielanie i zwalnianie pamięci oraz obsługę okresów istnienia obiektów. W aplikacjach .NET Framework CLR udostępnia te usługi w imieniu aplikacji.

- Wspólny system typów. W tradycyjnych językach programistycznych typy podstawowe są definiowane przez kompilator, co komplikuje współdziałanie między językami. W .NET Framework typy podstawowe są definiowane przez system typu .NET Framework i są wspólne dla wszystkich języków, które są przeznaczone do .NET Framework.

- Obszerna biblioteka klas. Zamiast konieczności pisania ogromnych ilości kodu do obsługi typowych operacji programistycznych niskiego poziomu, programiści wykorzystują łatwo dostępną bibliotekę typów i ich członków z biblioteki klas .NET Framework.

- Platformy i technologie programistyczne. .NET Framework obejmuje biblioteki dla określonych obszarów tworzenia aplikacji, takich jak ASP.NET for Web Apps, ADO.NET do uzyskiwania dostępu do danych, Windows Communication Foundation dla aplikacji zorientowanych na usługę i Windows Presentation Foundation dla aplikacji klasycznych systemu Windows.

- Współdziałanie języków. Kompilatory języka, które są przeznaczone dla .NET Framework emitują kod pośredni o nazwie common pośredniego języka (CIL), które z kolei są kompilowane w czasie wykonywania przez środowisko uruchomieniowe języka wspólnego. Dzięki tej funkcji procedury utworzone w jednym języku są dostępne dla innych języków, a programiści koncentrują się na tworzeniu aplikacji w ich preferowanych językach.

- Zgodność wersji. Z rzadkimi wyjątkami aplikacje opracowywane przy użyciu określonej wersji .NET Framework są uruchamiane bez modyfikacji w nowszej wersji.

- Wykonywanie równoczesne. .NET Framework ułatwia rozwiązywanie konfliktów wersji przez umożliwienie istnienia wielu wersji środowiska uruchomieniowego języka wspólnego na tym samym komputerze. Oznacza to, że wiele wersji aplikacji może współistnieć i że aplikacja może działać w wersji .NET Framework, z którą została skompilowana. Wykonywanie równoczesne dotyczy grup .NET Framework wersji 1.0/1.1, 2.0/3.0/3.5 i 4/4.5. x/4.6. x/4,7. x/4.8.

- Wielowersyjności kodu. Według [.NET Standard](../../standard/net-standard.md), deweloperzy tworzą biblioteki klas, które działają na wielu platformach .NET Framework obsługiwanych przez tę wersję Standard. Na przykład biblioteki, które są przeznaczone dla .NET Standard 2,0 mogą być używane przez aplikacje przeznaczone dla .NET Framework 4.6.1, .NET Core 2,0 i platformy UWP 10.0.16299.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>.NET Framework dla użytkowników

Jeśli nie opracowujesz aplikacji .NET Framework, ale ich używasz, nie musisz mieć konkretnej wiedzy na temat .NET Framework lub jego działania. W większości przypadków platforma jest całkowicie niewidoczna dla użytkowników.

Jeśli używasz systemu operacyjnego Windows, .NET Framework mogą być już zainstalowane na komputerze. Ponadto jeśli zainstalujesz aplikację, która wymaga .NET Framework, program instalacyjny aplikacji może zainstalować określoną wersję platformy na komputerze. W niektórych przypadkach może zostać wyświetlone okno dialogowe z prośbą o zainstalowanie .NET Framework. Jeśli właśnie podjęto próbę uruchomienia aplikacji po wyświetleniu tego okna dialogowego i jeśli komputer ma dostęp do Internetu, możesz przejść do strony sieci Web, która umożliwia zainstalowanie brakującej wersji .NET Framework. Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji](../install/index.md).

Ogólnie rzecz biorąc nie należy odinstalowywać wersji .NET Framework zainstalowanych na komputerze. Istnieją dwa powody takiego działania:

- Jeśli używana aplikacja zależy od określonej wersji .NET Framework, ta aplikacja może zostać przerwana, jeśli ta wersja zostanie usunięta.

- Niektóre wersje .NET Framework są aktualizacjami w miejscu do wcześniejszych wersji. Na przykład .NET Framework 3,5 to aktualizacja w miejscu do wersji 2,0, a .NET Framework 4,8 to aktualizacja w miejscu do wersji 4 za poorednictwem 4.7.2. Aby uzyskać więcej informacji, zobacz [.NET Framework wersje i zależności](../migration-guide/versions-and-dependencies.md).

W wersjach systemu Windows starszych niż Windows 8, jeśli wybierzesz opcję usunięcia .NET Framework, w panelu sterowania zawsze używaj **programów i funkcji** , aby odinstalować je. Nie usuwaj ręcznie wersji .NET Framework. W systemie Windows 8 i nowszych .NET Framework to składnik systemu operacyjnego i nie może zostać odinstalowany niezależnie.

Wiele wersji .NET Framework może współistnieć na jednym komputerze w tym samym czasie. Oznacza to, że nie trzeba odinstalowywać poprzednich wersji, aby można było zainstalować nowszą wersję.

## <a name="net-framework-for-developers"></a>.NET Framework dla deweloperów

Jeśli jesteś deweloperem, wybierz dowolny język programowania, który obsługuje .NET Framework do tworzenia aplikacji. Ponieważ .NET Framework zapewnia niezależność języka i współdziałanie, można korzystać z innych .NET Framework aplikacji i składników niezależnie od języka, w którym zostały opracowane.

Aby opracowywać .NET Framework aplikacje lub składniki, wykonaj następujące czynności:

1. Jeśli nie jest ona wstępnie zainstalowana w systemie operacyjnym, Zainstaluj wersję .NET Framework, do której aplikacja będzie docelowa. Najnowsza wersja produkcyjna to .NET Framework 4,8. Jest ona wstępnie zainstalowana w systemie Windows 10 maja 2019 Update i jest dostępna do pobrania we wcześniejszych wersjach systemu operacyjnego Windows. Aby uzyskać wymagania systemowe .NET Framework, zobacz [wymagania systemowe](system-requirements.md). Aby uzyskać informacje na temat instalowania innych wersji .NET Framework, zobacz [Przewodnik instalacji](../install/guide-for-developers.md). Dodatkowe pakiety .NET Framework są wyłączane poza pasmem, co oznacza, że są one zwalniane na podstawie cyklu regularnego lub zaplanowanych wersji. Aby uzyskać informacje o tych pakietach, zobacz [.NET Framework i wersje poza pasmem](the-net-framework-and-out-of-band-releases.md).

2. Wybierz język lub języki obsługiwane przez wersję .NET Framework, która ma zostać użyta do opracowywania aplikacji. Dostępne są różne języki, w tym [Visual Basic](../../visual-basic/index.yml), [C#](../../csharp/index.yml), [F #](../../fsharp/index.yml)i [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) od firmy Microsoft. (Język programowania, który umożliwia tworzenie aplikacji dla .NET Framework jest zgodny ze [specyfikacją Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)).

3. Wybierz i zainstaluj środowisko programistyczne, które ma być używane do tworzenia aplikacji, które obsługuje wybrany język programowania lub języki. Zintegrowane środowisko programistyczne firmy Microsoft (IDE) dla aplikacji .NET Framework jest [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Jest on dostępny w wielu wersjach.

Aby uzyskać więcej informacji na temat tworzenia aplikacji przeznaczonych do .NET Framework, zobacz [Przewodnik programowania](../development-guide.md).

## <a name="related-articles"></a>Pokrewne artykuły:

| Tytuł | Opis |
| ----- |------------ |
| [Omówienie](overview.md) | Zawiera szczegółowe informacje dla deweloperów, którzy tworzą aplikacje, które są przeznaczone .NET Framework. |
| [Przewodnik instalacji](../install/index.md) | Zawiera informacje o instalowaniu .NET Framework. |  
| [.NET Framework i wersje poza pasmem](the-net-framework-and-out-of-band-releases.md) | Opisuje .NET Framework wersje poza pasmem oraz sposób ich używania w aplikacji. |
| [Wymagania systemowe](system-requirements.md) | Zawiera listę wymagań sprzętowych i programowych dotyczących uruchamiania .NET Framework. |
| [Oprogramowanie .NET Core i Open-Source](net-core-and-open-source.md) | Opisuje platformę .NET Core w odniesieniu do .NET Framework i sposób uzyskiwania dostępu do projektów platformy .NET Core Open Source. |
| [Dokumentacja platformy .NET Core](../../core/index.yml) | Zawiera dokumentację dotyczącą pojęć i interfejsów API dla platformy .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | W tym artykule omówiono .NET Standard, specyfikacje wersji, które są obsługiwane przez poszczególne implementacje platformy .NET, aby zagwarantować, że na wielu platformach jest dostępny spójny zestaw interfejsów API.

## <a name="see-also"></a>Zobacz także

- [.NET framework — przewodnik](../index.yml)
- [Co nowego](../whats-new/index.md)
- [Przeglądarka interfejsów API platformy .NET](../../../api/index.md)
- [Podręcznik programowania](../development-guide.md)
