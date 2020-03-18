---
title: Łącze źródłowe i biblioteki .NET
description: Najlepsze zalecenia dotyczące używania łącza źródłowego w celu poprawy debugowania bibliotek .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744542"
---
# <a name="source-link"></a>Link do źródła

Source Link to technologia, która umożliwia debugowanie kodu źródłowego zestawów .NET z NuGet przez deweloperów. Łącze źródłowe jest wykonywane podczas tworzenia pakietu NuGet i osadza metadane kontroli źródła wewnątrz zestawów i pakietu. Deweloperzy, którzy pobierają pakiet i mają łącze źródłowe włączone w programie Visual Studio, mogą wkroczyć do jego kodu źródłowego. Łącze źródłowe udostępnia metadane kontroli źródła, aby utworzyć doskonałe środowisko debugowania.

## <a name="source-link-demo"></a>Wersja demonstracyjna Source Link

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Korzystanie z łącza źródłowego

Instrukcje dotyczące korzystania z łącza źródłowego można znaleźć w repozytorium GitHub [dotnet/sourcelink.](https://github.com/dotnet/sourcelink/blob/master/README.md)

Można użyć [NuGet Package Explorer,](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby potwierdzić, że metadane łącza źródłowego został pomyślnie osadzony w pakiecie. Sprawdź, `Repository` czy metadane są obecne z identyfikatorem zatwierdzenia i czy pliki .pdb znajdują się z dll każdego obiektu docelowego.

![Łącze źródłowe w Eksploratorze pakietów NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Łącze źródłowe w Eksploratorze pakietów NuGet")

✔️ ZAPOMOCĄ łącza źródłowego, aby dodać metadane kontroli źródła do zestawów i pakietów NuGet.

> [!TIP]
> Można dodatkowo zwiększyć środowisko debugowania dewelopera, dodając atrybuty debugera do swoich typów.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>można dostosować sposób wyświetlania klasy lub pola w oknach zmiennych debugera.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje debugera, aby krok po kroku kodu zamiast przechodzenia do kodu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>określa, czy element członkowski jest wyświetlany w oknach zmiennej debugera.

✔️ ROZWAŻ OPUBLIKOWANIE`*.pdb`plików symboli ( ).

> Aby uzyskać najlepsze środowisko debugowania, biblioteka powinna publikować pliki symboli, a także używać łącza źródłowego. Aby uzyskać więcej informacji na temat plików symboli i pakietów symboli, zobacz [Pakiety symboli](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Poprzedni](dependencies.md)
>[następny](publish-nuget-package.md)
