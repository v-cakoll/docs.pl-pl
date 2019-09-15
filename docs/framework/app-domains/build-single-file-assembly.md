---
title: 'Instrukcje: Kompilowanie zestawu .NET Framework jednego pliku'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991249"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Instrukcje: Kompilowanie zestawu .NET Framework jednego pliku

Zestaw jednoplikowy, który jest najprostszym typem zestawu, zawiera informacje o typie i implementację, a także [manifest zestawu](../../standard/assembly/manifest.md). Można użyć kompilatorów wiersza polecenia lub programu Visual Studio, aby utworzyć zestaw jednoplikowy, który jest przeznaczony dla .NET Framework. Domyślnie kompilator tworzy plik zestawu z rozszerzeniem *. exe* .

> [!NOTE]
> Programu Visual Studio C# for i Visual Basic można używać tylko do tworzenia zestawów jednoplikowych. Jeśli chcesz utworzyć zestawy wieloplikowe, musisz użyć kompilatorów wiersza polecenia lub wizualizacji C++.

W poniższych procedurach pokazano, jak utworzyć zestawy Jednoplikowe za pomocą kompilatorów wiersza polecenia.

## <a name="create-an-assembly-with-an-exe-extension"></a>Utwórz zestaw z rozszerzeniem. exe

W wierszu polecenia wpisz następujące polecenie:

\<> *Nazwa modułu* poleceń\<kompilatora>

W tym poleceniu *kompilator* jest poleceniem kompilatora dla języka używanego w module kodu, a *Nazwa modułu* to nazwa modułu kodu do skompilowania do zestawu.

Poniższy przykład tworzy zestaw o nazwie mój *Code. exe* z modułu kodu o nazwie `myCode`.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Tworzenie zestawu z rozszerzeniem. exe i Określanie nazwy pliku wyjściowego

W wierszu polecenia wpisz następujące polecenie:

\<*polecenie*\<kompilatora/out: nazwa pliku nazwamodułu\<> > >

W tym poleceniu *kompilator* jest poleceniem kompilatora dla języka używanego w module kodu, *Nazwa pliku* jest nazwą pliku wyjściowego, a *Nazwa modułu* to nazwa modułu kodu do skompilowania do zestawu.

Poniższy przykład tworzy zestaw o nazwie mój *Assembly. exe* z modułu kodu o nazwie `myCode`.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Utwórz zestawy bibliotek
 Zestaw biblioteki jest podobny do biblioteki klas. Zawiera typy, do których odwołują się inne zestawy, ale nie ma punktu wejścia, aby rozpocząć wykonywanie.

Aby utworzyć zestaw biblioteki, w wierszu polecenia wpisz następujące polecenie:

\<polecenie> kompilatora — *Nazwa modułu* **t:Library** \<>

W tym poleceniu *kompilator* jest poleceniem kompilatora dla języka używanego w module kodu, a *Nazwa modułu* to nazwa modułu kodu do skompilowania do zestawu. Można również użyć innych opcji kompilatora, takich jak opcja **-out:** .

Poniższy przykład tworzy zestaw biblioteki o nazwie *myCodeAssembly. dll* z modułu kodu o nazwie `myCode`.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](../../standard/assembly/create.md)
- [Zestawy wieloplikowe](multifile-assemblies.md)
- [Instrukcje: Kompilowanie zestawu wieloplikowego](build-multifile-assembly.md)
- [Program z zestawami](../../standard/assembly/program.md)
