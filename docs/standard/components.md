---
title: "Składniki architektury .NET"
description: "W tym artykule opisano składniki architektury .NET, takie jak .NET Standard, .NET implementacji środowiska uruchomieniowe .NET i narzędzi."
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 08eeb08debdc2e71a85dbc18053bf1aac779069a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-architectural-components"></a>Składniki architektury .NET

Aplikacji .NET jest opracowany dla i działa w co najmniej jeden *implementacje .NET*.  Implementacje .NET obejmują .NET Framework .NET Core i Mono. Wspólne dla wszystkich implementacji programu .NET, który wywołał .NET Standard to specyfikacja interfejsu API. Ten artykuł zawiera krótkie wprowadzenie do każdego z tych pojęć.

## <a name="net-standard"></a>.NET standard

.NET Standard to zestaw interfejsów API, które są implementowane przez podstawowej biblioteki klas z implementacji programu .NET. Więcej formalnie jest specyfikacji interfejsów API platformy .NET, które tworzą jednolity zestaw kontraktów kompilowanych Twój kod. Umowy te są implementowane w każdej implementacji .NET. Dzięki temu przenośność przez inne implementacje .NET, skuteczne stosowanie wszędzie wykonywania kodu.

.NET Standard jest również [platformy docelowej](glossary.md#target-framework). Jeśli kod jest przeznaczony dla wersji programu .NET Standard, można go uruchomić w implementacji .NET obsługującej danej wersji programu .NET Standard.

Aby dowiedzieć się więcej o .NET Standard i stosowanie ich, zobacz [.NET Standard](net-standard.md) tematu.

## <a name="net-implementations"></a>Implementacje .NET

Każda implementacja .NET obejmuje następujące składniki:

- Jeden lub więcej środowisk uruchomieniowych. Przykłady: CLR programu .NET Framework, środowisko CoreCLR i CoreRT dla platformy .NET Core.
- Biblioteka klas, który implementuje standardowe .NET i może wdrożyć dodatkowe interfejsy API. Przykłady: Klasa podstawowa Biblioteka programu .NET Framework, .NET Core klasy podstawowej biblioteki.
- Opcjonalnie co najmniej jeden struktury aplikacji. Przykłady: [ASP.NET](https://www.asp.net/), [formularzy systemu Windows](../framework/winforms/windows-forms-overview.md), i [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) znajdują się w programie .NET Framework.
- Opcjonalnie narzędzia do programowania. Niektóre narzędzia do programowania są współużytkowane przez wiele implementacji.

Istnieją cztery głównej implementacje .NET, które firma Microsoft aktywnie rozwija i przechowuje: .NET Core, .NET Framework Mono i platformy uniwersalnej systemu Windows.

### <a name="net-core"></a>.NET Core

Oprogramowanie .NET core to implementacja i platform .NET i przeznaczone do obsługi obciążeń serwera i w chmurze na dużą skalę. Uruchamia go w systemie Windows, system macOS i Linux. Implementuje standardowe .NET, więc kod, który jest przeznaczony dla platformy .NET Standard można uruchamiać na .NET Core. Platformy ASP.NET Core działa na .NET Core. 

Aby dowiedzieć się więcej na temat platformy .NET Core, zobacz [.NET Core przewodnik](../core/index.md) i [wybór między .NET Core i .NET Framework dla aplikacji serwera](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework jest oryginalnym implementację .NET, która była dostępna już 2002. Jest tej samej .NET Framework, która zawsze używanych istniejących programistów platformy .NET. W wersji 4.5 i wdrożenie nowszej .NET Standard tak kodu, który jest przeznaczony dla platformy .NET Standard można uruchomić w tych wersjach systemu .NET Framework. Zawiera on dodatkowe interfejsy API właściwe dla systemu Windows, takich jak interfejsy API dla systemu Windows dla deweloperów pulpitu WPF i formularze systemu Windows. .NET Framework jest zoptymalizowana pod kątem tworzenia aplikacji klasycznych systemu Windows.

Aby dowiedzieć się więcej na temat programu .NET Framework, zobacz [.NET Framework — przewodnik](../framework/index.md).

### <a name="mono"></a>Mono

Mono jest implementację .NET, która jest głównie używane, gdy wymagana jest mała środowiska wykonawczego. To środowisko uruchomieniowe, które uprawnienia aplikacji platformy Xamarin Android, Mac, iOS, systemu tvOS i watchOS i koncentruje się przede wszystkim na niewielkie rozmiary.

Obsługuje wszystkie obecnie opublikowanej wersji platformy .NET Standard.

W przeszłości Mono zaimplementowana większych interfejsu API programu .NET Framework i emulowane niektóre najpopularniejsze funkcje w systemie Unix. Czasami służy do uruchamiania aplikacji .NET, które zależą od tych funkcji w systemie Unix.

Mono jest zwykle używana z kompilatora just in time, ale także kompilatora pełnej statyczne (kompilacja z wyprzedzeniem o czasie) używaną na platformach, np. z systemem iOS.

Aby dowiedzieć się więcej na temat Mono, zobacz [Mono dokumentacji](http://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Platforma uniwersalna systemu Windows (UWP)

Platformy uniwersalnej systemu Windows jest implementacja klasy .NET, który jest używany do tworzenia nowoczesnych, obsługą dotyku aplikacji systemu Windows, jak i oprogramowania dla Internetu rzeczy (IoT). Zostało zaprojektowane do ujednolicenie różne typy urządzeń, które chcesz docelowych, łącznie z komputerami, tablety, phablets, telefony i nawet Xbox. Platformy uniwersalnej systemu Windows udostępnia wiele usług, takich jak scentralizowane sklepu, środowiska wykonawczego (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT). Aplikacje mogą być napisane w języku C++, C#, VB.NET i JavaScript. Korzystając z języka C# i VB.NET, interfejsów API architektury .NET są udostępniane przez oprogramowanie .NET Core.

Aby dowiedzieć się więcej na temat platformy uniwersalnej systemu Windows, zobacz [wprowadzenie do platformy uniwersalnej systemu Windows](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Środowiska uruchomieniowe .NET

Środowisko wykonawcze jest środowiska wykonania programu zarządzanych. System operacyjny jest częścią środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET. Oto kilka przykładów środowisk uruchomieniowych .NET:
 
 - Środowisko uruchomieniowe języka wspólnego (CLR) dla programu .NET Framework
 - Podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR) dla platformy .NET Core
 - Architektura .NET native dla platformy uniwersalnej systemu Windows 
 - Mono środowiska wykonawczego dla platformy Xamarin.iOS, Xamarin.Android Xamarin.Mac i Mono framework pulpitu

## <a name="net-tooling-and-common-infrastructure"></a>Narzędzia .NET i wspólnej infrastruktury

Masz dostęp do rozbudowany zestaw narzędzi i składników infrastruktury, które współpracują z każdego wdrożenia programu .NET. Te obejmują, ale nie są ograniczone do następujących:

- Języków .NET i ich kompilatory
- System projektu platformy .NET (na podstawie *.csproj*, *vbproj*, i *.fsproj* plików)
- [MSBuild](/visualstudio/msbuild/msbuild), aparatu kompilacji używany do tworzenia projektów
- [NuGet](/nuget/), Menedżer pakietów firmy Microsoft dla programu .NET
- Orchestration kompilacji open source narzędzi, takich jak [CIASTO](http://cakebuild.net/) i [FAŁSZYWE](https://fake.build/)

## <a name="see-also"></a>Zobacz także
[Wybór między .NET Core i .NET Framework dla serwera aplikacji](choosing-core-framework-server.md)   
[.NET Standard](net-standard.md)  
[Przewodnik platformy .NET Core](../core/index.md)  
[.NET framework — przewodnik](../framework/index.md)  
[Przewodnik dla języka C#](../csharp/index.md)  
[Podręcznik języka F #](../fsharp/index.md)  
[Przewodnik VB.NET](../visual-basic/index.md)  

