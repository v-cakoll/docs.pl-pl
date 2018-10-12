---
title: Biblioteki SourceLink i platformy .NET
description: Najlepszym rozwiązaniem, zalecenia dotyczące używania SourceLink w celu debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123875"
---
# <a name="sourcelink"></a>SourceLink

SourceLink to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów. SourceLink jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu. Deweloperzy, którzy pobrać pakiet oraz mieć włączone w programie Visual Studio SourceLink wejść do jego kod źródłowy. SourceLink udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.

## <a name="sourcelink-demo"></a>Pokaz SourceLink

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>Za pomocą SourceLink

Instrukcje dotyczące korzystania z SourceLink znajduje się na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.

Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane SourceLink zostały pomyślnie osadzonego w pakiecie. Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.

![SourceLink w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink w Eksploratorze pakietu NuGet")

**ROZWAŻ ✔️** używanie SourceLink do dodawania metadanych kontroli źródła do zestawów i pakietów NuGet.

**ROZWAŻ ✔️** w tym pliki PDB w pakiecie NuGet.

>[!div class="step-by-step"]
[Poprzednie](./dependencies.md)
[dalej](./publish-nuget-package.md)
