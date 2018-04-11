---
title: '#else (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3468d35a6e45c06f46fe8671708ce01a3cc7b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="else-c-reference"></a>#else (odwołanie w C#)
`#else` umożliwia utworzenie złożonej dyrektywy warunkowej polegającej na tym, że jeśli żadne z wyrażeń we wcześniejszych dyrektywach [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) i (opcjonalnie) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) nie zwróci wartości `true`, kompilator wykona kod między dyrektywą`#else` a następującą po niej dyrektywą`#endif`.
  
## <a name="remarks"></a>Uwagi  
 Następną dyrektywą preprocesora po `#else` musi być [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md). Aby zapoznać się z przykładem użycia dyrektywy `#else`, zobacz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md). 
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
