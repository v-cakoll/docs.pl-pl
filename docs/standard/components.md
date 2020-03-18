---
title: Składniki architektury .NET
description: Zawiera opis składników architektury .NET, takich jak .NET Standard, implementacje .NET, elementy wykonawcze .NET i narzędzia.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: eadcf05069edfa32a52c5e73045b4cebd1a9a6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400478"
---
# <a name="net-architectural-components"></a>Składniki architektury .NET

Aplikacja .NET jest opracowywana dla i działa w jednej lub kilku *implementacjach .NET*.  Implementacje .NET obejmują .NET Framework, .NET Core i Mono. Istnieje specyfikacja interfejsu API wspólne dla wszystkich implementacji .NET, który jest nazywany .NET Standard. W tym artykule przedstawiono krótkie wprowadzenie do każdego z tych pojęć.

## <a name="net-standard"></a>.NET Standard

Standard .NET to zestaw interfejsów API, które są implementowane przez bibliotekę klas podstawowych implementacji .NET. Bardziej formalnie jest to specyfikacja interfejsów API .NET, które tworzą jednolity zestaw umów, które są kompilowane kodu przeciwko. Te kontrakty są implementowane w każdej implementacji .NET. Umożliwia to przenoszenie w różnych implementacjach platformy .NET, co skutecznie pozwala na uruchomienie kodu wszędzie.

Standard .NET jest również [platformą docelową](glossary.md#target-framework). Jeśli kod jest przeznaczony dla wersji standardu .NET, można go uruchomić na dowolnej implementacji .NET, która obsługuje tę wersję .NET Standard.

Aby dowiedzieć się więcej o standardzie .NET i sposobie kierowania na niego, zobacz temat [Standard .NET.](net-standard.md)

## <a name="net-implementations"></a>Implementacje .NET

Każda implementacja programu .NET zawiera następujące składniki:

- Co najmniej jeden bieg. Przykłady: CLR dla .NET Framework, CoreCLR i CoreRT dla .NET Core.
- Biblioteka klas, która implementuje standard .NET i może implementować dodatkowe interfejsy API. Przykłady: Biblioteka klas podstawowych .NET Framework, biblioteka podstawowych klas .NET Core.
- Opcjonalnie co najmniej jedna struktura aplikacji. Przykłady: [ASP.NET,](https://www.asp.net/) [Formularze systemu Windows](../framework/winforms/windows-forms-overview.md)i [Program Windows Presentation Foundation (WPF)](../framework/wpf/index.md) są zawarte w .NET Framework i .NET Core.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Istnieją cztery podstawowe implementacje .NET, które firma Microsoft aktywnie opracowuje i utrzymuje: .NET Core, .NET Framework, Mono i UWP.

### <a name="net-core"></a>.NET Core

.NET Core to wieloplatformowa implementacja platformy .NET przeznaczona do obsługi obciążeń serwerowych i w chmurze na dużą skalę. Działa na Windows, macOS i Linux. Implementuje .NET Standard, więc kod, który jest przeznaczony dla standardu .NET można uruchomić na .NET Core. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](../framework/winforms/windows-forms-overview.md)i Windows Presentation [Foundation (WPF)](../framework/wpf/index.md) działają na .NET Core.

Aby dowiedzieć się więcej o platformie .NET Core, zobacz [przewodnik .NET Core guide](../core/index.md) i wybierając między [.NET Core i .NET Framework dla aplikacji serwera](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

The.NET Framework to oryginalna implementacja .NET, która istnieje od 2002 roku. Jest to ta sama .NET Framework, że istniejący deweloperzy .NET zawsze używane. W wersjach 4.5 i nowszych implementować .NET Standard, więc kod, który jest przeznaczony dla .NET Standard można uruchomić w tych wersjach .NET Framework. Zawiera dodatkowe interfejsy API specyficzne dla systemu Windows, takie jak interfejsy API dla tworzenia pulpitu systemu Windows z formularzami systemu Windows i WPF. Program .NET Framework jest zoptymalizowany do tworzenia aplikacji klasycznych systemu Windows.

Aby dowiedzieć się więcej o platformie .NET Framework, zobacz [przewodnik .NET Framework](../framework/index.md).

### <a name="mono"></a>Mono

Mono jest implementacją .NET, która jest używana głównie wtedy, gdy wymagane jest małe uruchomienie. Jest to środowisko wykonawcze, które zasila aplikacje Xamarin na Androida, macOS, iOS, tvOS i watchOS i koncentruje się przede wszystkim na niewielkim rozmiarze. Mono zasila również gry zbudowane przy użyciu silnika Unity.

Obsługuje wszystkie aktualnie opublikowane wersje .NET Standard.

W przeszłości mono implementowane większy interfejs API .NET Framework i emulował niektóre z najbardziej popularnych funkcji na Unix. Czasami jest używany do uruchamiania aplikacji .NET, które opierają się na tych możliwości ach w uniksie.

Mono jest zwykle używany z kompilatorem just-in-time, ale zawiera również pełny kompilator statyczny (kompilacja z wyprzedzeniem), który jest używany na platformach takich jak iOS.

Aby dowiedzieć się więcej o mono, zobacz [dokumentację Mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Platforma uniwersalna systemu Windows (UWP)

Platforma uwp to implementacja .NET, która jest używana do tworzenia nowoczesnych aplikacji i oprogramowania systemu Windows z obsługą dotyku dla Internetu rzeczy (IoT). Został zaprojektowany w celu uniewinnienia różnych typów urządzeń, na które chcesz kierować reklamy, w tym komputerów, tabletów, phabletów, telefonów, a nawet konsoli Xbox. Platforma UWP udostępnia wiele usług, takich jak scentralizowany sklep z aplikacjami, środowisko wykonywania (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT). Aplikacje można zapisywać w językach C++, C#, Visual Basic i JavaScript. Korzystając z języka C# i Języka Visual Basic, interfejsy API .NET są dostarczane przez .NET Core.

Aby dowiedzieć się więcej o programie Uniwersalnej usługi Uniwersalnej [platformy Windows, zobacz Wprowadzenie do platformy uniwersalnej systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Czas wykonywania .NET

Środowisko wykonawcze jest środowiskiem wykonawczym dla programu zarządzanego. Środowisko operacyjne jest częścią środowiska środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET. Oto kilka przykładów uruchomień programu .NET:

- Czas wykonywania języka wspólnego (CLR) dla platformy .NET Framework
- Core Common Language Runtime (CoreCLR) dla programu .NET Core
- Natywna platforma .NET dla uniwersalnej platformy Windows
- Środowisko uruchomieniowe Mono dla platformy Xamarin.iOS, Xamarin.Android, Xamarin.Mac i platformy pulpitu Mono

## <a name="net-tooling-and-common-infrastructure"></a>Oprzyrządowanie .NET i wspólna infrastruktura

Masz dostęp do obszernego zestawu narzędzi i składników infrastruktury, które współpracują z każdą implementacją .NET. Należą do nich, ale nie są ograniczone do następujących:

- Języki .NET i ich kompilatory
- System projektów .NET (oparty na plikach *.csproj*, *.vbproj*i *.fsproj)*
- [MSBuild](/visualstudio/msbuild/msbuild), aparat kompilacji używany do tworzenia projektów
- [NuGet](/nuget/), menedżer pakietów firmy Microsoft dla .NET
- Narzędzia aranżacji kompilacji typu open source, takie jak [CAKE](https://cakebuild.net/) i [FAKE](https://fake.build/)

## <a name="applicable-standards"></a>Obowiązujące normy

Specyfikacje języka C# i wspólnej infrastruktury językowej (CLI) są standaryzowane za pośrednictwem [ecma international®](https://www.ecma-international.org/). Pierwsze wydania tych norm zostały opublikowane przez Ecma w grudniu 2001 r.

Kolejne zmiany standardów zostały opracowane przez grupy zadaniowe TC49-TG2 (C#) i TC49-TG3 (CLI) w ramach Komitetu Technicznego Języków Programowania[(TC49)](https://www.ecma-international.org/memento/tc49.htm)i przyjęte przez Zgromadzenie Ogólne Ecma, a następnie przez ISO/IEC JTC 1 w ramach procesu iso fast-track.

### <a name="latest-standards"></a>Najnowsze standardy

Następujące oficjalne dokumenty Ecma są dostępne dla [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) i [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)):

- **Standard językowy Języka C# (wersja 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Wspólna infrastruktura językowa**: Jest dostępna w formie [pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) i [zip.](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip)
- **Informacje pochodzące z pliku XML partycji IV:** Jest on dostępny w formatach [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) i [zip.](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip)

Oficjalne dokumenty ISO/IEC są dostępne na stronie ISO/IEC [Publicly Available Standards.](https://standards.iso.org/ittf/PubliclyAvailableStandards/) Linki te pochodzą bezpośrednio z tej strony:

- **Technologia informacyjna - Języki programowania - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Technologia informacyjna — Partycje common language infrastructure (CLI) Od I do VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Technologia informacyjna — Wspólna infrastruktura językowa (CLI) — Raport techniczny dotyczący informacji pochodzących z pliku XML partycji IV:** [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Zobacz też

- [Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [Przewodnik po rdzeniu .NET](../core/index.md)
- [.NET framework — przewodnik](../framework/index.md)
- [Przewodnik po języku C#](../csharp/index.yml)
- [Przewodnik Po f#](../fsharp/index.yml)
- [Przewodnik po Visual Basic](../visual-basic/index.yml)
