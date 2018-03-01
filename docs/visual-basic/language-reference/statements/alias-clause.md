---
title: "Alias — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f61e738434ea616d751576ef21669545afc41397
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="alias-clause-visual-basic"></a>Alias — Klauzula (Visual Basic)
Wskazuje, że procedura zewnętrzna ma inną nazwę w bibliotece DLL.  
  
## <a name="remarks"></a>Uwagi  
 `Alias` Można użyć słowa kluczowego, w tym kontekście:  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 W poniższym przykładzie `Alias` słowo kluczowe jest używane do określenia nazwy funkcji w advapi32.dll, `GetUserNameA`, że `getUserName` jest używany zamiast w tym przykładzie. Funkcja `getUserName` jest wywoływana w sub `getUser`, która zawiera nazwę bieżącego użytkownika.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
