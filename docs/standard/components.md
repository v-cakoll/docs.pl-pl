---
title: Składniki architektury .NET
description: W tym artykule opisano składniki architektury platformy .NET, takie jak standard .NET, implementacje .NET, środowiska wykonawcze .NET i narzędzia.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 027fdb4cec47550f88f6930a4bbdff4ab5cdfb36
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344167"
---
# <a name="net-architectural-components"></a>Składniki architektury .NET

Aplikacja .NET jest rozwijana i uruchamiana w jednej lub kilku *implementacjach platformy .NET*.  Implementacje platformy .NET obejmują platformę .NET Framework, .NET Core i Mono. Istnieje specyfikacja interfejsu API wspólne dla wszystkich implementacji .NET, który jest nazywany .NET Standard. W tym artykule przedstawiono krótkie wprowadzenie do każdej z tych pojęć.

## <a name="net-standard"></a>.NET Standard

.NET Standard to zestaw interfejsów API, które są implementowane przez bibliotekę klas podstawowych implementacji platformy .NET. Bardziej formalnie jest to specyfikacja interfejsów API platformy .NET, które tworzą jednolity zestaw umów, które kompilujesz kod. Kontrakty te są implementowane w każdej implementacji platformy .NET. Umożliwia to przenośność w różnych implementacjach platformy .NET, skutecznie umożliwiając uruchamianie kodu wszędzie.

.NET Standard jest również [platformą docelową](glossary.md#target-framework). Jeśli kod jest przeznaczony dla wersji programu .NET Standard, można go uruchomić na dowolnej implementacji platformy .NET obsługującej tę wersję programu .NET Standard.

Aby dowiedzieć się więcej o .NET Standard i sposobie kierowania na niego, zobacz [.NET Standard](net-standard.md).

## <a name="net-implementations"></a>Implementacje platformy .NET

Każda implementacja platformy .NET zawiera następujące składniki:

- Co najmniej jeden środowiska uruchomieniowe. Przykłady: CLR dla platformy .NET Framework, CoreCLR i CoreRT dla platformy .NET Core.
- Biblioteka klas, która implementuje standard .NET i może implementować dodatkowe interfejsy API. Przykłady: biblioteka klas podstawowych programu .NET Framework, biblioteka klas podstawowych .NET Core.
- Opcjonalnie co najmniej jedna struktura aplikacji. Przykłady: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md)i Windows Presentation [Foundation (WPF)](../framework/wpf/index.md) są zawarte w programie .NET Framework i .NET Core.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Istnieją cztery podstawowe implementacje platformy .NET, które firma Microsoft aktywnie opracowuje i utrzymuje: .NET Core, .NET Framework, Mono i UWP.

### <a name="net-core"></a>.NET Core

.NET Core to wieloplatformowa implementacja platformy .NET, zaprojektowana do obsługi obciążeń serwerowych i chmurowych na dużą skalę. Działa w systemach Windows, macOS i Linux. Implementuje standard .NET, więc kod, który jest przeznaczony dla standardu .NET można uruchomić na .NET Core. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](../framework/winforms/windows-forms-overview.md)i [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) są uruchamiane na programie .NET Core.

Aby dowiedzieć się więcej o platformie .NET Core, zobacz [Przewodnik po rdzeniu .NET](../core/index.yml) i [wybieranie między programem .NET Core a platformą .NET Framework dla aplikacji serwera](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework to oryginalna implementacja platformy .NET, która istnieje od 2002 roku. Wersje 4.5 i nowsze implementują .NET Standard, więc kod, który jest przeznaczony dla programu .NET Standard, może być uruchamiany w tych wersjach programu .NET Framework. Zawiera dodatkowe interfejsy API specyficzne dla systemu Windows, takie jak interfejsy API dla tworzenia pulpitu systemu Windows z windows forms i WPF. Program .NET Framework jest zoptymalizowany pod kątem tworzenia aplikacji klasycznych systemu Windows.

Aby dowiedzieć się więcej o platformie .NET Framework, zobacz [przewodnik po platformie .NET Framework](../framework/index.yml).

### <a name="mono"></a>Mono

Mono jest implementacją platformy .NET, która jest używana głównie wtedy, gdy wymagane jest małe środowisko uruchomieniowe. Jest to środowisko wykonawcze, które zasila aplikacje platformy Xamarin w systemach Android, macOS, iOS, tvOS i watchOS i koncentruje się przede wszystkim na niewielkim rozmiarze. Mono zasila również gry zbudowane za pomocą silnika Unity.

Obsługuje wszystkie aktualnie opublikowane wersje .NET Standard.

W przeszłości Mono implementował większy interfejs API programu .NET Framework i emulował niektóre z najbardziej popularnych funkcji uniksu. Czasami jest używany do uruchamiania aplikacji platformy .NET, które opierają się na tych możliwościach w uniksie.

Mono jest zwykle używany z kompilatorem just-in-time, ale posiada również kompilator statyczny (kompilacja przed czasem), który jest używany na platformach takich jak iOS.

Aby dowiedzieć się więcej o mono, zobacz [dokumentację mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Platforma uniwersalna systemu Windows (UWP)

Platformy uniwersalnej systemu Windows jest implementacja .NET, który jest używany do tworzenia nowoczesnych, dotykowych aplikacji systemu Windows i oprogramowania do Internetu rzeczy (IoT). Został zaprojektowany w celu ujednolicenia różnych typów urządzeń, na które możesz chcieć kierować reklamy, w tym komputerów, tabletów, telefonów, a nawet konsoli Xbox. Platformy uniwersalnej systemu Windows udostępnia wiele usług, takich jak scentralizowany sklep z aplikacjami, środowisko wykonywania (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT). Aplikacje mogą być zapisywane w językach C++, C#, Visual Basic i JavaScript. Podczas korzystania z języka C# i Visual Basic interfejsy API platformy .NET są dostarczane przez program .NET Core.

Aby dowiedzieć się więcej o platformie uniwersalnej systemu Windows, zobacz [Wprowadzenie do platformy uniwersalnej systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Środowiska wykonawcze platformy .NET

Środowisko wykonawcze jest środowiskiem wykonywania dla programu zarządzanego. System operacyjny jest częścią środowiska wykonawczego, ale nie jest częścią środowiska uruchomieniowego .NET. Oto kilka przykładów środowiska uruchomieniowego platformy .NET:

- Wspólny czas wykonywania języka (CLR) dla programu .NET Framework
- Core Common Language Runtime (CoreCLR) dla .NET Core
- Platforma .NET Native dla platformy systemu Windows
- Środowisko wykonawcze Mono dla platformy Xamarin.iOS, Xamarin.Android, Xamarin.Mac i mono struktury pulpitu

## <a name="net-tooling-and-common-infrastructure"></a>Narzędzia .NET i wspólna infrastruktura

Masz dostęp do obszernego zestawu narzędzi i składników infrastruktury, które działają z każdej implementacji .NET. Te narzędzia i składniki obejmują:

- Języki .NET i ich kompilatory
- System projektu .NET (oparty na plikach *csproj*, *.vbproj*i *.fsproj)*
- [MSBuild](/visualstudio/msbuild/msbuild), aparat kompilacji używany do tworzenia projektów
- [NuGet](/nuget/), menedżer pakietów firmy Microsoft dla platformy .NET
- Narzędzia aranżacji open-source, takie jak [CAKE](https://cakebuild.net/) i [FAKE](https://fake.build/)

## <a name="applicable-standards"></a>Obowiązujące normy

Specyfikacje języka C# i wspólnej infrastruktury językowej (CLI) są standaryzowane za pośrednictwem [programu Ecma International&reg;](https://www.ecma-international.org/). Pierwsze wydania tych standardów zostały opublikowane przez Ecma w grudniu 2001 roku.

Kolejne zmiany norm zostały opracowane przez grupy zadaniowe TC49-TG2 (C#) i TC49-TG3 (CLI) w ramach Komitetu Technicznego Języków Programowania[(TC49),](https://www.ecma-international.org/memento/tc49.htm)a następnie przyjęte przez Zgromadzenie Ogólne Ecma, a następnie przez ISO/IEC JTC 1 w ramach procesu szybkiego działania ISO.

### <a name="latest-standards"></a>Najnowsze standardy

Następujące oficjalne dokumenty Ecma są dostępne dla [języka C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) i [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)):

- **Standard języka C# (wersja 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Wspólna infrastruktura językowa**: Dostępna w formie [pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) i [zip.](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip)
- **Informacje pochodzące z pliku XML Partition IV**: Dostępne w formatach [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) i [zip.](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip)

Oficjalne dokumenty ISO/IEC są dostępne na stronie NORMY [PUBLICZNE](https://standards.iso.org/ittf/PubliclyAvailableStandards/) ISO/IEC. Te linki są bezpośrednio z tej strony:

- **Informatyka - Języki programowania - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Technologia informacyjna — Partycje wspólnej infrastruktury językowej (CLI) I-VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Technologia informacyjna — Wspólna infrastruktura językowa (CLI) — Raport techniczny dotyczący informacji pochodzących z pliku XML partycji IV:** [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Zobacz też

- [Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [Przewodnik po rdzeniu .NET](../core/index.yml)
- [Przewodnik po platformach .NET Framework](../framework/index.yml)
- [C# Przewodnik](../csharp/index.yml)
- [F# Przewodnik](../fsharp/index.yml)
- [Przewodnik po podstawowych języka Visual](../visual-basic/index.yml)
