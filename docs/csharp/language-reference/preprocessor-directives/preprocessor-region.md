---
title: '#region - Odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173396"
---
# <a name="region-c-reference"></a>#region (odwołanie w C#)
`#region`umożliwia określenie bloku kodu, który można rozwinąć lub zwinąć podczas korzystania z funkcji [konspektu](/visualstudio/ide/outlining) Edytora kodu programu Visual Studio. W dłuższych plikach kodu wygodnie jest zwinąć lub ukryć jeden lub więcej regionów, dzięki czemu można skupić się na części pliku, nad którą aktualnie pracujesz. W poniższym przykładzie pokazano, jak zdefiniować region:  
  
```csharp
#region MyClass definition  
public class MyClass
{  
    static void Main()
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>Uwagi  
 Blok `#region` musi zostać zakończony dyrektywą [#endregion.](./preprocessor-endregion.md)  
  
 Blok `#region` nie może nakładać się na blok [#if.](./preprocessor-if.md) Jednak `#region` blok może być zagnieżdżone w `#if` bloku, a `#if` blok może być zagnieżdżone w `#region` bloku.  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
