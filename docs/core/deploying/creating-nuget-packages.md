---
title: Tworzenie pakietu NuGet przy użyciu narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "dotnet Pack".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: d36a6ee7d524933577928daa9993fba8ce62f6c7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116698"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Jak utworzyć pakiet NuGet przy użyciu narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core

> [!NOTE]
> Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu UNIX. `dotnet pack` Polecenie, jak pokazano w tym miejscu, działa w taki sam sposób w systemie Windows.

Biblioteki .NET Standard i .NET Core są dystrybuowane jako pakiety NuGet. Jest to fakt, że wszystkie .NET Standard biblioteki są dystrybuowane i używane. Jest to najłatwiej wykonane za `dotnet pack` pomocą polecenia.

Załóżmy, że właśnie Zapisano nową bibliotekę, którą chcesz dystrybuować za pośrednictwem narzędzia NuGet. Pakiet NuGet można utworzyć przy użyciu narzędzi międzyplatformowych, aby dokładnie wykonać te czynności. W poniższym przykładzie przyjęto, że Biblioteka o nazwie `netstandard1.0`SuperAwesomeLibrary, której obiekty docelowe.

Jeśli istnieją zależności przechodnie; oznacza to, że projekt, który zależy od innego pakietu, przed utworzeniem pakietu NuGet należy przywrócić pakiety dla całego rozwiązania za pomocą `dotnet restore` polecenia. Wykonanie tej czynności spowoduje, że `dotnet pack` polecenie nie będzie działać prawidłowo.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów możesz przejść do katalogu, w którym przebywa Biblioteka:

```console
cd src/SuperAwesomeLibrary
```

Jest to tylko jedno polecenie z wiersza polecenia:

```dotnetcli
dotnet pack
```

`/bin/Debug` Folder będzie teraz wyglądać następująco:

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Należy pamiętać, że spowoduje to utworzenie pakietu, który jest w stanie debugować. Jeśli chcesz skompilować pakiet NuGet przy użyciu plików binarnych wydania, wystarczy dodać `--configuration` przełącznik (lub `-c`) i użyć `release` jako argument.

```dotnetcli
dotnet pack --configuration release
```

Folder będzie teraz `release` zawierać folder zawierający pakiet NuGet z wersjami plików binarnych: `/bin`

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Teraz masz wymagane pliki do opublikowania pakietu NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nie należy `dotnet pack` mylić z`dotnet publish`

Należy pamiętać, że w żadnym momencie nie jest to pożądane `dotnet publish` polecenie. `dotnet publish` Polecenie służy do wdrażania aplikacji ze wszystkimi zależnościami w tym samym pakiecie — nie do generowania pakietu NuGet, który ma być dystrybuowany i używany za pośrednictwem programu NuGet.

## <a name="see-also"></a>Zobacz także

- [Szybki start: Tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
