---
title: Tworzenie pakietu NuGet za pomocą cli .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "dotnet pack".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920918"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>Jak utworzyć pakiet NuGet za pomocą cli .NET Core

> [!NOTE]
> Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix. Polecenie, `dotnet pack` jak pokazano tutaj działa w ten sam sposób w systemie Windows.

Oczekuje się, że biblioteki .NET Standard i .NET Core będą dystrybuowane jako pakiety NuGet. Jest to w rzeczywistości, jak wszystkie biblioteki .NET Standard są dystrybuowane i używane. Najłatwiej to zrobić `dotnet pack` za pomocą polecenia.

Wyobraź sobie, że właśnie napisał niesamowite nowej biblioteki, które chcesz rozpowszechniać za pomocą NuGet. Możesz utworzyć pakiet NuGet z narzędziami wieloplatformowymi, aby dokładnie to zrobić! W poniższym przykładzie przyjęto założenie biblioteki `netstandard1.0`o nazwie **SuperAwesomeLibrary,** która jest przeznaczona dla .

Jeśli masz zależności przechodnie, oznacza to, że projekt, który zależy od innego pakietu, `dotnet restore` upewnij się, aby przywrócić pakiety dla całego rozwiązania za pomocą polecenia przed utworzeniem pakietu NuGet. Niezastosowanie się do tego `dotnet pack` spowoduje, że polecenie nie działa poprawnie.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Po przywróceniu pakietów można przejść do katalogu, w którym znajduje się biblioteka:

```console
cd src/SuperAwesomeLibrary
```

Następnie jest to tylko jedno polecenie z wiersza polecenia:

```dotnetcli
dotnet pack
```

Folder */bin/Debug* będzie teraz wyglądał tak:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Spowoduje to wygenerowanie pakietu, który jest zdolny do debugowania. Jeśli chcesz utworzyć pakiet NuGet z plikami binarnymi wersji, `--configuration` wszystko, co musisz zrobić, to dodać (lub `-c`) przełącznik i używać `release` jako argument.

```dotnetcli
dotnet pack --configuration release
```

Folder */bin* będzie teraz miał folder *wersji* zawierający pakiet NuGet z plikami binarnymi wersji:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

A teraz masz niezbędne pliki do opublikowania pakietu NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nie myl `dotnet pack` się z`dotnet publish`

Ważne jest, aby pamiętać, że `dotnet publish` w żadnym momencie nie jest to polecenie zaangażowany. Polecenie `dotnet publish` służy do wdrażania aplikacji ze wszystkimi ich zależnościami w tym samym pakiecie — a nie do generowania pakietu NuGet do dystrybucji i używania za pośrednictwem NuGet.

## <a name="see-also"></a>Zobacz też

- [Szybki start: tworzenie i publikowanie pakietu](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
