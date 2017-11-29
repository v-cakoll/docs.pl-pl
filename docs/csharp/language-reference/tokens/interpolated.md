---
title: "$ (Odwołanie w C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d245bab063721abdb930aae113aab2094553b9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a>$ (Odwołanie w C#)

Określa ciąg literału jako [interpolowane ciąg](../keywords/interpolated-strings.md). Ciąg typu szablonu, który zawiera literały tekstowe wraz z programem jest ciągu interpolowanym *interpolowane wyrażenia*. Po usunięciu ciągu interpolowanym, na przykład w instrukcji przypisania lub wywołanie metody jego interpolowanego wyrażenia zastępuje ich reprezentacji ciągu w ciągu wynik. Ciągi interpolowane są elementy zastępcze [ciągi formatujące złożonego](../../../standard/base-types/composite-format.md) obsługiwane przez program .NET Framework.

W poniższym przykładzie użyto `$` znaków do definiowania ciągu interpolowanym.

[!code-csharp[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

Aby uzyskać więcej informacji dotyczących ciągi interpolowane, zobacz [ciągi interpolowane](../keywords/interpolated-strings.md) tematu.

## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Znaki specjalne C#](../../../csharp/language-reference/tokens/index.md)
