---
title: Instrukcja nie jest prawidłowa wewnątrz metody / wielowierszowego wyrażenia lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 994cafc44a37d16d0f70caec560f530c6a836ec0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841566"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda
Wykonywanie instrukcji nie jest prawidłowy w ramach `Sub`, `Function`, właściwość `Get`, lub właściwości `Set` procedury. Niektóre instrukcje mogą być umieszczone na poziomie modułu lub klasy. Inne, takie jak `Option Strict`, musi znajdować się na poziomie przestrzeni nazw i poprzedzać wszystkie inne deklaracje.  
  
 **Identyfikator błędu:** BC30024  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń instrukcję od procedury.  
  
## <a name="see-also"></a>Zobacz także

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
