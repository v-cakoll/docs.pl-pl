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
ms.openlocfilehash: 3f49f05f1deb2027b03bbf3443ca44f30c44344e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404216"
---
# <a name="resume-statement"></a>Resume — Instrukcja
Wznawia wykonywanie po zakończeniu procedury obsługi błędu.  
  
 Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z obsługi wyjątków bez struktury i `On Error` instrukcji i `Resume` . Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Części  
 `Resume`  
 Wymagany. Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji, która spowodowała błąd. Jeśli wystąpił błąd w wywoływanej procedurze, wykonanie zostaje wznowione w instrukcji, która została ostatnio wywołana z procedury zawierającej procedurę obsługi błędu.  
  
 `Next`  
 Opcjonalny. Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która spowodowała błąd. Jeśli wystąpił błąd w wywoływanej procedurze, wykonywanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która została ostatnio wywołana z procedury zawierającej procedury obsługi błędu (lub `On Error Resume Next` instrukcji).  
  
 `line`  
 Opcjonalny. Wykonanie wznowione w wierszu określonym w wymaganym `line` argumencie. `line`Argument jest etykietą wiersza lub numerem wiersza i musi znajdować się w tej samej procedurze jak program obsługi błędów.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie to możliwe, zamiast używania obsługi wyjątków niestrukturalnych i `On Error` `Resume` instrukcji i. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).  
  
 Jeśli używasz `Resume` instrukcji w innym miejscu niż w procedurze obsługi błędów, wystąpi błąd.  
  
 `Resume`Instrukcji nie można używać w żadnej procedurze zawierającej `Try...Catch...Finally` instrukcję.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `Resume` instrukcji, aby zakończyć obsługę błędów w procedurze, a następnie wznowić wykonywanie przy użyciu instrukcji, która spowodowała błąd. Numer błędu 55 został wygenerowany w celu zilustrowania użycia `Resume` instrukcji.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Wymagania  
 **Przestrzeń nazw:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Zobacz też

- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
- [Error — Instrukcja](error-statement.md)
- [On Error, instrukcja](on-error-statement.md)
