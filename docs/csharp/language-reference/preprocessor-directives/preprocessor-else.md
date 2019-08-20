---
title: '#else- C# Reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: d6a514f71b3526b2ffe347cdd971b81907fb0aad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605717"
---
# <a name="else-c-reference"></a>#else (odwołanie w C#)
`#else`umożliwia utworzenie złożonej dyrektywy warunkowej, tak aby w przypadku braku wyrażeń w powyższym [#if](./preprocessor-if.md) lub (opcjonalnie) [#elif](./preprocessor-elif.md) dyrektywy nie były oceniane do `true`, kompilator oceni cały kod między `#else` i kolejne `#endif`.  
  
## <a name="remarks"></a>Uwagi  
 Następną dyrektywą preprocesora po [ musi być ](./preprocessor-endif.md)#endif`#else`. Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](./preprocessor-if.md)#if`#else`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)
