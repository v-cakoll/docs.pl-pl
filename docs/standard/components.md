---
title: Składniki architektury .NET
description: W tym artykule opisano składniki architektury .NET, takich jak .NET Standard, implementacje platformy .NET i środowiska uruchomieniowe platformy .NET oraz narzędzia.
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: e131ab48b666f2d22d8bd02e41ed76e415a2597d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034944"
---
# <a name="net-architectural-components"></a>Składniki architektury .NET

Aplikacja .NET został opracowany dla i działa w co najmniej jeden *implementacji .NET*.  Implementacje platformy .NET zawierają .NET Framework, .NET Core i platformy Mono. Specyfikacja interfejsu API jest wspólne dla wszystkich implementacji platformy .NET, który wywołał .NET Standard. Ten artykuł zawiera krótkie wprowadzenie do każdego z tych pojęć.

## <a name="net-standard"></a>.NET standard

.NET Standard to zestaw interfejsów API, które są implementowane przez Biblioteka klasy podstawowej implementacji .NET. Jest bardziej formalnie specyfikacji interfejsów API platformy .NET, wchodzące w skład jednolity zbiór umowy, które można skompilować kod. Umowy te są implementowane w każdej implementacji .NET. Dzięki temu przenośność między różne implementacje platformy .NET, co skutecznie kod wszędzie.

.NET Standard jest również [platformę docelową](glossary.md#target-framework). Jeśli Twój kod jest przeznaczony dla wersji programu .NET Standard, może działać na dowolnej implementacji .NET, który obsługuje daną wersję .NET Standard.

Aby dowiedzieć się więcej na temat .NET Standard i jak określić obiekt docelowy, zobacz [.NET Standard](net-standard.md) tematu.

## <a name="net-implementations"></a>Implementacje platformy .NET

Każda implementacja platformy .NET obejmuje następujące składniki:

- Co najmniej jeden środowisk uruchomieniowych. Przykłady: CLR programu .NET Framework, programów CoreCLR i CoreRT dla platformy .NET Core.
- Biblioteka klas, który implementuje .NET Standard i może wdrożyć dodatkowe interfejsy API. Przykłady: Podstawowej biblioteki klas .NET Framework, biblioteki klas podstawowych platformy .NET.
- Opcjonalnie co najmniej jeden struktury aplikacji. Przykłady: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), i [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) są zawarte w .NET Framework.
- Opcjonalnie narzędzia programistyczne. Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.

Istnieją cztery podstawowego implementacji .NET, które firma Microsoft aktywnie opracowuje i utrzymuje: .NET Core, .NET Framework, narzędzie Mono i platformy uniwersalnej systemu Windows.

### <a name="net-core"></a>.NET Core

.NET core jest implementacją dla wielu platform .NET i z myślą o obsłudze obciążeń serwera i chmury na dużą skalę. Działa na Windows, macOS i Linux. Implementuje .NET Standard, dzięki czemu kod, który jest przeznaczony dla .NET Standard może działać na platformie .NET Core. Platforma ASP.NET Core jest uruchamiany na platformie .NET Core. 

Aby dowiedzieć się więcej na temat platformy .NET Core, zobacz [przewodnik platformy .NET Core](../core/index.md) i [Wybieranie między programami .NET Core i .NET Framework dla aplikacji serwerowych](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

Środowiska.NET Framework jest oryginalnej implementacji .NET, która istniała od 2002. To ten sam .NET Framework, która istniejących deweloperów platformy .NET były zawsze używane. Wersje 4.5 i nowsze implementacji .NET Standard, więc kod, który jest przeznaczony dla .NET Standard można uruchomić w tych wersjach systemu .NET Framework. Zawiera on dodatkowe interfejsy API specyficzne dla Windows, takich jak programowanie aplikacji klasycznych interfejsów API dla Windows, Windows Forms i WPF. .NET Framework jest zoptymalizowane pod kątem tworzenia aplikacji klasycznych Windows.

Aby dowiedzieć się więcej na temat programu .NET Framework, zobacz [.NET Framework — przewodnik](../framework/index.md).

### <a name="mono"></a>Mono

Narzędzie mono jest implementacji .NET, która jest głównie używane, gdy wymagana jest mały środowiska uruchomieniowego. To środowisko uruchomieniowe, które obsługuje aplikacje platformy Xamarin na systemów Android, Mac, iOS, tvOS i watchOS i koncentruje się głównie na niewielkie rozmiary. Narzędzie mono obsługuje również gry utworzone przy użyciu aparatu Unity.

Obsługuje on wszystkie obecnie opublikowane wersje .NET Standard.

W przeszłości narzędzie Mono zaimplementowana większych interfejsu API programu .NET Framework i emulowane niektóre najpopularniejsze funkcje, w systemach Unix. To jest czasami używane do uruchamiania aplikacji .NET, które zależą od tych funkcji w systemach Unix.

Narzędzie mono jest zwykle używany z kompilator just-in-time, ale także kompilatora pełnej statyczne (kompilacja z wyprzedzeniem of-time), jaka jest używana na platformach, np. iOS.

Aby dowiedzieć się więcej na temat platformy Mono, zobacz [dokumentacja narzędzia Mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Platforma uniwersalna systemu Windows (UWP)

Platformy uniwersalnej systemu Windows jest implementacją platformy .NET, który jest używany do tworzenia nowoczesnych, obsługą dotyku aplikacje Windows, jak i oprogramowania dla Internetu rzeczy (IoT). Ustalono, aby zunifikować różnych typów urządzeń, które ma pod kątem, w tym komputerów, tabletów, phablets, telefony i nawet konsoli Xbox. Platformy uniwersalnej systemu Windows zapewnia wiele usług, takich jak w sklepie z aplikacjami scentralizowanego, środowisko wykonawcze (AppContainer) i zestaw interfejsów API Windows, zamiast Win32 (WinRT). Aplikacje mogą być napisane w języku C++, C#, VB.NET i JavaScript. Korzystając z języka C# i VB.NET, interfejsów API platformy .NET są dostarczane przez platformy .NET Core.

Aby dowiedzieć się więcej na temat platformy uniwersalnej systemu Windows, zobacz [wprowadzenie do platformy uniwersalnej Windows](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Środowiska uruchomieniowe platformy .NET

Środowisko uruchomieniowe jest środowisko wykonawcze programu zarządzanych. System operacyjny jest częścią środowiska wykonawczego, ale nie jest częścią środowiska uruchomieniowego .NET. Poniżej przedstawiono kilka przykładów środowiska uruchomieniowe platformy .NET:

- Środowisko uruchomieniowe języka wspólnego (CLR) w programie .NET Framework
- Podstawowe środowisko uruchomieniowe języka wspólnego (CoreCLR) dla platformy .NET Core
- Architektura .NET native dla platformy Universal Windows 
- Środowisko uruchomieniowe Mono dla platformy Xamarin.iOS, Xamarin.Android, Xamarin.Mac i Mono framework pulpitu

## <a name="net-tooling-and-common-infrastructure"></a>Narzędzia platformy .NET i wspólna infrastruktura

Masz dostęp do obszerny zestaw narzędzi i składników infrastruktury, współpracujących z każdej implementacji .NET. Te obejmują, ale nie są ograniczone do następujących:

- W językach .NET i ich kompilatory
- System projektu platformy .NET (na podstawie *.csproj*, *.vbproj*, i *.fsproj* plików)
- [Program MSBuild](/visualstudio/msbuild/msbuild), aparat kompilacji używany do tworzenia projektów
- [NuGet](/nuget/), Menedżer pakietów firmy Microsoft dla platformy .NET
- Narzędzia kompilacji typu open-source aranżacji, takich jak [TORT](https://cakebuild.net/) i [FAŁSZYWE](https://fake.build/)

## <a name="see-also"></a>Zobacz także

- [Wybieranie między programami .NET Core i .NET Framework na potrzeby aplikacji serwerowych](choosing-core-framework-server.md)   
- [.NET Standard](net-standard.md)  
- [Przewodnik platformy .NET Core](../core/index.md)  
- [.NET framework — przewodnik](../framework/index.md)  
- [Przewodnik dla języka C#](../csharp/index.md)  
- [Podręcznik języka F #](../fsharp/index.md)  
- [VB.NET Guide](../visual-basic/index.md)  
