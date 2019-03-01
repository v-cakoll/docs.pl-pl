---
title: Resume — instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: fcb50a9c7e36bab046be25d7f82f91cfe0f9be8e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966921"
---
# <a name="resume-statement"></a>Resume — Instrukcja
Wznawia działanie po zakończeniu procedury obsługi błędów.  
  
 Sugerujemy, że używasz strukturalna Obsługa wyjątków w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez określonej struktury i `On Error` i `Resume` instrukcji. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Części  
 `Resume`  
 Wymagana. Jeśli błąd wystąpił w tej samej procedury obsługi błędów, wykonanie zostanie wznowione za pomocą instrukcji, które spowodowały błąd. Jeśli błąd wystąpił w wywołanej procedurze, wykonanie wznawia działanie w instrukcji, która ostatnio wywołana poza procedura zawierająca procedurę obsługi błędów.  
  
 `Next`  
 Opcjonalna. Jeśli błąd wystąpił w tej samej procedury obsługi błędów, wykonanie zostanie wznowione za pomocą instrukcji natychmiast następującej instrukcji, które spowodowały błąd. Jeśli błąd wystąpił w wywołanej procedurze, wykonanie zostanie wznowione instrukcji od razu następującej instrukcji, które ostatnio wywołana poza procedura zawierająca procedurę obsługi błędów (lub `On Error Resume Next` instrukcji).  
  
 `line`  
 Opcjonalna. Wykonanie zostanie wznowione w wierszu określonym w wymaganym `line` argumentu. `line` Argument jest etykieta wiersza lub numer wiersza i musi znajdować się w tej samej procedury obsługi błędów.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Zalecane jest użycie strukturalna Obsługa wyjątków w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez określonej struktury i `On Error` i `Resume` instrukcji. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Jeśli używasz `Resume` wystąpi błąd instrukcji dowolnym innym niż w procedurze obsługi błędów.  
  
 `Resume` Instrukcji nie można używać w dowolnej procedury, która zawiera `Try...Catch...Finally` instrukcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Resume` instrukcję, aby zakończyć obsługi błędów w procedurze, a następnie wznowić wykonywania za pomocą instrukcji, które spowodowały błąd. Numer błędu 55 jest generowany w celu zilustrowania użytkowania `Resume` instrukcji.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz także
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error, instrukcja](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
