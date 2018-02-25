---
title: "Analizator przenośność .NET - .NET"
description: "Dowiedz się, jak można ocenić, jak przenośnego kodu jest między różne implementacje .NET, w tym oprogramowanie .NET Core, .NET Standard platformy uniwersalnej systemu Windows i Xamarin przy użyciu narzędzia Analizator przenośność .NET."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7e3d628fe4b4a8f01e692a70892658fceeb87953
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="the-net-portability-analyzer"></a>Analizator przenośność .NET

Mają być bibliotek obejmującego wiele platform? Chcesz zobaczyć, jak dużo pracy jest wymagana do uzyskania aplikacji zgodnych z innych implementacji .NET i profile, w tym oprogramowanie .NET Core, .NET Standard platformy uniwersalnej systemu Windows i program Xamarin dla systemu iOS, Android i komputerów Mac? [Analizator przenośność .NET](http://go.microsoft.com/fwlink/?LinkID=507467) to narzędzie, które umożliwia szczegółowe raportu w sposób elastyczny program jest przez implementacje .NET analizując zestawów. Analizator przenośność jest oferowany jako rozszerzenia programu Visual Studio i jako aplikacji konsoli.

## <a name="new-targets"></a>Nowe elementy docelowe

* [Oprogramowanie .NET core](../../core/index.md): ma modularny projekt, wykorzystuje side-by-side i jest przeznaczony dla scenariuszy wieloplatformowych. Side-by-side pozwala na przyjęcie nowych wersji platformy .NET Core bez przerywania innych aplikacji.
* [Platformy ASP.NET Core](/aspnet/core): to nowoczesnych sieci web — architektura oparta na .NET Core, dzięki czemu deweloperzy takich samych korzyści.
* [Platforma uniwersalna systemu Windows](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): poprawić wydajność aplikacji Sklepu Windows działających w x64 i architekturą ARM przy użyciu platformy .NET Native statycznych kompilacji. 
* + Rozszerzenia platformy .NET core: Zawiera podstawowych interfejsów API .NET oprócz innych interfejsów API w ekosystemie .NET, takie jak usługi WCF, platformy ASP.NET Core języka FSharp i Azure.
* .NET standard + rozszerzenia platformy: Obejmuje standardowych interfejsów API architektury .NET oprócz innych ekosystemu .NET, takie jak usługi WCF, platformy ASP.NET Core języka FSharp i Azure.

## <a name="how-to-use-portability-analyzer"></a>Jak używać analizatora przenośność

Aby rozpocząć korzystanie z analizatora przenośność .NET, należy najpierw pobrać i zainstalować rozszerzenie z [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=507467). Działa on w Visual Studio 2015 i Visual Studio 2017 r. Można go skonfigurować w programie Visual Studio za pomocą **Analizuj** > **ustawień analizatora przenośność** i wybierz z platformami docelowymi.

![Zrzut ekranu przenośność](./media/portability-analyzer/portability-screenshot.png)

Do analizy całego projektu, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **analizowanie przenośności zestawu**. W przeciwnym razie przejdź do **Analizuj** menu i wybierz **analizowanie przenośności zestawu**. Z tego miejsca wybierz plik wykonywalny projektu lub biblioteki DLL.

![Przenośność Eksploratora rozwiązań](./media/portability-analyzer/portability-solution-explorer.png)

Po zakończeniu analizy, zobaczysz raportu przenośność .NET. Tylko typy, które nie są obsługiwane przez platformę docelową znajdują się na liście i przejrzeć zalecenia w **wiadomości** karcie **listy błędów**. Można także przejść do obszarów problemów bezpośrednio z **wiadomości** kartę.

![Przenośność raportu](./media/portability-analyzer/portability-report.png)

Nie chcesz użyć programu Visual Studio? Umożliwia także analizator przenośność z wiersza polecenia. Wystarczy pobrać [analizator przenośność interfejsu API](http://www.microsoft.com/download/details.aspx?id=42678).

*   Wpisz następujące polecenie, aby przeanalizować bieżącego katalogu: `\...\ApiPort.exe analyze -f .`
*   Do analizowania określonych listą plików .dll, wpisz następujące polecenie: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

.NET przenośność raport jest zapisywany jako plik programu Excel (*xlsx*) w bieżącym katalogu. **Szczegóły** karta w skoroszycie programu Excel zawiera więcej informacji.

Aby uzyskać więcej informacji na analizator przenośność .NET, odwiedź stronę [dokumentacji GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i [A krótki przyjrzeć się analizator przenośność .NET](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) wideo z witryny Channel 9.
