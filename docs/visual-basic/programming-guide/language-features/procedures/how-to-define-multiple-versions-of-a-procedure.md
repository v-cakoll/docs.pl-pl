---
title: 'Porady: definiowanie wielu wersji procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: e8ed9a6356b7177b2c029a9280d0790a93676653
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347603"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Porady: definiowanie wielu wersji procedury (Visual Basic)
Można zdefiniować procedurę w wielu wersjach przez *przekazanie* jej przy użyciu tej samej nazwy, ale innej listy parametrów dla każdej wersji. Przeciążanie polega na zdefiniowaniu kilku ściśle powiązanych wersji procedury bez konieczności odróżnienia ich według nazwy.  
  
 Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Aby zdefiniować wiele wersji procedury  
  
1. Napisz `Sub` lub instrukcję deklaracji `Function` dla każdej wersji procedury, która ma zostać zdefiniowana. Użyj tej samej nazwy procedury w każdej deklaracji.  
  
2. Poprzedź słowo kluczowe `Sub` lub `Function` w każdej deklaracji za pomocą słowa kluczowego [overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) . Opcjonalnie możesz pominąć `Overloads` w deklaracjach, ale jeśli zostanie on uwzględniony w dowolnej deklaracji, należy uwzględnić ją w każdej deklaracji.  
  
3. Zgodnie z każdą instrukcją deklaracji Napisz kod procedury, aby obsłużyć konkretny przypadek, w którym wywoływany kod dostarcza argumenty pasujące do listy parametrów tej wersji. Nie trzeba testować, dla którego parametrów dostarczono kod wywołujący. Visual Basic przekazuje kontrolę do zgodnej wersji procedury.  
  
4. Zakończ każdą wersję procedury z instrukcją `End Sub` lub `End Function`, zgodnie z potrzebami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano procedurę `Sub`, aby opublikować transakcję względem salda klienta. Używa słowa kluczowego `Overloads`, aby zdefiniować dwie wersje procedury, jedną, która akceptuje klienta według nazwy i innych według numeru konta.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Kod wywołujący może uzyskać identyfikację klienta jako `String` lub `Integer`, a następnie użyć tej samej instrukcji wywoływania w obu przypadkach.  
  
 Aby uzyskać informacje na temat sposobu wywoływania tych wersji procedury `post`, zobacz [How to: calling a przeciążona procedura](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Upewnij się, że każda ze przeciążonych wersji ma taką samą nazwę procedury, ale inną listę parametrów.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
