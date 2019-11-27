---
title: 'Porady: przeciążanie procedury wykorzystującej parametry opcjonalne'
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
ms.openlocfilehash: 4d31980e4b968cff274091ba4f307dffddab1100
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350863"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)
Jeśli procedura zawiera co najmniej jeden parametr [opcjonalny](../../../../visual-basic/language-reference/modifiers/optional.md) , nie można zdefiniować przeciążonej wersji zgodnej z żadnym z jego niejawnego przeciążenia. Aby uzyskać więcej informacji, zobacz "niejawne przeciążenia dla parametrów opcjonalnych" w [kwestiach dotyczących przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden opcjonalny parametr  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Aby przeciążyć procedurę, która przyjmuje jeden parametr opcjonalny  
  
1. Napisz instrukcję `Sub` lub `Function` deklaracji, która zawiera opcjonalny parametr na liście parametrów. Nie należy używać słowa kluczowego `Optional` w tej przeciążonej wersji.  
  
2. Poprzedź słowo kluczowe `Sub` lub `Function` za pomocą słowa kluczowego [overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .  
  
3. Napisz kod procedury, który powinien zostać wykonany, gdy wywoływany kod dostarcza opcjonalnego argumentu.  
  
4. W razie potrzeby Zakończ procedurę z użyciem instrukcji `End Sub` lub `End Function`.  
  
5. Napisz drugą instrukcję deklaracji, która jest identyczna z pierwszą deklaracją, z tą różnicą, że nie zawiera parametru opcjonalnego na liście parametrów.  
  
6. Napisz kod procedury, który powinien zostać wykonany, gdy wywołujący kod nie poda opcjonalnego argumentu. W razie potrzeby Zakończ procedurę z użyciem instrukcji `End Sub` lub `End Function`.  
  
     Poniższy przykład pokazuje procedurę zdefiniowaną za pomocą opcjonalnego parametru, równoważnego zestawu dwóch przeciążonych procedur, a wreszcie przykłady zarówno dla nieprawidłowych, jak i prawidłowych wersji przeciążonych.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Wiele parametrów opcjonalnych  
 W przypadku procedury z więcej niż jednym opcjonalnym parametrem zwykle wymagane są więcej niż dwie przeciążone wersje. Na przykład jeśli istnieją dwa parametry opcjonalne, a kod wywołujący może dostarczyć lub pominąć każdy z nich niezależnie, potrzebne są cztery przeciążone wersje, jeden dla każdej możliwej kombinacji dostarczonych argumentów.  
  
 Wraz ze wzrostem liczby parametrów opcjonalnych zwiększa się złożoność przeciążenia. Jeśli niektóre kombinacje podanych argumentów nie są akceptowalne, dla N opcjonalnych parametrów wymagane są 2 ^ N przeciążone wersje. W zależności od charakteru procedury, może się okazać, że przejrzystość logiki usprawiedliwia dodatkowy nakład pracy w celu zdefiniowania wszystkich przeciążonych wersji.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Aby przeciążyć procedurę, która przyjmuje więcej niż jeden parametr opcjonalny  
  
1. Ustal, które kombinacje podanych argumentów opcjonalnych są akceptowalne dla logiki procedury. Nieakceptowalna kombinacja może wystąpić, jeśli jeden opcjonalny parametr zależy od innego. Na przykład jeśli jeden parametr akceptuje nazwisko osoby i inny akceptuje wiek osoby, kombinację argumentów dostarczających wiek, ale pomijając nazwę, nie można jej zaakceptować.  
  
2. Dla każdej akceptowalnej kombinacji podanych argumentów opcjonalnych Napisz instrukcję `Sub` lub `Function` deklaracji, która definiuje odpowiednią listę parametrów. Nie należy używać słowa kluczowego `Optional`.  
  
3. W każdej deklaracji poprzedź słowo kluczowe `Sub` lub `Function` za pomocą słowa kluczowego [overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .  
  
4. Po każdej deklaracji Napisz kod procedury, który powinien zostać wykonany, gdy wywołujący kod dostarcza listę argumentów odpowiadającą tej deklaracji listy parametrów.  
  
5. W razie potrzeby Zakończ każdą procedurę z instrukcją `End Sub` lub `End Function`.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
