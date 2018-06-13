---
title: Alias — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 62b34f5860b35104b6a8caa82c359383999dd61b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599177"
---
# <a name="alias-clause-visual-basic"></a>Alias — Klauzula (Visual Basic)
Wskazuje, że procedura zewnętrzna ma inną nazwę w bibliotece DLL.  
  
## <a name="remarks"></a>Uwagi  
 Słowa kluczowego `Alias` można użyć w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 W poniższym przykładzie słowo kluczowe `Alias` jest używane do przekazania nazwy funkcji w pliku advapi32.dll, `GetUserNameA`, zamiast której w tym przykładzie występuje funkcja `getUserName`. Funkcja `getUserName` jest wywoływana w poleceniu Sub `getUser`, powodując wyświetlenie nazwy bieżącego użytkownika.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
