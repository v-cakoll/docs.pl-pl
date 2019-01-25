---
title: 'Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)'
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
ms.openlocfilehash: 54a8a65db6e1f532cd21e36eeb5b98670efd4289
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506397"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)
Jeśli procedura ma [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru nie można zdefiniować przeciążoną wersją, biorąc Jednowymiarowa tablica dla tablicy parametrów. Aby uzyskać więcej informacji, zobacz "Niejawne przeciążenia dla parametru ParamArray" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Aby przeciążanie procedury, która przyjmuje zmienną liczbę parametrów  
  
1.  Upewnić się, że procedury i wywoływać metodę kod logiki korzyści z przeciążone wersje ponad `ParamArray` parametru. Zobacz "Przeciążenia i ParamArrays" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
2.  Ustal, które numery podane wartości procedura powinna obsługiwać w części zmiennej listy parametrów. Może to obejmować przypadku żadnej wartości i może zawierać przypadku pojedynczą tablicę jednowymiarową.  
  
3.  Dla każdego dopuszczalna liczba podanych wartości zapisu `Sub` lub `Function` instrukcji deklaracji, która definiuje odpowiednie listy parametrów. Nie używaj albo `Optional` lub `ParamArray` — słowo kluczowe w tej wersji przeciążona.  
  
4.  W każdym zgłoszeniu, należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.  
  
5.  Po każdym zgłoszeniu należy napisać kod procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza wartości odpowiadające liście parametrów tej deklaracji.  
  
6.  Zakończenie każdej procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zdefiniowane za pomocą procedury [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru, a następnie zbiór równoważny, procedur przeciążona.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Nie można przeciążyć procedury z listą parametrów, który przyjmuje tablicę jednowymiarową dla tablicy parametrów. Można jednak użyć podpisy niejawne przeładowania. Następujące deklaracje pokazują to.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Kod w przeciążone wersje nie trzeba sprawdzić, czy kod wywołujący podano jeden lub więcej wartości dla `ParamArray` parametr, lub jeśli tak, jak wiele. Visual Basic przekazuje sterowanie do wersji pasujących do wywoływania listy argumentów.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ponieważ procedury z `ParamArray` parametr jest równoważny z zestawem przeciążone wersje, nie mogą przeciążać takiej procedury z dowolnego z tych niejawne przeładowania odpowiadający listą parametrów. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze, gdy użytkownik poradzić sobie z tablicy, które mogą być duże przez czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrznych wydajności aplikacji. Jeśli akceptujesz tablicy parametrów, należy sprawdzić długość tablicy przekazany kod wywołujący i podejmie stosowne działania, jeśli jest zbyt duży dla aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: Wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
