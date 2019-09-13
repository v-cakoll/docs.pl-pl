---
title: Link źródłowy i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących używania linku źródłowego w celu usprawnienia debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928990"
---
# <a name="source-link"></a>Link do źródła

Link źródłowy to technologia, która umożliwia debugowanie kodu źródłowego zestawów .NET z narzędzia NuGet przez deweloperów. Łącze źródłowe jest wykonywane podczas tworzenia pakietu NuGet i osadza metadane kontroli źródła wewnątrz zestawów i pakietu. Deweloperzy, którzy pobierają pakiet i łącze do źródła włączone w programie Visual Studio, mogą przejść do jego kodu źródłowego. Link źródłowy udostępnia metadane kontroli źródła w celu utworzenia doskonałego środowiska debugowania.

## <a name="source-link-demo"></a>Pokaz linku źródłowego

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Używanie linku źródłowego

Instrukcje dotyczące korzystania z linku źródłowego znajdują się w repozytorium [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) w witrynie GitHub.

Możesz użyć [Eksploratora pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) , aby potwierdzić, że metadane linku źródłowego zostały pomyślnie osadzone w pakiecie. Sprawdź, `Repository` czy metadane są dostępne z identyfikatorem komentarza i czy pliki. pdb znajdują się w pliku. dll każdego elementu docelowego.

![Link źródłowy w Eksploratorze pakietów NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Link źródłowy w Eksploratorze pakietów NuGet")

**✔️ rozważyć** użycie linku źródłowego w celu dodania metadanych kontroli źródła do zestawów i pakietów NuGet.

> [!TIP]
> Możesz bardziej usprawnić środowisko debugowania dewelopera, dodając do swoich typów atrybuty debugera.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute>można dostosować sposób wyświetlania klasy lub pola w oknach zmiennych debugera.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute>nakazuje debugerowi przechodzenie przez kod, a nie krokowe przechodzenie do kodu.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute>Określa, czy element członkowski jest wyświetlany w oknach zmiennych debugera.

**✔️ Rozważ** opublikowanie plików symboli`*.pdb`().

> W celu uzyskania najlepszego środowiska debugowania biblioteka powinna publikować pliki symboli, a także używać linku źródłowego. Aby uzyskać więcej informacji na temat plików symboli i pakietów symboli, zobacz [pakiety symboli](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Poprzedni](dependencies.md)Następny
>[](publish-nuget-package.md)
