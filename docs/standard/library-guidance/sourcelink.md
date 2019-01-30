---
title: Biblioteki Linku źródłowego i platformy .NET
description: Zalecane najlepsze w celu debugowania bibliotek platformy .NET przy użyciu Linku źródłowego.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 10596f589af7abee6ff7833ef25c606294337196
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204759"
---
# <a name="source-link"></a>Link źródłowy

Link źródłowy jest to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów. Link źródłowy jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu. Deweloperzy, którzy pobrać pakiet oraz mieć Linku źródłowego włączone w programie Visual Studio można wkroczyć do jego kod źródłowy. Link źródłowy udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.

## <a name="source-link-demo"></a>Pokaz Linku źródłowego

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Przy użyciu Linku źródłowego

Instrukcje dotyczące przy użyciu Linku źródłowego znajduje się na [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.

Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane Link źródłowy został pomyślnie osadzonego w pakiecie. Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.

![Źródło Link w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "źródła Link w Eksploratorze pakietu NuGet")

**ROZWAŻ ✔️** przy użyciu Linku źródłowego, aby dodać metadanych kontroli źródła do zestawów i pakietów NuGet.

> [!TIP]
> Przez dodanie atrybutów debugera do typów, może dodatkowo ulepszyć środowisko debugowania dla deweloperów.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować, jak klasa lub pole jest wyświetlana w oknach zmiennych debugera.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod zamiast Przechodzenie do kodu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> Określa, czy członek jest wyświetlana w oknach zmiennych debugera.

**ROZWAŻ ✔️** publikowania plików symboli (`*.pdb`).

> Najlepszego środowiska debugowania biblioteki powinny pliki symboli pubish oraz przy użyciu Linku źródłowego. Aby uzyskać więcej informacji na temat plików symboli i pakiety symboli, zobacz [symboli pakietów](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Poprzednie](dependencies.md)
>[dalej](publish-nuget-package.md)
