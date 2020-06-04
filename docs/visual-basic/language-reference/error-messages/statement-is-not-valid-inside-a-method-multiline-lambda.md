---
title: Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: f3c43d640259d5e1af545e2610088aab5d70453d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396249"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda
Instrukcja nie jest prawidłowa w ramach `Sub` procedury, `Function` , właściwości `Get` lub właściwości `Set` . Niektóre instrukcje mogą być umieszczane na poziomie modułu lub klasy. Inne, takie jak `Option Strict` , muszą znajdować się na poziomie przestrzeni nazw i poprzedzać wszystkie inne deklaracje.  
  
 **Identyfikator błędu:** BC30024  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń instrukcję z procedury.  
  
## <a name="see-also"></a>Zobacz też

- [Sub, instrukcja](../statements/sub-statement.md)
- [Function, instrukcja](../statements/function-statement.md)
- [Get — Instrukcja](../statements/get-statement.md)
- [Set — Instrukcja](../statements/set-statement.md)
