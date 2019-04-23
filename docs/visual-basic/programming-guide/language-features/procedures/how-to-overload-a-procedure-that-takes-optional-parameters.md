---
title: 'Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 58c52a7d73efbd96d772dd85d6bf2c9084fb1241
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320234"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)
Jeśli procedura ma co najmniej jeden [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametrów, nie można zdefiniować przeciążoną wersją, dowolny z jej przeciążeń niejawne dopasowania. Aby uzyskać więcej informacji, zobacz "Niejawne przeciążenia dla opcjonalne parametry" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden parametr opcjonalny  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Aby przeciążanie procedury, która przyjmuje jeden parametr opcjonalny  
  
1. Zapis `Sub` lub `Function` instrukcji deklaracji, która zawiera parametr opcjonalny na liście parametrów. Nie używaj `Optional` — słowo kluczowe w tej wersji przeciążona.  
  
2. Należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.  
  
3. Napisz kod procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza opcjonalny argument.  
  
4. Zakończenie procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.  
  
5. Napisz drugiej instrukcji deklaracji, która jest taka sama jak pierwszej deklaracji, z tą różnicą, że nie ma opcjonalnego parametru na liście parametrów.  
  
6. Napisz kod procedury, który powinien zostać wykonany, gdy kod wywołujący nie dostarcza opcjonalny argument. Zakończenie procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.  
  
     Poniższy przykład pokazuje zdefiniowane z opcjonalnym parametrem, równoważne zbiór dwie procedury przeciążone, a na końcu przykłady nieprawidłowych i prawidłowe przeciążone wersje procedury.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Wiele parametrów opcjonalnych  
 Procedury z więcej niż jeden parametr opcjonalny zwykle wymaga więcej niż dwie przeciążone wersje. Na przykład jeśli istnieją dwa parametry opcjonalne, a kod wywołujący może dostarczyć lub Pomiń każdej z nich niezależnie od innych, należy cztery przeciążone wersje: jeden dla każdej możliwej kombinacji podanych argumentów.  
  
 W miarę zwiększania liczby parametrów opcjonalnych zwiększa złożonością przeciążenia. Chyba że niektóre kombinacje przekazanych argumentów nie są dozwolone, następujące parametry opcjonalne N na potrzeby należy 2 ^ N przeciążone wersje. W zależności od charakteru procedura może się okazać, że w celu uściślenia logiki uzasadnia dodatkowego wysiłku definiowania przeciążone wersje.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Aby przeciążanie procedury wykorzystującej więcej niż jeden parametr opcjonalny  
  
1. Ustal, kombinacje podane argumenty opcjonalne są akceptowane przez logikę procedury. Można zaakceptować połączenie może wystąpić, jeśli jeden parametr opcjonalny jest zależny od innego. Na przykład jeden parametr akceptuje współmałżonka nazwę i inny akceptuje współmałżonka wiek, kombinacja argumentów, podając wiek, ale pomijając nazwę jest nie do przyjęcia.  
  
2. Dla każdej kombinacji dopuszczalne podanych argumentów opcjonalnych zapisu `Sub` lub `Function` instrukcji deklaracji, która definiuje odpowiednie listy parametrów. Nie używaj `Optional` — słowo kluczowe.  
  
3. W każdym zgłoszeniu, należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.  
  
4. Po każdym zgłoszeniu należy napisać kod procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza listy argumentów odpowiadający tej deklaracji listy parametrów.  
  
5. Zakończenie każdej procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: Wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
