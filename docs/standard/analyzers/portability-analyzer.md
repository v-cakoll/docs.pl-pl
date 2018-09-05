---
title: Narzędzia .NET Portability Analyzer — .NET
description: Dowiedz się, jak ocenić, jak przenośny kod jest między różne implementacje platformy .NET, takich jak .NET Core, .NET Standard, platformy uniwersalnej systemu Windows i Xamarin za pomocą narzędzia .NET Portability Analyzer.
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 515dd7a393d87811377aa5d9fb02de35943b6966
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557327"
---
# <a name="the-net-portability-analyzer"></a>Narzędzia .NET Portability Analyzer

Czy chcesz wprowadzić bibliotek dla wielu platform? Chcesz zobaczyć, ile pracy jest wymagane, aby Twoje aplikacje zgodne z innych implementacji platformy .NET i profilów, w tym .NET Core, .NET Standard, platformy uniwersalnej systemu Windows i Xamarin dla systemów iOS, Android i Mac? [Narzędzia .NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) to narzędzie, które zawiera szczegółowy raport w sposób elastyczny Twój program jest w implementacji platformy .NET, analizując zestawy. Analizator przenośności jest oferowana jako rozszerzenia programu Visual Studio i aplikacji konsoli.

## <a name="new-targets"></a>Nowe obiekty docelowe

* [.NET core](../../core/index.md): ma modułowej, stosuje side-by-side i jest przeznaczony dla scenariuszy dla wielu platform. Side-by-side umożliwia wdrażanie nowych wersji platformy .NET Core bez przerywania innych aplikacji.
* [Platforma ASP.NET Core](/aspnet/core): to nowoczesnej sieci web — struktura oparta na module .NET Core, co daje deweloperom te same korzyści.
* [Universal Windows Platform](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): poprawianie wydajności aplikacji Windows Store przeznaczonych dla x64 i maszyn ARM przy użyciu platformy .NET Native kompilacji statyczne. 
* + Rozszerzenia platformy .NET core: Zawiera podstawowe interfejsy API .NET oprócz innych interfejsów API, należący do ekosystemu .NET, takich jak usługi WCF, ASP.NET Core, języka FSharp i platformy Azure.
* .NET standard + rozszerzenia platformy: Obejmuje standardowych interfejsów API .NET oprócz innych ekosystemu .NET, takich jak usługi WCF, ASP.NET Core, języka FSharp i platformy Azure.

## <a name="how-to-use-portability-analyzer"></a>Jak używać analizator przenośności

Aby rozpocząć korzystanie z narzędzia .NET Portability Analyzer, należy najpierw pobrać i zainstalować rozszerzenie z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Działa w programie Visual Studio 2015 i Visual Studio 2017. Można go skonfigurować w programie Visual Studio za pośrednictwem **analizy** > **Portability Analyzer ustawienia** i wybieranie platform docelowych.

![Zrzut ekranu przenośności](./media/portability-analyzer/portability-screenshot.png)

Aby analizować cały projekt, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **analizowanie przenośności zestawu**. W przeciwnym razie przejdź do **analizy** menu, a następnie wybierz **analizowanie przenośności zestawu**. W tym miejscu wybierz plik wykonywalny projektu lub biblioteki DLL.

![Eksplorator rozwiązań przenośności](./media/portability-analyzer/portability-solution-explorer.png)

Po uruchomieniu analizy, zobaczą raport przenośność .NET. Tylko typy, które nie są obsługiwane przez platformę docelową są wyświetlane na liście i przejrzeć zalecenia w **wiadomości** karcie **lista błędów**. Możesz również przejść do obszarów problemów bezpośrednio z **wiadomości** kartę.

![Przenośność raportu](./media/portability-analyzer/portability-report.png)

Nie chcesz używać programu Visual Studio? Można również użyć analizator przenośności w wierszu polecenia. Wystarczy pobrać [analizator przenośności interfejsu API](https://www.microsoft.com/download/details.aspx?id=42678).

*   Wpisz następujące polecenie, aby analizować bieżący katalog: `\...\ApiPort.exe analyze -f .`
*   Aby analizować określonych listą plików .dll, wpisz następujące polecenie: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

.NET Portability raport jest zapisywany jako plik programu Excel (*xlsx*) w bieżącym katalogu. **Szczegóły** karta w skoroszycie programu Excel zawiera więcej informacji.

Aby uzyskać więcej informacji dotyczących narzędzia .NET Portability Analyzer, odwiedź stronę [dokumentację GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i [krótki Przyjrzyj się narzędzia .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) wideo Channel 9.
