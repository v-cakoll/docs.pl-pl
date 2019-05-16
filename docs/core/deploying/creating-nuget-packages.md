---
title: Utwórz pakiet NuGet za pomocą narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "pakietu dotnet".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b86b2706968bf302a8421bcc8e12c32a97102e9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632111"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Jak utworzyć pakiet NuGet za pomocą narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core

> [!NOTE]
> Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix. `dotnet pack` Polecenia, jak pokazano poniżej na Windows działa tak samo.

Powinny być dystrybuowane jako pakiety NuGet biblioteki .NET standard i .NET Core. Jest to w rzeczywistości, jak wszystkie biblioteki .NET Standard rozproszone i używane. Łatwo to zrobić za pomocą `dotnet pack` polecenia.

Wyobraź sobie, napisany właśnie awesome nowej biblioteki, które chcesz dystrybuować za pośrednictwem NuGet. Można utworzyć pakietu NuGet wraz z tym dokładnie narzędzi międzyplatformowych! W poniższym przykładzie założono biblioteki, o nazwie **SuperAwesomeLibrary** które elementy docelowe `netstandard1.0`.

Jeśli masz przechodnie zależności oznacza to, że projekt, który jest zależny od innego pakietu, konieczne będzie upewnij się, że przywracanie pakietów dla całego rozwiązania przy użyciu `dotnet restore` polecenia przed utworzeniem pakietu NuGet. Niepowodzenie w tym spowoduje `dotnet pack` polecenia nie będą działać prawidłowo.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po upewnieniu się, pakiety zostaną przywrócone, możesz przejść do katalogu, w którym przebywa biblioteki:

```console
cd src/SuperAwesomeLibrary
```

Następnie jest tylko jednego polecenia w wierszu polecenia:

```console
dotnet pack
```

Twoje `/bin/Debug` folder będzie teraz wyglądać następująco:

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Należy pamiętać, pozwoli to osiągnąć pakietu, który jest w stanie debugowane. Jeśli chcesz utworzyć pakiet NuGet przy użyciu wersji plików binarnych, wszystko, czego potrzebujesz, aby zrobić to dodanie `--configuration` (lub `-c`) Przełącz i użyj `release` jako argument.

```console
dotnet pack --configuration release
```

Twoje `/bin` folderu będą teraz mieć `release` folder zawierający pakiet NuGet z plikami binarnymi wersji:

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

I czy masz pliki niezbędne do publikowania pakietu NuGet teraz!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nie należy mylić `dotnet pack` z `dotnet publish`

Ważne jest, aby pamiętać, że w żadnym punkcie nie jest `dotnet publish` zaangażowane polecenia. `dotnet publish` Polecenie służy do wdrażania aplikacji za pomocą wszystkie zależności są tego samego pakietu — nie dla generowania pakietu NuGet do dystrybucji i używane za pośrednictwem pakietu NuGet.

## <a name="see-also"></a>Zobacz także

- [Szybki start: Tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
