---
title: '-target: module (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393129"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: module (opcje kompilatora C#)
Ta opcja powoduje, że kompilator generuje manifest zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie plik wyjściowy, utworzone przez kompilowanie przy użyciu tej opcji będzie mieć rozszerzenie .netmodule.  
  
 Nie można załadować pliku, który nie ma w manifeście zestawu przez .NET Framework środowisko uruchomieniowe języka wspólnego. Jednak taki plik, należy włączyć do manifestu zestawu zestawu poprzez [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Jeśli więcej niż jeden moduł jest tworzona w jednej kompilacji, [wewnętrzny](../../../csharp/language-reference/keywords/internal.md) typów w jednym module będzie dostępny dla innych modułów w kompilacji. Gdy kod w odwołaniach do modułów jeden `internal` typów w innym module, a następnie obu modułów musi być włączona do manifestu zestawu przez **- addmodule —**.  
  
 Tworzenie modułu nie jest obsługiwane w środowisku programowania Visual Studio.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs`, tworzenie `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [-target (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
