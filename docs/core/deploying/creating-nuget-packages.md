---
title: Tworzenie pakietu NuGet za pomocą narzędzi międzyplatformowych
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "pakietu dotnet".
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 6be94c2e2cef443f69b2d6df7c2d490cb1fb629d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536024"
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Jak utworzyć pakiet NuGet za pomocą narzędzi międzyplatformowych

> [!NOTE]
> Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix.  `dotnet pack` Polecenia, jak pokazano poniżej na Windows działa tak samo.

Dla platformy .NET Core 1.0 bibliotek powinny znajdować się jako pakiety NuGet.  Jest to w rzeczywistości, jak wszystkie biblioteki .NET Standard rozproszone i używane.  Łatwo to zrobić za pomocą `dotnet pack` polecenia.

Wyobraź sobie, napisany właśnie awesome nowej biblioteki, które chcesz dystrybuować za pośrednictwem NuGet.  Można utworzyć pakietu NuGet wraz z tym dokładnie narzędzi międzyplatformowych!  W poniższym przykładzie założono biblioteki, o nazwie **SuperAwesomeLibrary** które elementy docelowe `netstandard1.0`.

Jeśli masz przechodnie zależności oznacza to, że projekt, który jest zależny od innego projektu, musisz upewnij się, że przywracanie pakietów dla całego rozwiązania przy użyciu `dotnet restore` polecenia przed utworzeniem pakietu NuGet.  Niepowodzenie w tym spowoduje `dotnet pack` polecenia nie będą działać prawidłowo.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


Po upewnieniu się, pakiety zostaną przywrócone, możesz przejść do katalogu, w którym przebywa biblioteki:

`$ cd src/SuperAwesomeLibrary`

Następnie jest tylko jednego polecenia w wierszu polecenia:
    
`$ dotnet pack`

Twoje `/bin/Debug` folder będzie teraz wyglądać następująco:

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Należy pamiętać, pozwoli to osiągnąć pakietu, który jest w stanie debugowane.  Jeśli chcesz utworzyć pakiet NuGet przy użyciu wersji plików binarnych, wszystko, czego potrzebujesz, aby zrobić to dodanie `-c` / `--configuration` przełącznika i użyj `release` jako argument.

`$ dotnet pack --configuration release`

Twoje `/bin` folderu będą teraz mieć `release` folder zawierający pakiet NuGet z plikami binarnymi wersji:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

I czy masz pliki niezbędne do publikowania pakietu NuGet teraz!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nie należy mylić `dotnet pack` z `dotnet publish`

Ważne jest, aby pamiętać, że w żadnym punkcie nie jest `dotnet publish` zaangażowane polecenia.  `dotnet publish` Polecenie służy do wdrażania aplikacji ze wszystkimi ich zależności w ten sam pakiet — nie dla generowania pakietu NuGet do dystrybucji i używane za pośrednictwem pakietu NuGet.
