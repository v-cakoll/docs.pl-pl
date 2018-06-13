---
title: '-docelowych: module (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d02a46390ca34b8063320df6ec237a00c0423c88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214257"
---
# <a name="-targetmodule-c-compiler-options"></a>-docelowych: module (opcje kompilatora C#)
Ta opcja powoduje, że kompilator nie Generuj manifest zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie plik danych wyjściowych, utworzone przez kompilowania przy użyciu tej opcji będzie miał rozszerzenie modułu .netmodule.  
  
 Nie można załadować pliku, który nie ma manifestu zestawu przez .NET Framework środowisko uruchomieniowe języka wspólnego. Jednak taki plik można uwzględnić w manifeście zestawu zestawu za pomocą klasy [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Jeśli więcej niż jeden moduł jest tworzony w jednej kompilacji, [wewnętrzny](../../../csharp/language-reference/keywords/internal.md) typów w jeden moduł będzie dostępna dla innych modułów w kompilacji. Gdy kod w odwołaniach do modułów `internal` typów w innym module, a następnie obu modułów musi być włączona do manifestu zestawu za pomocą klasy **- addmodule**.  
  
 Tworzenie modułu nie jest obsługiwane w środowisku projektowym Visual Studio.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs`, tworzenie `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [-docelowego (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
