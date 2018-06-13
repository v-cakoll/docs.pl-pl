---
title: 'Porady: kompilacja zestawu jednoplikowego'
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
ms.openlocfilehash: 6aa39671da519ebf54dad52638ab940897209517
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744320"
---
# <a name="how-to-build-a-single-file-assembly"></a>Porady: kompilacja zestawu jednoplikowego
Zestawu pojedynczego pliku, który jest najprostsza rodzaju zestawu, zawiera informacje o typie i wdrażania, jak również [manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md). Kompilatory w wierszu polecenia można użyć lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] można utworzyć zestawu pojedynczego pliku. Domyślnie kompilator tworzy plik zestawu z rozszerzeniem .exe.  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] C# i Visual Basic można użyć tylko w celu utworzenia zestawy jednoplikowe. Jeśli chcesz utworzyć zestawy wieloplikowe, należy użyć kompilatory w wierszu polecenia lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] w języku Visual C++.  
  
 Poniższe procedury pokazują, jak utworzyć zestawy jednoplikowe przy użyciu kompilatory w wierszu polecenia.  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a>Można utworzyć zestawu z rozszerzeniem .exe  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     \<*polecenie kompilatora*> \<*nazwy modułu*>  
  
     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu i *nazwy modułu* to nazwa modułu kodu do kompilacji w zestawie.  
  
 Poniższy przykład tworzy zestaw o nazwie `myCode.exe` z modułu kodu o nazwie `myCode`.  
  
```console
csc myCode.cs  
```  

```console
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Aby utworzyć zestaw z rozszerzeniem .exe i określ nazwę pliku wyjściowego  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     \<*polecenie kompilatora*> **/out:**\<*nazwę pliku*> \<*nazwy modułu*>  
  
     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu *nazwę pliku* to nazwa pliku wyjściowego i *nazwy modułu* jest nazwą Moduł kodu do kompilacji w zestawie.  
  
 Poniższy przykład tworzy zestaw o nazwie `myAssembly.exe` z modułu kodu o nazwie `myCode`.  
  
```console  
csc -out:myAssembly.exe myCode.cs  
```  
  
```console
vbc -out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a>Tworzenie zestawów biblioteki  
 Zestaw biblioteki jest podobny do biblioteki klas. Zawiera typy, które będzie odwoływać się do innych zestawów, ale nie żaden punkt wejścia, aby rozpocząć wykonywania.  
  
#### <a name="to-create-a-library-assembly"></a>Aby utworzyć zestaw biblioteki  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     \<*polecenie kompilatora*> **- t: Biblioteka** \< *nazwy modułu*>  
  
     W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu i *nazwy modułu* to nazwa modułu kodu do kompilacji w zestawie. Umożliwia także inne opcje kompilatora, takich jak **-out:** opcji.  
  
 Poniższy przykład tworzy zestaw biblioteczny o nazwie `myCodeAssembly.dll` z modułu kodu o nazwie `myCode`.  
  
```console  
csc -out:myCodeLibrary.dll -t:library myCode.cs  
```  
  
```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [Instrukcje: kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
