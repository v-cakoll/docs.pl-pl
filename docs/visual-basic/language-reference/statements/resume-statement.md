---
title: Resume — Instrukcja
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
ms.openlocfilehash: 95137a9f6a4a4a18655b51b95300bfaf93cca193
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333028"
---
# <a name="resume-statement"></a>Resume — Instrukcja
Wznawia wykonywanie po zakończeniu procedury obsługi błędu.  
  
 Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z obsługi wyjątków niestrukturalnych oraz instrukcji `On Error` i `Resume`. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Części  
 `Resume`  
 Wymagana. Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji, która spowodowała błąd. Jeśli wystąpił błąd w wywoływanej procedurze, wykonanie zostaje wznowione w instrukcji, która została ostatnio wywołana z procedury zawierającej procedurę obsługi błędu.  
  
 `Next`  
 Opcjonalna. Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która spowodowała błąd. Jeśli wystąpił błąd w wywoływanej procedurze, wykonywanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która została ostatnio wywołana z procedury zawierającej procedury obsługi błędu (lub instrukcji `On Error Resume Next`).  
  
 `line`  
 Opcjonalna. Wykonanie wznowione w wierszu określonym w wymaganym argumencie `line`. Argument `line` jest etykietą wiersza lub numerem wiersza i musi znajdować się w tej samej procedurze jak program obsługi błędów.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z obsługi wyjątków niestrukturalnych oraz instrukcji `On Error` i `Resume`. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Jeśli używasz instrukcji `Resume` w innym miejscu niż w procedurze obsługi błędów, wystąpi błąd.  
  
 Instrukcji `Resume` nie można użyć w żadnej procedurze, która zawiera instrukcję `Try...Catch...Finally`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa instrukcji `Resume`, aby zakończyć obsługę błędów w procedurze, a następnie wznowić wykonywanie przy użyciu instrukcji, która spowodowała błąd. Numer błędu 55 został wygenerowany w celu zilustrowania użycia instrukcji `Resume`.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Zobacz także

- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error, instrukcja](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
