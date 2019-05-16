---
title: 'Instrukcje: Kompilacja zestawu jednoplikowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a409a93e5d84e96bbab13f2f6268d7f7ce6464ed
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634244"
---
# <a name="how-to-build-a-single-file-assembly"></a>Instrukcje: Kompilacja zestawu jednoplikowego

Zestawu pojedynczego pliku to najprostszy rodzaj zestawów, zawiera informacje o typie i wdrażania, jak również [manifestu zestawu](../../../docs/framework/app-domains/assembly-manifest.md). Można użyć kompilatorów wiersza polecenia lub programu Visual Studio, można utworzyć zestawu pojedynczego pliku. Domyślnie kompilator tworzy plik zestawu z rozszerzeniem .exe.

> [!NOTE]
> Program Visual Studio dla języka C# i Visual Basic mogą służyć tylko do tworzenia zespołów pojedynczego pliku. Jeśli chcesz utworzyć zestawy wieloplikowe, należy użyć kompilatorów wiersza polecenia lub programu Visual C++.

Poniższe procedury przedstawiają sposób tworzenia zespołów pojedynczego pliku za pomocą kompilatorów wiersza polecenia.

## <a name="to-create-an-assembly-with-an-exe-extension"></a>Aby utworzyć zestaw z rozszerzeniem .exe

1. W wierszu polecenia wpisz następujące polecenie:

     \<*polecenie kompilatora*> \<*Nazwa modułu*>

     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu, i *Nazwa modułu* to nazwa modułu kodu, aby skompilować do zestawu.

 Poniższy przykład tworzy zestaw o nazwie `myCode.exe` moduł kodu o nazwie `myCode`.

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Aby utworzyć zestaw z rozszerzeniem .exe i określ nazwę pliku wyjściowego

1. W wierszu polecenia wpisz następujące polecenie:

     \<*polecenie kompilatora*> **/out:**\<*nazwy pliku*> \<*Nazwa modułu*>

     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu, *nazwy pliku* jest nazwa pliku wyjściowego i *Nazwa modułu* nazywa się Moduł kodu, aby skompilować do zestawu.

 Poniższy przykład tworzy zestaw o nazwie `myAssembly.exe` moduł kodu o nazwie `myCode`.

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a>Tworzenie zestawów biblioteki
 W zestawie biblioteki jest podobny do biblioteki klas. Zawiera typy, które będzie używane przez inne zestawy, ale go nie ma punktu wejścia do rozpoczęcia wykonywania.

### <a name="to-create-a-library-assembly"></a>Można utworzyć zestawu biblioteki

1. W wierszu polecenia wpisz następujące polecenie:

     \<*polecenie kompilatora*> **- t: Biblioteka** \< *Nazwa modułu*>

     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu, i *Nazwa modułu* to nazwa modułu kodu, aby skompilować do zestawu. Umożliwia także inne opcje kompilatora, takich jak **-out:** opcji.

 Poniższy przykład tworzy zestaw biblioteki o nazwie `myCodeAssembly.dll` moduł kodu o nazwie `myCode`.

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)
- [Instrukcje: Kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
