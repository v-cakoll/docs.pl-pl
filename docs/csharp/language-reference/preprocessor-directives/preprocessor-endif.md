---
title: '#endif — odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712549"
---
# <a name="endif-c-reference"></a>#endif (odwołanie w C#)
`#endif`określa koniec dyrektywy warunkowej, która rozpoczęła się od [dyrektywy #if.](./preprocessor-if.md) Na przykład:  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Uwagi  
 Dyrektywa warunkowa, `#if` począwszy od dyrektywy, musi `#endif` zostać wyraźnie zakończona dyrektywą. Zobacz [#if](./preprocessor-if.md) przykład użycia `#endif`.  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
