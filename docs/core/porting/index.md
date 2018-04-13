---
title: Eksportowanie do platformy .NET Core z .NET Framework
description: Opis procesu przenoszenia i odnajdywanie narzędzia, które mogą być przydatne podczas przenoszenia projekt .NET Framework .NET Core.
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 00d00d38-99af-44f4-a75f-defcd9729dc5
ms.workload:
- dotnetcore
ms.openlocfilehash: 3413b73c2a0a3c3ebf49b0b3ec81d00c6558d9a8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core-from-net-framework"></a>Eksportowanie do platformy .NET Core z .NET Framework

Jeśli masz kodu uruchomionego w programie .NET Framework może Cię zainteresować systemem kodu .NET Core 1.0.  Ten artykuł zawiera omówienie procesu przenoszenia listę narzędzi, które mogą być przydatne przy eksportowaniu na .NET Core.

## <a name="overview-of-the-porting-process"></a>Omówienie procesu przenoszenia

Zalecany proces przy eksportowaniu obejmuje następujące serie kroków.  Każdy z tych elementów procesu są opisane bardziej szczegółowo w dalszej artykułach.

1. Identyfikowanie i konta dla zależności innych firm.

   Obejmuje understanding jakie zależności innych firm są, jak zależeć na ich sposób, aby sprawdzić, czy są one również uruchomić na oprogramowanie .NET Core i kroki można wykonać, jeśli tak nie jest.
   
2. Przekieruj wszystkie projekty, które chcesz dodać port do docelowej platformy .NET Framework 4.6.2.

   Dzięki temu, że można użyć interfejsu API alternatyw dla celów specyficzne dla platformy .NET Framework w przypadkach, gdy oprogramowanie .NET Core nie obsługuje określonego interfejsu API.
   
3. Użyj [narzędzia Analizator przenośność interfejsu API](https://github.com/Microsoft/dotnet-apiport/) do analizowania ponownie zestawy i opracowanie planu portu, na podstawie jej wyników.

   Narzędzie Analizator przenośność interfejsu API analizowanie ponownie skompilowane zestawy i Generowanie raportu, który znajduje się podsumowanie wysokiego poziomu przenośność i podział każdego interfejsu API używasz niedostępny na .NET Core.  Ten raport z analizy można użyć programu codebase aby opracować plan dla jak będzie port kodu za pośrednictwem.
   
4. Port kodu testy.

   Eksportowanie do platformy .NET Core jest duży zmiany do baza kodu, ma zalecane uzyskanie przenoszone, aby uruchomić testy zgodnie z portu kodu w testach.  MSTest, xUnit i NUnit obsługuje obecnie .NET Core 1.0.
   
6. Wykonanie planu przy eksportowaniu!

## <a name="tools-to-help"></a>Narzędzia ułatwiające

Poniżej przedstawiono krótką listę narzędzi, które znajdują się pomocne:

* NuGet - [klienta Nuget](https://dist.nuget.org/index.html) lub [Explorer pakietu NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Menedżer pakietów firmy Microsoft dla implementacji .NET.
* Analizator przenośność interfejsu API - [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) lub [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), łańcuch narzędzi, które można wygenerować raport jak przenośnego kodu jest między .NET Framework i .NET Core z Podział zestawu przez zestaw problemów.  Zobacz [narzędzi, aby ułatwić proces](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Aby uzyskać więcej informacji.
* Wstecznego wyszukiwania pakietu - A [usługi sieci web przydatne](https://packagesearch.azurewebsites.net) który służy do wyszukiwania typów i Znajdź pakiety zawierające tego typu.

## <a name="next-steps"></a>Następne kroki

[Analizowanie zależności innych firm.](third-party-deps.md)
   
