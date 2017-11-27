---
title: "Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 37d5b47f06bad1c2a8871168c5642663aedcccf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)
Jeśli procedura ma [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, nie można zdefiniować przeciążonego wersji biorąc tablicą jednowymiarową dla tablicy parametrów. Aby uzyskać więcej informacji, zobacz "Niejawne Overloads dla parametru ParamArray" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Aby przeciążanie procedury wykorzystującej zmienną liczbę parametrów  
  
1.  Upewnić się, że procedura i wywoływania kodu logiki korzyści z przeciążone wersje więcej niż `ParamArray` parametru. Zobacz "Przeciążenia i ParamArrays" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
2.  Ustal, które numery podane wartości procedura powinna obsługiwać w części zmiennej listy parametrów. Może to być case o wartości i może zawierać przypadku tablicą jednowymiarową.  
  
3.  Dla każdego dopuszczalne liczba podanych wartości zapisu `Sub` lub `Function` instrukcji deklaracji, który definiuje na odpowiedniej liście parametrów. Nie używaj albo `Optional` lub `ParamArray` — słowo kluczowe w tej wersji przeciążona.  
  
4.  W każdej deklaracji poprzedzać `Sub` lub `Function` — słowo kluczowe z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.  
  
5.  Po każdej deklaracji pisania kodu procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza wartości odpowiadających listy parametrów tej deklaracji.  
  
6.  Zakończenie każdej procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono procedurę zdefiniowane z [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, a następnie równoważne zbiór procedury przeciążenia.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Nie można przeciążyć procedury z listą parametrów pobierającej tablicą jednowymiarową dla tablicy parametrów. Można jednak użyć podpisy niejawne przeładowania. Następujące deklaracje ilustrację.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Kod w wersjach przeciążone nie ma do sprawdzenia, czy kod wywołujący dostarczonych wartości co najmniej jeden `ParamArray` parametr, lub jeśli tak, jak wiele. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Formant przekazuje do wersji pasujących do wywoływania listy argumentów.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ponieważ procedura o `ParamArray` parametru jest odpowiednikiem zestaw zastąpionej wersji, nie mogą przeciążać takiej procedury z listą parametrów odpowiadający żadnego z tych niejawne przeładowania. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji. Akceptujesz tablicy parametrów, należy przetestować długości tablicy przekazywania kod wywołujący i podejmij odpowiednie kroki, jeśli jest ona za duża dla aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Procedury rozwiązywania problemów](./troubleshooting-procedures.md)  
 [Porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Porady: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)  
 [Porady: przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)
