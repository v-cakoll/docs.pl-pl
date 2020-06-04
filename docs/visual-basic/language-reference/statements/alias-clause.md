---
title: Alias, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408474"
---
# <a name="alias-clause-visual-basic"></a>Alias — Klauzula (Visual Basic)
Wskazuje, że procedura zewnętrzna ma inną nazwę w bibliotece DLL.  
  
## <a name="remarks"></a>Uwagi  
 `Alias`Słowo kluczowe może być używane w tym kontekście:  
  
 [Declare — Instrukcja](declare-statement.md)  
  
 W poniższym przykładzie `Alias` słowo kluczowe jest używane do podania nazwy funkcji w advapi32. dll, `GetUserNameA` która `getUserName` jest używana zamiast w tym przykładzie. Funkcja `getUserName` jest wywoływana w sub `getUser` , która wyświetla nazwę bieżącego użytkownika.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe](../keywords/index.md)
