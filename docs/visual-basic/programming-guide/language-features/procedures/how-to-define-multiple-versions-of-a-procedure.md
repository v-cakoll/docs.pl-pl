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
ms.openlocfilehash: 870a18dbf3a7e28b7d7b612e853beeec6908cf6f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387936"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Porady: definiowanie wielu wersji procedury (Visual Basic)
Można zdefiniować procedurę w wielu wersjach przez *przekazanie* jej przy użyciu tej samej nazwy, ale innej listy parametrów dla każdej wersji. Przeciążanie polega na zdefiniowaniu kilku ściśle powiązanych wersji procedury bez konieczności odróżnienia ich według nazwy.  
  
 Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Aby zdefiniować wiele wersji procedury  
  
1. Napisz `Sub` instrukcję lub `Function` deklaracji dla każdej wersji procedury, która ma zostać zdefiniowana. Użyj tej samej nazwy procedury w każdej deklaracji.  
  
2. Poprzedź `Sub` `Function` słowo kluczowe or w każdej deklaracji za pomocą słowa kluczowego [overloads](../../../language-reference/modifiers/overloads.md) . Opcjonalnie możesz pominąć `Overloads` deklaracje, ale jeśli zostanie on uwzględniony w dowolnej deklaracji, należy uwzględnić ją w każdej deklaracji.  
  
3. Zgodnie z każdą instrukcją deklaracji Napisz kod procedury, aby obsłużyć konkretny przypadek, w którym wywoływany kod dostarcza argumenty pasujące do listy parametrów tej wersji. Nie trzeba testować, dla którego parametrów dostarczono kod wywołujący. Visual Basic przekazuje kontrolę do zgodnej wersji procedury.  
  
4. Przerwij każdą wersję procedury z `End Sub` instrukcją lub, `End Function` zgodnie z potrzebami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `Sub` procedurę publikowania transakcji na podstawie salda klienta. Używa `Overloads` słowa kluczowego, aby zdefiniować dwie wersje procedury, jedną, która akceptuje klienta według nazwy i innych według numeru konta.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Kod wywołujący może uzyskać identyfikację klienta jako `String` lub `Integer` , a następnie użyć tej samej instrukcji wywołującej w obu przypadkach.  
  
 Aby uzyskać informacje na temat sposobu wywoływania tych wersji `post` procedury, zobacz [How to: calling a przeciążona procedura](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Upewnij się, że każda ze przeciążonych wersji ma taką samą nazwę procedury, ale inną listę parametrów.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
