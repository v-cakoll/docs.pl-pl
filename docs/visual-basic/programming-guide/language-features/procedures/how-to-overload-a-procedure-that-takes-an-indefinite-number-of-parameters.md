---
title: 'Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 047d566c13f03803d2e5c3bc6cce0db56df4a3f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345850"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)
Jeśli procedura zawiera parametr [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , nie można zdefiniować przeciążonej wersji pobierającej tablicę jednowymiarową dla tablicy parametrów. Aby uzyskać więcej informacji, zobacz "niejawne przeciążenia dla parametru ParamArray" w artykule dotyczącym [przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Aby przeciążyć procedurę, która przyjmuje zmienną liczbę parametrów  
  
1. Należy upewnić się, że procedura i wywoływanie logiki kodu z przeciążonych wersji nie przekracza z `ParamArray` parametru. Zobacz sekcję "overloads and ParamArrays" w artykule dotyczącym [przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
2. Określ, które liczby podanych wartości mają być akceptowane przez procedurę w zmiennej części listy parametrów. Może to obejmować przypadek braku wartości i może uwzględniać wielkość liter pojedynczej tablicy jednowymiarowej.  
  
3. Dla każdej akceptowalnej liczby podanych wartości Napisz `Sub` lub instrukcję deklaracji `Function`, która definiuje odpowiednią listę parametrów. Nie należy używać słowa kluczowego `Optional` ani `ParamArray` w tej przeciążonej wersji.  
  
4. W każdej deklaracji poprzedź słowo kluczowe `Sub` lub `Function` za pomocą słowa kluczowego [overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .  
  
5. Po każdej deklaracji Napisz kod procedury, który powinien zostać wykonany, gdy wywoływany kod zawiera wartości odpowiadające tej deklaracji listy parametrów.  
  
6. W razie potrzeby Zakończ każdą procedurę z instrukcją `End Sub` lub `End Function`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje procedurę zdefiniowaną za pomocą parametru [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , a następnie równoważnego zestawu przeciążonych procedur.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Nie można przeciążyć takiej procedury z listą parametrów, która przyjmuje jednowymiarową tablicę dla tablicy parametrów. Można jednak użyć podpisów innych niejawnych przeciążeń. Ilustruje to następujące deklaracje.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Kod w przeciążonych wersjach nie musi testować, czy kod wywołujący dostarczył jedną lub więcej wartości dla parametru `ParamArray`, czy tak, ile. Visual Basic przekazuje kontrolę do wersji zgodnej z listą argumentów wywołujących.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ponieważ procedura z parametrem `ParamArray` jest równoważna z zestawem przeciążonych wersji, nie można przeciążyć takiej procedury z listą parametrów odpowiadającą każdemu z tych niejawnych przeciążeń. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji. Jeśli zaakceptujesz tablicę parametrów, należy sprawdzić długość tablicy, do której przeszedł kod wywołujący, i wykonać odpowiednie czynności, jeśli jest zbyt duży dla aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
