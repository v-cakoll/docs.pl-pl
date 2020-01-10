---
title: Link źródłowy i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących używania linku źródłowego w celu usprawnienia debugowania bibliotek platformy .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 0ebc7601f1ad92b0fc6ab4c7599b010cb42feb5d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706442"
---
# <a name="source-link"></a>Link do źródła

Link źródłowy to technologia, która umożliwia debugowanie kodu źródłowego zestawów .NET z narzędzia NuGet przez deweloperów. Łącze źródłowe jest wykonywane podczas tworzenia pakietu NuGet i osadza metadane kontroli źródła wewnątrz zestawów i pakietu. Deweloperzy, którzy pobierają pakiet i łącze do źródła włączone w programie Visual Studio, mogą przejść do jego kodu źródłowego. Link źródłowy udostępnia metadane kontroli źródła w celu utworzenia doskonałego środowiska debugowania.

## <a name="source-link-demo"></a>Pokaz linku źródłowego

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Używanie linku źródłowego

Instrukcje dotyczące korzystania z linku źródłowego znajdują się w repozytorium [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) w witrynie GitHub.

Możesz użyć [Eksploratora pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) , aby potwierdzić, że metadane linku źródłowego zostały pomyślnie osadzone w pakiecie. Sprawdź, czy metadane `Repository` są obecne w identyfikatorze zatwierdzenia i czy pliki. pdb znajdują się w pliku. dll każdego elementu docelowego.

![Link źródłowy w Eksploratorze pakietów NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Link źródłowy w Eksploratorze pakietów NuGet")

**✔️ rozważyć** użycie linku źródłowego w celu dodania metadanych kontroli źródła do zestawów i pakietów NuGet.

> [!TIP]
> Możesz bardziej usprawnić środowisko debugowania dewelopera, dodając do swoich typów atrybuty debugera.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować sposób wyświetlania klasy lub pola w oknach zmiennych debugera.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> nakazuje debugerowi przechodzenie przez kod, a nie krokowe przechodzenie do kodu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> kontroluje, czy element członkowski jest wyświetlany w oknach zmiennych debugera.

**✔️ Rozważ** opublikowanie plików symboli (`*.pdb`).

> W celu uzyskania najlepszego środowiska debugowania biblioteka powinna publikować pliki symboli, a także używać linku źródłowego. Aby uzyskać więcej informacji na temat plików symboli i pakietów symboli, zobacz [pakiety symboli](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Poprzedni](dependencies.md)
>[Następny](publish-nuget-package.md)
