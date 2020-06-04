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
ms.openlocfilehash: 9ae6818b1e03ccd00ed554e98690e02ffa45de99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387845"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)
Jeśli procedura zawiera co najmniej jeden parametr [opcjonalny](../../../language-reference/modifiers/optional.md) , nie można zdefiniować przeciążonej wersji zgodnej z żadnym z jego niejawnego przeciążenia. Aby uzyskać więcej informacji, zobacz "niejawne przeciążenia dla parametrów opcjonalnych" w [kwestiach dotyczących przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Jeden opcjonalny parametr  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Aby przeciążyć procedurę, która przyjmuje jeden parametr opcjonalny  
  
1. Napisz `Sub` instrukcję lub `Function` deklaracji, która zawiera opcjonalny parametr na liście parametrów. Nie należy używać `Optional` słowa kluczowego w tej przeciążonej wersji.  
  
2. Poprzedź `Sub` słowo kluczowe or `Function` za pomocą słowa kluczowego [overloads](../../../language-reference/modifiers/overloads.md) .  
  
3. Napisz kod procedury, który powinien zostać wykonany, gdy wywoływany kod dostarcza opcjonalnego argumentu.  
  
4. Zakończ procedurę z `End Sub` `End Function` instrukcją lub, zgodnie z potrzebami.  
  
5. Napisz drugą instrukcję deklaracji, która jest identyczna z pierwszą deklaracją, z tą różnicą, że nie zawiera parametru opcjonalnego na liście parametrów.  
  
6. Napisz kod procedury, który powinien zostać wykonany, gdy wywołujący kod nie poda opcjonalnego argumentu. Zakończ procedurę z `End Sub` `End Function` instrukcją lub, zgodnie z potrzebami.  
  
     Poniższy przykład pokazuje procedurę zdefiniowaną za pomocą opcjonalnego parametru, równoważnego zestawu dwóch przeciążonych procedur, a wreszcie przykłady zarówno dla nieprawidłowych, jak i prawidłowych wersji przeciążonych.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Wiele parametrów opcjonalnych  
 W przypadku procedury z więcej niż jednym opcjonalnym parametrem zwykle wymagane są więcej niż dwie przeciążone wersje. Na przykład jeśli istnieją dwa parametry opcjonalne, a kod wywołujący może dostarczyć lub pominąć każdy z nich niezależnie, potrzebne są cztery przeciążone wersje, jeden dla każdej możliwej kombinacji dostarczonych argumentów.  
  
 Wraz ze wzrostem liczby parametrów opcjonalnych zwiększa się złożoność przeciążenia. Jeśli niektóre kombinacje podanych argumentów nie są akceptowalne, dla N opcjonalnych parametrów wymagane są 2 ^ N przeciążone wersje. W zależności od charakteru procedury, może się okazać, że przejrzystość logiki usprawiedliwia dodatkowy nakład pracy w celu zdefiniowania wszystkich przeciążonych wersji.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Aby przeciążyć procedurę, która przyjmuje więcej niż jeden parametr opcjonalny  
  
1. Ustal, które kombinacje podanych argumentów opcjonalnych są akceptowalne dla logiki procedury. Nieakceptowalna kombinacja może wystąpić, jeśli jeden opcjonalny parametr zależy od innego. Na przykład jeśli jeden parametr akceptuje nazwisko osoby i inny akceptuje wiek osoby, kombinację argumentów dostarczających wiek, ale pomijając nazwę, nie można jej zaakceptować.  
  
2. Dla każdej akceptowalnej kombinacji podanych argumentów opcjonalnych Napisz `Sub` `Function` instrukcję lub deklarację, która definiuje odpowiednią listę parametrów. Nie należy używać `Optional` słowa kluczowego.  
  
3. W każdej deklaracji poprzedź słowo kluczowe `Sub` or słowa `Function` kluczowego [overloads](../../../language-reference/modifiers/overloads.md) .  
  
4. Po każdej deklaracji Napisz kod procedury, który powinien zostać wykonany, gdy wywołujący kod dostarcza listę argumentów odpowiadającą tej deklaracji listy parametrów.  
  
5. Przerwij każdą procedurę za pomocą `End Sub` instrukcji lub w `End Function` zależności od potrzeb.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Parameter — Tablice](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
