---
title: "Klasa delegata &#39; &lt;classname&gt;&#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords: BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Klasa delegata &#39; &lt;classname&gt;&#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
Wywołanie `Invoke` za pośrednictwem pełnomocnika nie powiodła się ponieważ `Invoke` nie jest zaimplementowana w klasie obiektów delegowanych.  
  
 **Identyfikator błędu:** BC30220  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że utworzono wystąpienie klasy delegata z `Dim` instrukcji i czy przypisano procedury na wystąpienie obiektu delegowanego z `AddressOf` operatora.  
  
2.  Znajdź kod, który implementuje klasie obiektów delegowanych i upewnij się, że implementuje `Invoke` procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty delegowane](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [AddressOf — Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
