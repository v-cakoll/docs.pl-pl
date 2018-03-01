---
title: "&#39; AddressOf &#39; Argument musi być nazwą metody (bez nawiasów)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39; AddressOf &#39; Argument musi być nazwą metody (bez nawiasów)
`AddressOf` Operator tworzy procedury wystąpienia delegata, który odwołuje się do określonej procedury. Składnia jest następująca:  
  
 `AddressOf``procedurename`  
  
 Dodaje nawiasy następujący argument `AddressOf`, gdy nie są jest potrzebne.  
  
 **Identyfikator błędu:** BC30577  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń nawiasy następujący argument `AddressOf`.  
  
2.  Upewnij się, że argument jest nazwą metody.  
  
## <a name="see-also"></a>Zobacz też  
 [AddressOf — Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Obiekty delegowane](../../../visual-basic/programming-guide/language-features/delegates/index.md)
