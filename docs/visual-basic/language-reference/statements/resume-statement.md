---
title: "Resume — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a>Resume — Instrukcja
Wznawia wykonywanie po zakończeniu procedury obsługi błędów.  
  
 Zaleca się, że używasz, obsługa wyjątków strukturalnych w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez struktury i `On Error` i `Resume` instrukcje. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Części  
 `Resume`  
 Wymagany. Jeśli błąd wystąpił w tej samej procedury co program obsługi błędów, zostanie wznowione instrukcja, która spowodowała błąd wykonywania. Jeśli błąd wystąpił w wywoływana procedura, wykonanie wznawia działanie w instrukcji, która ostatnio została wywołana poza procedury zawierające procedury obsługi błędów.  
  
 `Next`  
 Opcjonalny. Jeśli w tę samą procedurę obsługi błędu wystąpił błąd, wykonanie wznawia z instrukcją natychmiast po instrukcji, który spowodował błąd. Jeśli błąd wystąpił w wywoływana procedura, wykonanie wznawia z instrukcją natychmiast po instrukcji, które ostatnio została wywołana poza procedury zawierająca procedurę obsługi błędu (lub `On Error Resume Next` instrukcji).  
  
 `line`  
 Opcjonalny. Wznawia wykonywanie w wierszu określonym w wymaganym `line` argumentu. `line` Argument wiersza etykiety lub numeru wiersza i musi być w tej samej procedury co program obsługi błędów.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Zalecane jest użycie Obsługa wyjątków strukturalnych w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez struktury i `On Error` i `Resume` instrukcje. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Jeśli używasz `Resume` instrukcji dowolnym innym niż w procedurze obsługi błędów, wystąpi błąd.  
  
 `Resume` Instrukcji nie można użyć w dowolnej procedury, która zawiera `Try...Catch...Finally` instrukcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Resume` instrukcji, aby zakończyć obsługi błędów w procedurze, a następnie Wznów wykonywanie instrukcji, który spowodował błąd. Błąd 55 jest generowane w celu zilustrowania użycie `Resume` instrukcji.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz też  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Error — instrukcja](../../../visual-basic/language-reference/statements/error-statement.md)  
 [On Error — instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
