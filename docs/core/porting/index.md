---
title: Eksportowanie do programu .NET Core z .NET Framework
description: Zrozumieć proces przenoszenia i Odkryj narzędzia, które mogą być przydatne podczas przenoszenia projektu .NET Framework i .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 10/23/2018
ms.openlocfilehash: 0c0ec3d8ab09e34e8dae24623903ca571f2cca6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192775"
---
# <a name="porting-to-net-core-from-net-framework"></a>Eksportowanie do programu .NET Core z .NET Framework

Jeśli masz kod uruchomiony w środowisku .NET Framework, może Cię zainteresować uruchamiania kodu na platformie .NET Core.  W tym artykule opisano przebieg procesu przenoszenia oraz listę narzędzi, które mogą być przydatne w przypadku przenoszenia do platformy .NET Core.

## <a name="overview-of-the-porting-process"></a>Omówienie procesu przenoszenia

Zalecany proces przenoszenia następuje poniższą sekwencję czynności.  Każdy z tych elementów, proces zostały omówione bardziej szczegółowo w dalszej artykułów.

1. Identyfikuj i uwzględnić zależności innych firm.

   Działania te obejmują zrozumienie, jakie zależności innych firm są, jak zależeć na ich, w jaki sposób, aby sprawdzić, czy działają one również na platformy .NET Core i kroki można wykonać, jeśli nie.
   
2. Przekieruj wszystkie projekty, które chcesz portów pod kątem najnowszych wersji programu .NET Framework.

   Daje to gwarancję, że można użyć interfejsu API alternatyw dla celów specyficzne dla platformy .NET Framework w przypadkach, w której platformy .NET Core nie obsługuje określony interfejs API.
   
3. Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i opracować plan do portu, na podstawie jej wyników.

   Narzędzie Analizator przenośności interfejsu API analizy skompilowanych zestawów i Generowanie raportu, który przedstawia podsumowanie wysokiego poziomu przenośność i podział każdy interfejs API używasz, nie jest dostępna na platformie .NET Core.  Możesz użyć tego raportu, wraz z analizą Twojej bazy kodu, aby opracować plan dla jak Twój kod będzie portu za pośrednictwem.
   
4. Przyłącz kod testów.

   Eksportowanie do programu .NET Core jest naprawdę spora zmiana bazie kodu, ma zdecydowanie zaleca uzyskać przenoszone, aby uruchomić testy zgodnie z portu kodu przez testy.  MSTest, xUnit i NUnit obecnie obsługuje platformy .NET Core.
   
6. Wykonaj swój plan w celu przenoszenia!

## <a name="tools-to-help"></a>Narzędzia ułatwiające

Poniżej przedstawiono krótką listę narzędzi, które będzie pomocne:

* NuGet — [klienta programu Nuget](https://dist.nuget.org/index.html) lub [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Menedżer pakietów firmy Microsoft dla implementacji platformy .NET.
* Analizator przenośności interfejsu API — [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) lub [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), łańcuch narzędzi, który można wygenerować raport jak przenośny kod jest między .NET Framework i .NET Core za pomocą zestaw, zestaw z rozbiciem na poszczególne problemy.  Zobacz [narzędzia ułatwiające procesu](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Aby uzyskać więcej informacji.
* Odwrócone wyszukiwanie pakietu - A [usługi sieci web przydatne](https://packagesearch.azurewebsites.net) umożliwiająca wyszukiwania dla typu i znajdowania pakiety zawierające tego typu.

## <a name="next-steps"></a>Następne kroki

[Analizowanie zależności innych firm.](third-party-deps.md)
   
