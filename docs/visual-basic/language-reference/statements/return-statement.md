---
title: "Return — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a>Return — Instrukcja (Visual Basic)
Zwraca sterowania do kodu, który wywołał `Function`, `Sub`, `Get`, `Set`, lub `Operator` procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Część  
 `expression`  
 Wymagane w `Function`, `Get`, lub `Operator` procedury. Wyrażenie, które reprezentuje wartość zwracana do wywołującego kodu.  
  
## <a name="remarks"></a>Uwagi  
 W `Sub` lub `Set` procedury `Return` instrukcja jest odpowiednikiem `Exit Sub` lub `Exit Property` instrukcji i `expression` nie muszą być dostarczone.  
  
 W `Function`, `Get`, lub `Operator` procedury `Return` instrukcja musi zawierać `expression`, i `expression` musi mieć typ danych, który można przekonwertować na typ zwracany procedury. W `Function` lub `Get` procedury, masz również alternatywnej przypisywania wyrażenia na nazwę procedury jako wartość zwracaną i następnie wykonywanie `Exit Function` lub `Exit Property` instrukcji. W `Operator` procedurę, musisz użyć `Return``expression`.  
  
 Może zawierać tyle `Return` instrukcje zgodnie z potrzebami w tej samej procedury.  
  
> [!NOTE]
>  Kod w `Finally` bloku jest uruchamiany po `Return` instrukcji w `Try` lub `Catch` blok jest napotkano, ale przed nim `Return` wykonywania instrukcji. A `Return` instrukcji nie można uwzględnić w `Finally` bloku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Return` instrukcji kilka razy, aby powrócić do wywołującego kodu, gdy procedura nie trzeba nic robić.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get — instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set — instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit — instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
