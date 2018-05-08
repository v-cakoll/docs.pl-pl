---
title: Klasa obiektu delegowanego &#39; &lt;classname&gt; &#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: cc1abba46224772e733780800dd104dfc7ebe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Klasa obiektu delegowanego &#39; &lt;classname&gt; &#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
Wywołanie `Invoke` za pośrednictwem pełnomocnika nie powiodła się ponieważ `Invoke` nie jest zaimplementowana w klasie obiektów delegowanych.  
  
 **Identyfikator błędu:** BC30220  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że utworzono wystąpienie klasy delegata z `Dim` instrukcji i czy przypisano procedury na wystąpienie obiektu delegowanego z `AddressOf` operatora.  
  
2.  Znajdź kod, który implementuje klasie obiektów delegowanych i upewnij się, że implementuje `Invoke` procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
