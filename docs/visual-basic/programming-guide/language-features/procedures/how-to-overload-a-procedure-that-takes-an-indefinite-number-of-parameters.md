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
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387884"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)
Jeśli procedura zawiera parametr [ParamArray](../../../language-reference/modifiers/paramarray.md) , nie można zdefiniować przeciążonej wersji pobierającej tablicę jednowymiarową dla tablicy parametrów. Aby uzyskać więcej informacji, zobacz "niejawne przeciążenia dla parametru ParamArray" w artykule dotyczącym [przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Aby przeciążyć procedurę, która przyjmuje zmienną liczbę parametrów  
  
1. Należy upewnić się, że procedura i wywoływanie logiki kodu z przeciążonych wersji nie przekracza z `ParamArray` parametru. Zobacz sekcję "overloads and ParamArrays" w artykule dotyczącym [przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
2. Określ, które liczby podanych wartości mają być akceptowane przez procedurę w zmiennej części listy parametrów. Może to obejmować przypadek braku wartości i może uwzględniać wielkość liter pojedynczej tablicy jednowymiarowej.  
  
3. Dla każdej akceptowalnej liczby podanych wartości Napisz `Sub` instrukcję lub `Function` deklarację, która definiuje odpowiednią listę parametrów. Nie należy używać `Optional` `ParamArray` słowa kluczowego or w tej przeciążonej wersji.  
  
4. W każdej deklaracji poprzedź słowo kluczowe `Sub` or słowa `Function` kluczowego [overloads](../../../language-reference/modifiers/overloads.md) .  
  
5. Po każdej deklaracji Napisz kod procedury, który powinien zostać wykonany, gdy wywoływany kod zawiera wartości odpowiadające tej deklaracji listy parametrów.  
  
6. Przerwij każdą procedurę za pomocą `End Sub` instrukcji lub w `End Function` zależności od potrzeb.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje procedurę zdefiniowaną za pomocą parametru [ParamArray](../../../language-reference/modifiers/paramarray.md) , a następnie równoważnego zestawu przeciążonych procedur.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Nie można przeciążyć takiej procedury z listą parametrów, która przyjmuje jednowymiarową tablicę dla tablicy parametrów. Można jednak użyć podpisów innych niejawnych przeciążeń. Ilustruje to następujące deklaracje.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 Kod w przeciążonych wersjach nie musi testować, czy kod wywołujący dostarczył jedną lub więcej wartości `ParamArray` parametru, czy tak, ile tak. Visual Basic przekazuje kontrolę do wersji zgodnej z listą argumentów wywołujących.  
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Ponieważ procedura z `ParamArray` parametrem jest równoważna z zestawem przeciążonych wersji, nie można przeciążyć takiej procedury z listą parametrów odpowiadającą każdemu z tych niejawnych przeciążeń. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji. Jeśli zaakceptujesz tablicę parametrów, należy sprawdzić długość tablicy, do której przeszedł kod wywołujący, i wykonać odpowiednie czynności, jeśli jest zbyt duży dla aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Parameter — Tablice](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
