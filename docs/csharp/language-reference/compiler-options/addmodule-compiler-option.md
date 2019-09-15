---
title: -addmodule (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970187"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (C# opcje kompilatora)
Ta opcja dodaje moduł, który został utworzony za pomocą elementu docelowego: przełączenie modułu do bieżącej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`, `file2`  
 Plik wyjściowy zawierający metadane. Plik nie może zawierać manifestu zestawu. Aby zaimportować więcej niż jeden plik, oddziel nazwy plików przecinkami lub średnikami.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie moduły dodane za pomocą polecenia **-addmodule** muszą znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania. Oznacza to, że można określić moduł w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli moduł nie znajduje się w katalogu aplikacji w czasie wykonywania, <xref:System.TypeLoadException>otrzymasz.  
  
 `file`nie może zawierać zestawu. Na przykład jeśli plik wyjściowy został utworzony za pomocą [elementu-target: module](./target-module-compiler-option.md), jego metadane można zaimportować za pomocą polecenia **-addmodule**.  
  
 Jeśli plik wyjściowy został utworzony z opcją **-Target** inną niż **-target: module**, nie można zaimportować jej metadanych przy użyciu parametru **-addmodule** , ale można go zaimportować z [-Reference](./reference-compiler-option.md).  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio; projekt nie może odwoływać się do modułu. Ponadto nie można programowo zmienić tej opcji kompilatora.  
  
## <a name="example"></a>Przykład  
 Kompiluj plik `input.cs` źródłowy i Dodaj metadane z `metad1.netmodule` i `metad2.netmodule` do produkcji `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [Zestawy wieloplikowe](../../../framework/app-domains/multifile-assemblies.md)
- [Instrukcje: Kompilowanie zestawu wieloplikowego](../../../framework/app-domains/build-multifile-assembly.md)
