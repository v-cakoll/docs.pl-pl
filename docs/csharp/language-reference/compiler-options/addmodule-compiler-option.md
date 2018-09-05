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
ms.openlocfilehash: 39955d86085b49ef503ea9ed531df9feafa648ac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524591"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (opcje kompilatora C#)
Ta opcja dodaje moduł, który został utworzony po przełączeniu target: module na bieżącej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`, `file2`  
 Plik wyjściowy, który zawiera metadane. Plik nie zawiera manifest zestawu. Aby zaimportować więcej niż jeden plik, oddziel nazwy plików przecinkami lub średnikami.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie moduły dodawane z **- addmodule** musi znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania. Oznacza to, że można określić modułu w dowolnym katalogu, w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli moduł nie jest w katalogu aplikacji w czasie wykonywania, zostanie wyświetlony <xref:System.TypeLoadException>.  
  
 `file` nie może zawierać zestaw. Na przykład, jeśli plik wyjściowy został utworzony za pomocą [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), jego metadane mogą być importowane przy **- addmodule**.  
  
 Jeśli plik wyjściowy został utworzony za pomocą **-docelowej** opcji innych niż **-target: module**, nie można zaimportować metadanych z **- addmodule —** , ale mogą być importowane przy [— dokumentacja](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio; Projekt nie może odwoływać się do modułu. Ponadto ta opcja kompilatora nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompilowanie pliku źródłowego `input.cs` i Dodaj metadane z `metad1.netmodule` i `metad2.netmodule` do produkcji `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
- [Zestawy wieloplikowe](../../../framework/app-domains/multifile-assemblies.md)  
- [Instrukcje: kompilacja zestawów wieloplikowych](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
