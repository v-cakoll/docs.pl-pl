---
title: Biblioteki SourceLink i platformy .NET
description: Najlepszym rozwiązaniem, zalecenia dotyczące używania SourceLink w celu debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: be97f868e2fcfc6c45e4bbac45b033f8914f4d99
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333541"
---
# <a name="sourcelink"></a>SourceLink

SourceLink to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów. SourceLink jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu. Deweloperzy, którzy pobrać pakiet oraz mieć włączone w programie Visual Studio SourceLink wejść do jego kod źródłowy. SourceLink udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.

## <a name="sourcelink-demo"></a>SourceLink demo

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>Za pomocą SourceLink

Instrukcje dotyczące korzystania z SourceLink znajduje się na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.

Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane SourceLink zostały pomyślnie osadzonego w pakiecie. Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.

![SourceLink w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink w Eksploratorze pakietu NuGet")

**ROZWAŻ ✔️** używanie SourceLink do dodawania metadanych do kontroli źródła do zestawów i pakietów NuGet.

> [!TIP]
> Przez dodanie atrybutów debugera do typów, może dodatkowo ulepszyć środowisko debugowania dla deweloperów.
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować, jak klasa lub pole jest wyświetlana w oknach zmiennych debugera.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod zamiast Przechodzenie do kodu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> Określa, czy członek jest wyświetlana w oknach zmiennych debugera.

**ROZWAŻ ✔️** publikowania plików symboli (`*.pdb`).

> Aby uzyskać więcej informacji na temat plików symboli i pakiety symboli, zobacz [symboli pakietów](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Poprzednie](dependencies.md)
>[dalej](publish-nuget-package.md)
