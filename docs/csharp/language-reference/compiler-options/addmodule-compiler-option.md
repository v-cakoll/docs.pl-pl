---
title: -addmodule (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970187"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (Opcje kompilatora C#)
Ta opcja dodaje moduł, który został utworzony za pomocą przełącznika target:module do bieżącej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`, `file2`  
 Plik wyjściowy zawierający metadane. Plik nie może zawierać manifestu zestawu. Aby zaimportować więcej niż jeden plik, należy oddzielić nazwy plików przecinkiem lub średnikiem.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie moduły dodane za pomocą **modułu -addmodule** muszą znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania. Oznacza to, że można określić moduł w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli moduł nie znajduje się w katalogu aplikacji w <xref:System.TypeLoadException>czasie wykonywania, otrzymasz plik .  
  
 `file`nie może zawierać zestawu. Na przykład, jeśli plik wyjściowy został utworzony za pomocą [-target:module,](./target-module-compiler-option.md)jego metadane mogą być importowane za pomocą **-addmodule**.  
  
 Jeśli plik wyjściowy został utworzony z opcją **-target** inną niż **-target:module,** jego metadanych nie można zaimportować za pomocą **modułu -addmodule,** ale można go zaimportować z [-reference](./reference-compiler-option.md).  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio; projekt nie może odwoływać się do modułu. Ponadto tej opcji kompilatora nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Skompiluj plik `input.cs` źródłowy i dodaj metadane z `metad1.netmodule` i `metad2.netmodule` do produkcji: `out.exe`  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [Zestawy wieloplikowe](../../../framework/app-domains/multifile-assemblies.md)
- [Porady: kompilacja zestawów wieloplikowych](../../../framework/app-domains/build-multifile-assembly.md)
