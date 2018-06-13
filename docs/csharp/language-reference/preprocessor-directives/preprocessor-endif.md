---
title: '#ENDIF (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 1686e706ce5cae3b2eaa28a7e1c89b5694b2be88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269980"
---
# <a name="endif-c-reference"></a>#endif (odwołanie w C#)
`#endif` Określa koniec dyrektywy warunkowej, rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy. Na przykład  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Uwagi  
 Dyrektywy warunkowej, począwszy od `#if` dyrektywy, musi być jawnie zakończona z `#endif` dyrektywy. Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#endif`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
