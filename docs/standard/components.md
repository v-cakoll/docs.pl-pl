---
title: Składniki architektury .NET
description: Opisuje składniki architektury .NET, takie jak .NET Standard, implementacje platformy .NET, środowiska uruchomieniowe platformy .NET i narzędzia.
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: baeb091f7c1757e62ba049afc7a92ae8e73d3925
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70014945"
---
# <a name="net-architectural-components"></a>Składniki architektury .NET

Aplikacja platformy .NET jest opracowana dla i działa w co najmniej jednej *implementacji platformy .NET*.  Implementacje programu .NET obejmują .NET Framework, .NET Core i mono. Istnieje Specyfikacja interfejsu API wspólna dla wszystkich implementacji platformy .NET, która nazywa się .NET Standard. Ten artykuł zawiera krótkie wprowadzenie do każdego z tych koncepcji.

## <a name="net-standard"></a>.NET Standard

.NET Standard to zestaw interfejsów API, które są implementowane przez podstawową bibliotekę klas implementacji platformy .NET. Bardziej formalnie jest to specyfikacja interfejsów API platformy .NET, które składają się na jednolity zestaw kontraktów, dla których kompilujesz swój kod. Te kontrakty są implementowane w każdej implementacji platformy .NET. Pozwala to na przenośność różnych implementacji platformy .NET, co skutecznie pozwala na uruchamianie kodu wszędzie.

.NET Standard jest również platformą [](glossary.md#target-framework)docelową. Jeśli kod jest przeznaczony dla wersji .NET Standard, można go uruchomić w dowolnej implementacji platformy .NET, która obsługuje tę wersję .NET Standard.

Aby dowiedzieć się więcej na temat .NET Standard i sposobu ich określania jako docelowej, zobacz temat [.NET Standard](net-standard.md) .

## <a name="net-implementations"></a>Implementacje platformy .NET

Każda implementacja platformy .NET obejmuje następujące składniki:

- Co najmniej jedno środowisko uruchomieniowe. Przykłady: Środowisko CLR dla .NET Framework, CoreCLR i CoreRT dla platformy .NET Core.
- Biblioteka klas, która implementuje .NET Standard i może implementować dodatkowe interfejsy API. Przykłady: .NET Framework podstawowa Biblioteka klas, podstawowa Biblioteka klas .NET Core.
- Opcjonalnie co najmniej jedna struktura aplikacji. Przykłady: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md)i [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) są zawarte w .NET Framework i .NET Core.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Istnieją cztery podstawowe implementacje platformy .NET, które firma Microsoft aktywnie opracowuje i utrzymuje: .NET Core, .NET Framework, mono i platformy UWP.

### <a name="net-core"></a>.NET Core

.NET Core to wieloplatformowa implementacja programu .NET i zaprojektowana pod kątem obsługi obciążeń serwera i chmury na dużą skalę. Działa w systemach Windows, macOS i Linux. Implementuje .NET Standard, więc kod, który jest przeznaczony dla .NET Standard można uruchomić na platformie .NET Core. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](../framework/winforms/windows-forms-overview.md)i [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) działają na platformie .NET Core.

Aby dowiedzieć się więcej na temat platformy .NET Core, zobacz [Przewodnik po programie .NET Core](../core/index.md) i [wybór między platformą .net core i .NET Framework dla aplikacji serwerowych](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

The.NET Framework to oryginalna implementacja platformy .NET, która istniała od 2002. Jest to ten sam .NET Framework, które są zawsze używane przez istniejących deweloperów platformy .NET. Wersje 4,5 i nowsze implementują .NET Standard, więc kod, który jest przeznaczony dla .NET Standard można uruchomić w tych wersjach .NET Framework. Zawiera dodatkowe interfejsy API specyficzne dla systemu Windows, takie jak interfejsy API dla deweloperów aplikacji klasycznych systemu Windows z Windows Forms i WPF. .NET Framework jest zoptymalizowany do tworzenia aplikacji klasycznych systemu Windows.

Aby dowiedzieć się więcej na temat .NET Framework, zapoznaj się z [przewodnikiem .NET Framework](../framework/index.md).

### <a name="mono"></a>Mono

Mono to implementacja platformy .NET, która jest używana głównie w przypadku, gdy wymagane jest małe środowisko uruchomieniowe. Jest to środowisko uruchomieniowe, które umożliwia aplikacjom platformy Xamarin w systemach Android, Mac, iOS, systemu tvOS i systemu watchOS i jest skoncentrowane głównie na małym rozmiarze. Program mono umożliwia również obsługę gier utworzonych przy użyciu aparatu Unity.

Obsługuje ona wszystkie aktualnie opublikowane wersje .NET Standard.

W przeszłości, mono zaimplementowano większy interfejs API .NET Framework i emuluje niektóre z najpopularniejszych możliwości w systemie UNIX. Jest on czasami używany do uruchamiania aplikacji .NET, które są zależne od tych funkcji w systemie UNIX.

Mono jest zazwyczaj używany z kompilatorem just-in-Time, ale również zawiera pełny statyczny kompilator (kompilacja przed czasem), która jest używana na platformach takich jak iOS.

Aby dowiedzieć się więcej o programie mono, zobacz [dokumentację narzędzia mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Platforma uniwersalna systemu Windows (UWP)

PLATFORMY UWP to implementacja platformy .NET, która jest używana do tworzenia nowoczesnych aplikacji i oprogramowania systemu Windows z obsługą dotykową dla Internet rzeczy (IoT). Ma ona na celu ujednolicenie różnych typów urządzeń, które mogą być ukierunkowane, w tym komputerów, tabletów, phablets, telefonów, a nawet z konsoli Xbox. Usługa platformy UWP udostępnia wiele usług, takich jak scentralizowany magazyn aplikacji, środowisko wykonawcze i zestaw interfejsów API systemu Windows, które mają być używane zamiast Win32 (WinRT). Aplikacje mogą być zapisywane w C++, C#, VB.NET i JavaScript. W przypadku C# używania i VB.NET interfejsy API platformy .NET są udostępniane przez platformę .NET Core.

Aby dowiedzieć się więcej na temat platformy UWP, zobacz [wprowadzenie do platforma uniwersalna systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Środowiska uruchomieniowe platformy .NET

Środowisko uruchomieniowe jest środowiskiem wykonywania programu zarządzanego. System operacyjny jest częścią środowiska uruchomieniowego, ale nie należy do środowiska uruchomieniowego .NET. Poniżej przedstawiono kilka przykładów środowiska uruchomieniowego platformy .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR) dla .NET Framework
- Podstawowe środowisko uruchomieniowe języka wspólnego (CoreCLR) dla platformy .NET Core
- .NET Native platforma uniwersalna systemu Windows 
- Środowisko uruchomieniowe mono dla platformy Xamarin. iOS, Xamarin. Android, Xamarin. Mac i programu mono Desktop

## <a name="net-tooling-and-common-infrastructure"></a>Narzędzia .NET i wspólna infrastruktura

Masz dostęp do obszernego zestawu narzędzi i składników infrastruktury, które współpracują z każdą implementacją platformy .NET. Należą do nich, ale nie są ograniczone do następujących:

- Języki .NET i ich kompilatory
- System projektu .NET (oparty na plikach *. csproj*, *. vbproj*i *. fsproj* )
- [MSBuild](/visualstudio/msbuild/msbuild), aparat kompilacji używany do kompilowania projektów
- Pakiet [NuGet](/nuget/), Menedżer pakietów firmy Microsoft dla platformy .NET
- Narzędzia aranżacji kompilacji typu open source, takie jak [ciastka](https://cakebuild.net/) i [fałszywe](https://fake.build/)

## <a name="see-also"></a>Zobacz także

- [Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [Przewodnik platformy .NET Core](../core/index.md)
- [.NET framework — przewodnik](../framework/index.md)
- [Przewodnik dla języka C#](../csharp/index.md)
- [Podręcznik języka F#](../fsharp/index.md)
- [VB.NET Guide](../visual-basic/index.md)
