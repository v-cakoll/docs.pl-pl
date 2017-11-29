---
title: "Tworzenie pakietu NuGet z wielu narzędzi platformy"
description: "Dowiedz się, jak utworzyć pakiet NuGet przy użyciu polecenia \"dotnet pack\"."
keywords: .NET, .NET core NuGet
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.openlocfilehash: a5738a4f3755a959660db4be683677673af61ef9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Jak utworzyć pakiet NuGet z wielu narzędzi platformy

> [!NOTE]
> Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix.  `dotnet pack` Polecenia w sposób pokazany poniżej działa tak samo w systemie Windows.

.NET Core 1.0 bibliotek powinny być dystrybuowane jako pakietów NuGet.  W rzeczywistości jest sposób wszystkich bibliotek .NET Standard distributed i używane.  Jest to łatwo zrobić za pomocą `dotnet pack` polecenia.

Załóżmy, po prostu zapisano świetny nowej biblioteki, który chcesz dystrybuować za pośrednictwem NuGet.  Można utworzyć pakietu NuGet z wielu narzędzi platformy w tym dokładnie!  W poniższym przykładzie założono bibliotece o nazwie **SuperAwesomeLibrary** cele, które `netstandard1.0`.

Jeśli masz przechodnie zależności; oznacza to, że projekt, który jest zależny od innego projektu, konieczne będzie upewnij się, że przywracanie pakietów dla całego rozwiązania z `dotnet restore` polecenia przed utworzeniem pakietu NuGet.  Niepowodzenie w tym przypadku spowoduje `dotnet pack` polecenia może nie działać poprawnie.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


Po sprawdzeniu, pakiety zostaną przywrócone, można przejść do katalogu, w którym mieszka biblioteki:

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

Należy pamiętać, że spowoduje to utworzenie pakietu, który jest w stanie debugowany.  Jeśli chcesz utworzyć pakiet NuGet przy użyciu wersji plików binarnych, wszystko co należy zrobić jest dodać `-c` / `--configuration` przełącznika i użyj `release` jako argument.

`$ dotnet pack --configuration release`

Twoje `/bin` folderu mają teraz `release` folderu zawierającego pakiet NuGet przy użyciu wersji plików binarnych:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

I teraz masz pliki niezbędne do publikowania pakietu NuGet!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Nie należy mylić `dotnet pack` z`dotnet publish`

Należy pamiętać, że w żadnym punkcie `dotnet publish` polecenia wykonywane.  `dotnet publish` Polecenie jest do wdrażania aplikacji za pomocą wszystkie zależności w tym samym pakiecie — nie w celu wygenerowania pakietu NuGet w celu można dystrybuować i używane za pośrednictwem pakietu NuGet.
