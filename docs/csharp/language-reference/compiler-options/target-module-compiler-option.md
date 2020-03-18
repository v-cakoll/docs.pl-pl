---
title: -target:module (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602444"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (Opcje kompilatora C#)
Ta opcja powoduje, że kompilator nie generuje manifestu zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie plik wyjściowy utworzony przez kompilację z tą opcją będzie miał rozszerzenie .netmodule.  
  
 Nie można załadować pliku, który nie ma manifestu zestawu, przez czas uruchomieniowy wspólnego języka .NET Framework. Jednak taki plik może być włączony do manifestu zestawu za pomocą [-addmodule](./addmodule-compiler-option.md).  
  
 Jeśli więcej niż jeden moduł jest tworzony w jednej kompilacji, typy [wewnętrzne](../keywords/internal.md) w jednym module będą dostępne dla innych modułów w kompilacji. Gdy kod w `internal` jednym module odwołuje się do typów w innym module, oba moduły muszą być włączone do manifestu zestawu za pomocą **-addmodule**.  
  
 Tworzenie modułu nie jest obsługiwane w środowisku programistycznym programu Visual Studio.  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 `in.cs`Kompiluj `in.netmodule`, tworząc:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [-target (Opcje kompilatora C#)](./target-compiler-option.md)
- [Opcje kompilatora Języka C#](./index.md)
