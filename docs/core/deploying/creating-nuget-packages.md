---
title: Tworzenie pakietu NuGet za pomocą interfejs wiersza polecenia platformy .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "dotnet Pack".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: ddc19faa7547637036686146f8600f40713541a8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740863"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Jak utworzyć pakiet NuGet przy użyciu narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core

> [!NOTE]
> Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu UNIX. Polecenie `dotnet pack`, jak pokazano w tym miejscu, działa w taki sam sposób w systemie Windows.

Biblioteki .NET Standard i .NET Core są dystrybuowane jako pakiety NuGet. Jest to fakt, że wszystkie .NET Standard biblioteki są dystrybuowane i używane. Jest to najłatwiej wykonane za pomocą polecenia `dotnet pack`.

Załóżmy, że właśnie Zapisano nową bibliotekę, którą chcesz dystrybuować za pośrednictwem narzędzia NuGet. Pakiet NuGet można utworzyć przy użyciu narzędzi międzyplatformowych, aby dokładnie wykonać te czynności. W poniższym przykładzie przyjęto, że biblioteka o nazwie **SuperAwesomeLibrary** , która jest przeznaczona dla `netstandard1.0`.

Jeśli istnieją zależności przechodnie, czyli projekt zależny od innego pakietu, należy przywrócić pakiety dla całego rozwiązania przy użyciu polecenia `dotnet restore` przed utworzeniem pakietu NuGet. W przeciwnym razie polecenie `dotnet pack` nie będzie działać prawidłowo.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów możesz przejść do katalogu, w którym przebywa Biblioteka:

```console
cd src/SuperAwesomeLibrary
```

Jest to tylko jedno polecenie z wiersza polecenia:

```dotnetcli
dotnet pack
```

Folder */bin/debug* będzie teraz wyglądać następująco:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Spowoduje to utworzenie pakietu, który może być debugowany. Jeśli chcesz skompilować pakiet NuGet przy użyciu plików binarnych wydania, wystarczy dodać przełącznik `--configuration` (lub `-c`) i użyć `release` jako argumentu.

```dotnetcli
dotnet pack --configuration release
```

Folder */bin.* będzie teraz zawierać folder *wersji* zawierający pakiet NuGet z wydaniami plików binarnych:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Teraz masz wymagane pliki do opublikowania pakietu NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nie należy mylić `dotnet pack` z `dotnet publish`

Należy pamiętać, że w żadnym momencie nie jest to `dotnet publish` polecenie. `dotnet publish` polecenie służy do wdrażania aplikacji ze wszystkimi zależnościami w tym samym pakiecie — nie do generowania pakietu NuGet, który ma być dystrybuowany i używany za pośrednictwem programu NuGet.

## <a name="see-also"></a>Zobacz także

- [Szybki Start: Tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
