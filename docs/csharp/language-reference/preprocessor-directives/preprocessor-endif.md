---
title: '#ENDIF - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 58e29363ca1298966ecf88e6b456f33f43a176b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573049"
---
# <a name="endif-c-reference"></a>#endif (odwołanie w C#)
`#endif` Określa koniec warunkowego dyrektywy, który rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy. Na przykład  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Uwagi  
 Dyrektywy warunkowej, począwszy od `#if` dyrektywy, jawnie muszą być zakończone znakiem `#endif` dyrektywy. Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#endif`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
