---
title: -addmodule (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: a5b0824774dabd4e0dd26dd1753eaba658299fbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (opcje kompilatora C#)
Ta opcja dodaje moduł, który został utworzony z opcją docelowych: moduł do bieżącej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`, `file2`  
 Plik wyjściowy, który zawiera metadanych. Plik nie zawiera manifest zestawu. Aby zaimportować więcej niż jeden plik, Rozdziel nazwy pliku przecinkami lub średnikami.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie moduły dodawane z **- addmodule** musi być w tym samym katalogu co plik wyjściowy w czasie wykonywania. Oznacza to można określić modułu w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli moduł nie jest w katalogu aplikacji w czasie wykonywania, otrzymasz <xref:System.TypeLoadException>.  
  
 `file` nie może zawierać zestawu. Na przykład, jeśli utworzono plik wyjściowy [-docelowych: moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), jego metadane mogą być importowane przy **- addmodule**.  
  
 Jeśli utworzono plik wyjściowy **— docelowy** opcji innych niż **— docelowych: moduł**, nie można zaimportować metadanych z **- addmodule** , ale mogą być importowane przy [— odwołanie](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio; Projekt nie może odwoływać się do modułu. Ponadto kompilatora nie można zmienić tej opcji programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluj plik źródłowy `input.cs` i Dodaj metadane z `metad1.netmodule` i `metad2.netmodule` do produkcji `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Zestawy wieloplikowe](../../../framework/app-domains/multifile-assemblies.md)  
 [Instrukcje: kompilacja zestawów wieloplikowych](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
