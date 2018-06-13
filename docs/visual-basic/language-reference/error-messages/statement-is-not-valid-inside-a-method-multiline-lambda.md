---
title: Instrukcja nie jest prawidłowa wewnątrz metody wielowierszowego wyrażenia lambda
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef5beea16c8589a884b7d3533e0543454783999
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598858"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda
Instrukcja nie jest prawidłowy w ramach `Sub`, `Function`, właściwość `Get`, lub właściwości `Set` procedury. Niektóre instrukcji można umieścić na poziomie modułu lub klasy. Inne, takie jak `Option Strict`, musi znajdować się na poziomie przestrzeni nazw i poprzedzać wszystkie inne deklaracje.  
  
 **Identyfikator błędu:** BC30024  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń instrukcji z procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
