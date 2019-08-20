---
title: '-target: module (C# opcje kompilatora)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602444"
---
# <a name="-targetmodule-c-compiler-options"></a>-target: module (C# opcje kompilatora)
Ta opcja powoduje, że kompilator nie generuje manifestu zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie plik wyjściowy utworzony przez kompilację z tą opcją będzie miał rozszerzenie.  
  
 Nie można załadować pliku, który nie zawiera manifestu zestawu, za pomocą środowiska uruchomieniowego języka wspólnego .NET Framework. Jednak taki plik można włączyć do manifestu zestawu zestawu za pomocą [-addmodule](./addmodule-compiler-option.md).  
  
 W przypadku utworzenia więcej niż jednego modułu w pojedynczej kompilacji typy [wewnętrzne](../keywords/internal.md) w jednym module będą dostępne dla innych modułów w kompilacji. Gdy kod w jednym module odwołuje `internal` się do typów w innym module, oba moduły muszą być dołączone do manifestu zestawu, za pomocą **-addmodule**.  
  
 Tworzenie modułu nie jest obsługiwane w środowisku deweloperskim programu Visual Studio.  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs`, Utwórz `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [-Target (C# opcje kompilatora)](./target-compiler-option.md)
- [Opcje kompilatora C#](./index.md)
