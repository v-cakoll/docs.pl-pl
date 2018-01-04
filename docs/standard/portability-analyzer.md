---
title: "Analizator przenośność .NET - .NET"
description: "Dowiedz się, jak można ocenić, jak przenośnego kodu jest między różnymi implementacje .NET przy użyciu narzędzia Analizator przenośność .NET."
keywords: .NET, .NET core
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
ms.openlocfilehash: fef0ddb05cd95c2db5492004c46951bb69ea01d8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="the-net-portability-analyzer"></a>Analizator przenośność .NET

Mają być bibliotek obejmującego wiele platform? Chcesz zobaczyć, jak dużo pracy jest wymagana do udostępnienia aplikacji zgodne z innych implementacji .NET? [Analizator przenośność .NET](http://go.microsoft.com/fwlink/?LinkID=507467) to narzędzie, które umożliwia szczegółowe raportu w sposób elastyczny program jest przez implementacje .NET analizując zestawów. Analizator przenośność jest oferowany jako rozszerzenia programu Visual Studio i jako aplikacji konsoli.

## <a name="new-targets"></a>Nowe elementy docelowe

* [Oprogramowanie .NET core](https://dotnetfoundation.org/net-core): ma modularny projekt, wykorzystuje side-by-side i jest przeznaczony dla scenariuszy wieloplatformowych. Side-by-side pozwala na przyjęcie nowych wersji platformy .NET Core bez przerywania innych aplikacji.
* [Platformy ASP.NET Core](https://dotnetfoundation.org/asp-net-core): to nowoczesnych sieci web — architektura oparta na .NET Core, dzięki czemu deweloperzy takich samych korzyści.
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

*   Wpisz następujące polecenie, aby przeanalizować bieżącego katalogu:`\...\ApiPort.exe analyze -f .`
*   Do analizowania określonych listą plików .dll, wpisz następujące polecenie:`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

.NET przenośność raport jest zapisywany jako plik programu Excel (*xlsx*) w bieżącym katalogu. **Szczegóły** karta w skoroszycie programu Excel zawiera więcej informacji.

Aby uzyskać więcej informacji na analizator przenośność .NET, odwiedź stronę [dokumentacji GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) i [A krótki przyjrzeć się analizator przenośność .NET](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) wideo z witryny Channel 9.
