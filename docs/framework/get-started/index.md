---
title: Wprowadzenie do programu .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d241f0f0c10be4a73c7ac55930e5dd24ef0b1e2
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453138"
---
# <a name="get-started-with-the-net-framework"></a>Wprowadzenie do programu .NET Framework

.NET Framework jest środowiskiem uruchomieniowym wykonywania, który zarządza aplikacji środowiska .NET Framework. Obraz zawiera środowisko uruchomieniowe języka wspólnego, które zapewnia zarządzanie pamięcią i innych usługach system oraz rozbudowanej biblioteki klas, która umożliwia programistom wykorzystanie zaawansowanego, niezawodnego kodu dla wszystkich głównych obszarów tworzenia aplikacji.

> [!NOTE] 
> .NET Framework jest dostępna tylko w systemach Windows. Możesz użyć [platformy .NET Core](../../core/index.md) można uruchamiać aplikacje na Windows, MacOS i Linux. 

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>Co to jest .NET Framework?

.NET Framework jest środowiskiem wykonania zarządzanego dla Windows, które oferuje szereg usług, aby jej uruchamiania aplikacji. Składa się z dwóch głównych składników: środowisko uruchomieniowe języka wspólnego (CLR), który jest aparatem wykonywania, który obsługuje uruchamianie aplikacji i biblioteki klas .NET Framework, która zawiera bibliotekę przetestowane, kodu wielokrotnego użytku, które deweloperzy mogą wywoływać ze swoich własnych aplikacji. Następujące usługi, które .NET Framework dostarcza do uruchamiania aplikacji:

- Zarządzanie pamięcią. W wielu językach programowania programiści są odpowiedzialne za przydzielanie i zwalnianie pamięci i obsługę czasów istnienia obiektów. W aplikacjach .NET Framework środowisko CLR udostępnia te usługi w imieniu aplikacji.

- Wspólny system typów. W tradycyjnych językach programowania typy podstawowe są definiowane przez kompilator, co komplikuje współdziałania wielu języków. W .NET Framework typy podstawowe są definiowane przez system typów środowiska .NET Framework i są wspólne dla wszystkich języków, które obsługują program .NET Framework.

- Kompleksowa Biblioteka klas. Zamiast pisać olbrzymich ilości kodu do obsługi typowych operacji programowania niskiego poziomu, programiści używać łatwo dostępnej biblioteki typów i ich członków z biblioteki klas programu .NET Framework.

- Środowiska i technologie programistyczne. Program .NET Framework zawiera biblioteki dla szczególnych obszarów projektowania aplikacji, takich jak ASP.NET dla aplikacji sieci web, ADO.NET dla dostępu do danych, programu Windows Communication Foundation dla aplikacji zorientowanych na usługi i aplikacje komputerowe Windows Presentation Foundation for Windows.

- Współdziałanie języków. Kompilatory języka, które obsługują program .NET Framework emitują kod pośredni o nazwie Wspólny język pośredni (CIL), który z kolei jest kompilowany w czasie wykonywania przez środowisko uruchomieniowe języka wspólnego. Dzięki tej funkcji procedury napisane w jednym języku są dostępne dla innych języków, a zespół programistów na temat tworzenia aplikacji w ich własnych językach preferowany.

- Zgodność wersji. W wyjątkowych przypadkach aplikacje utworzone przy użyciu określonej wersji programu .NET Framework uruchomić bez modyfikacji w nowszej wersji.

- Wykonanie Side-by-side. Program .NET Framework pomaga rozwiązywać konflikty wersji poprzez umożliwienie wielu wersjom środowiska uruchomieniowego języka wspólnego współistnienie na tym samym komputerze. Oznacza to, że wiele wersji aplikacji mogą współistnieć, i że aplikację można uruchomić w wersji programu .NET Framework, z którą została skompilowana. Wykonanie Side-by-side odnosi się do grup w wersji .NET Framework 1.0/1.1, 2.0/3.0/3.5 i 4/4.5.x/4.6.x/4.7.x.

- Wielowersyjności kodu w programie. Dzięki systemowi [.NET Standard](~/docs/standard/net-standard.md), deweloperom tworzenie bibliotek klas, które działają na wielu platformach .NET Framework obsługiwane przez tę wersję standard. Na przykład bibliotek przeznaczonych dla platformy .NET Standard 2.0 może służyć przez aplikacje, których platformą docelową jest program .NET Framework 4.6.1, .NET Core 2.0 i platformy uniwersalnej systemu Windows 10.0.16299. 

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>.NET Framework dla użytkowników

Jeśli nie tworzysz aplikacji .NET Framework, ale można ich użyć, możesz nie muszą mieć określone wiedzę na temat programu .NET Framework lub jego funkcjonowania. W większości przypadków .NET Framework jest całkowicie niewidoczne dla użytkowników.

Jeśli używasz systemu operacyjnego Windows .NET Framework może być już zainstalowane na tym komputerze. Ponadto po zainstalowaniu aplikacji, która wymaga programu .NET Framework, program instalacyjny aplikacji może zainstalować określoną wersję programu .NET Framework na komputerze. W niektórych przypadkach może wyświetlić okno dialogowe z prośbą o zainstalowanie programu .NET Framework. Jeśli właśnie próbowano uruchomić aplikację, gdy pojawi się okno dialogowe, a komputer ma dostęp do Internetu, możesz przejść do strony sieci Web, która pozwala zainstalować brakującą wersję programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji](../install/index.md).

Ogólnie rzecz biorąc nie należy odinstalować wersji programu .NET Framework, które są zainstalowane na tym komputerze. Istnieją dwa powody takiego:

- Jeśli aplikacji, którego używasz, zależy od określonej wersji programu .NET Framework, ta aplikacja może spowodować przerwanie usunięcie tej wersji.

- Niektóre wersje programu .NET Framework są aktualizacje w miejscu do wcześniejszych wersji. Na przykład [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] stanowi aktualizację w miejscu do wersji 2.0 i .NET Framework 4.7.2 stanowi aktualizację w miejscu do wersji 4 do 4.7.1. Aby uzyskać więcej informacji, zobacz [wersje programu .NET Framework i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md).

Na wersje Windows wcześniejsze niż Windows 8, jeśli zdecydujesz się usunąć programu .NET Framework, zawsze używaj **programy i funkcje** z poziomu Panelu sterowania, aby go odinstalować. Nigdy nie ręcznie usuń wersję programu .NET Framework. W systemie Windows 8 lub nowszym programu .NET Framework jest składnikiem systemu operacyjnego i nie można odinstalować niezależnie.

Należy pamiętać, że wiele wersji .NET Framework mogą współistnieć na jednym komputerze w tym samym czasie. Oznacza to, że nie trzeba odinstalowywać poprzednich wersji, aby można było zainstalować nowszą wersję.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>.NET Framework dla deweloperów

Jeśli jesteś deweloperem aplikacji, należy wybrać dowolny język programowania, który obsługuje program .NET Framework do tworzenia aplikacji. Ponieważ programu .NET Framework zapewnia niezależność języka i interoperacyjność, możesz korzystać z innych aplikacji .NET Framework i składniki, niezależnie od języka, za pomocą którego zostały opracowane.

Tworzenie aplikacji .NET Framework lub składniki, wykonaj następujące czynności:

1. Jeśli nie jest preinstalowany w systemie operacyjnym, należy zainstalować wersję programu .NET Framework, przeznaczony dla twojej aplikacji. Najnowsza wersja produkcyjna jest .NET Framework 4.7.2. Jest preinstalowany w systemie Windows 10 kwietnia 2018 Update i Windows 10 października 2018 r. Zaktualizuj i jest dostępna do pobrania we wcześniejszych wersjach systemu operacyjnego Windows. Aby uzyskać wymagania systemowe programu .NET Framework, zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md). Aby uzyskać informacje na temat instalowania innych wersji systemu .NET Framework, zobacz [Przewodnik instalacji](../../../docs/framework/install/guide-for-developers.md). Dodatkowe pakiety .NET Framework są wydawane poza pasmem, która oznacza, że ich wydaniu w sposób ciągły poza wszelkie regularnie lub według harmonogramu cyklu. Aby uzyskać informacje o tych paloetach, zobacz [.NET Framework i wersji Out-of-Band](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).

2. Wybierz język lub języki obsługiwane przez .NET Framework, która ma być używany do tworzenia aplikacji. Dostępnych jest kilka języków, w tym [języka Visual Basic](../../visual-basic/index.md), [C#](../../csharp/index.md), [F #](../../fsharp/index.md)i C + +/ interfejsu wiersza polecenia platformy firmy Microsoft. (Język programowania, który pozwala na opracowywanie aplikacji dla programu .NET Framework działa zgodnie z [specyfikacja Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkId=199862).)

3. Wybierz i zainstaluj rozwoju środowisko służące do tworzenia aplikacji, które obsługuje z wybranego języka programowania lub języków. Microsoft zintegrowane środowisko programistyczne (IDE) dla aplikacji .NET Framework jest [programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Jest ona dostępna w wielu wersjach.

Aby uzyskać więcej informacji na temat tworzenia aplikacji przeznaczonych dla platformy .NET Framework, zobacz [Podręcznik programowania](../../../docs/framework/development-guide.md).

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| ----- |------------ |
| [Omówienie](../../../docs/framework/get-started/overview.md) | Zawiera szczegółowe informacje dla deweloperów, którzy tworzenia aplikacji pod kątem programu .NET Framework. |
| [Przewodnik instalacji](../../../docs/framework/install/index.md) | Zawiera informacje dotyczące instalowania programu .NET Framework. |  
| [Program .NET Framework i wydania poza harmonogramem (OOB)](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md) | W tym artykule opisano .NET Framework poza harmonogramem i sposobu ich używania w Twojej aplikacji. |
| [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) | Wyświetla listę wymagań sprzętowych i programowych do uruchamiania programu .NET Framework. |
| [Oprogramowanie .NET Core i Open-Source](../../../docs/framework/get-started/net-core-and-open-source.md) | W tym artykule opisano platformy .NET Core w odniesieniu do programu .NET Framework i jak dostęp do projektów .NET Core typu open source. |
| [Dokumentacja platformy .NET core](https://docs.microsoft.com/dotnet/) | Udostępnia koncepcyjnej i dokumentacja interfejsu API dla platformy .NET Core. |
| [.NET Standard](~/docs/standard/net-standard.md) | W tym artykule omówiono .NET Standard, numerów wersji specyfikacji, obsługujące poszczególnych implementacji platformy .NET w celu zagwarantowania, że spójny zestaw interfejsów API są dostępne na wielu platformach.

## <a name="see-also"></a>Zobacz także

- [.NET framework — przewodnik](../../../docs/framework/index.md)   
- [Co nowego](../../../docs/framework/whats-new/index.md)   
- [Przeglądarka interfejsu API .NET](/dotnet/api/)   
- [Podręcznik programowania](../../../docs/framework/development-guide.md)
