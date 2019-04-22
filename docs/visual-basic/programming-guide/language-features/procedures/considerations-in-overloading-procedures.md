---
title: Zagadnienia dotyczące przeciążania procedur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: f14cc28960af28530bda9a78c1309dea10c18b8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815599"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Zagadnienia dotyczące przeciążania procedur (Visual Basic)
Możesz przeciążanie procedury, należy użyć innego *podpisu* dla każdej wersji przeciążona. Zwykle oznacza to, że każda wersja należy określić inną listą parametrów. Aby uzyskać więcej informacji, zobacz "Inny podpis" w [przeciążanie procedury](./procedure-overloading.md).  
  
 Możesz doprowadzić do przeciążenia `Function` procedury z `Sub` procedury i na odwrót, pod warunkiem mają różnych podpisów. Dwa przeciążenia nie różnią się tylko jeden z nich nie zwraca wartości, a drugi nie.  
  
 Możesz doprowadzić do przeciążenia właściwości taki sam sposób, przeciążanie procedury i z ograniczeniami. Jednak nie mogą przeciążać procedury z właściwością lub na odwrót.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternatywy dla przeciążone wersje  
 Czasami masz alternatyw przeciążone wersje, zwłaszcza w przypadku obecności argumentów jest opcjonalne, lub ich liczba jest zmienna.  
  
 Należy pamiętać, że opcjonalne argumenty nie są zawsze obsługiwane przez wszystkie języki i tablice parametrów są ograniczone do języka Visual Basic. Jeśli piszesz procedury, która może być wywoływana z kodu napisanego w dowolnym z kilku różnych języków, przeciążone wersje oferty największą elastyczność.  
  
### <a name="overloads-and-optional-arguments"></a>Przeciążenia i argumenty opcjonalne.  
 Gdy kod wywołujący może opcjonalnie podaj lub Pomiń jeden lub więcej argumentów, można zdefiniować wiele przeciążone wersje, lub korzystanie z parametrów opcjonalnych.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kiedy należy używać przeciążone wersje  
 Można rozważyć Definiowanie szereg przeciążone wersje w następujących przypadkach:  
  
-   Logiki w kodzie procedury różni się znacznie w zależności od tego, czy kod wywołujący dostarcza opcjonalny argument, czy nie.  
  
-   Kod procedury niezawodne nie można sprawdzić, czy kod wywołujący udostępnił opcjonalny argument. Jest to możliwe, na przykład, jeśli ma nie kandydatem dla domyślną wartość, która kod wywołujący nie należy się spodziewać umożliwiają określanie wartości.  
  
#### <a name="when-to-use-optional-parameters"></a>Kiedy należy używać parametrów opcjonalnych  
 Można wybrać co najmniej jeden parametr opcjonalny w następujących przypadkach:  
  
-   Tylko niezbędne czynności podczas wywoływania kodu nie dostarcza opcjonalny argument jest ustawić parametr na wartość domyślną. W takiej sytuacji kod procedury może być mniej skomplikowany, jeśli zdefiniujesz z co najmniej jedną wersję `Optional` parametrów.  
  
 Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Przeciążenia i ParamArrays  
 Gdy kod wywołujący może przekazać zmienną liczbę argumentów, można zdefiniować wiele przeciążone wersje, lub użyj tablicy parametrów.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kiedy należy używać przeciążone wersje  
 Można rozważyć Definiowanie szereg przeciążone wersje w następujących przypadkach:  
  
-   Wiesz, że kod wywołujący nigdy nie przekazuje ponad niewielka liczba wartości do tablicy parametrów.  
  
-   Logiki w kodzie procedura jest znacząco różne w zależności od tego, jak wiele wartości, które przekazuje kodu wywołującego.  
  
-   Kod wywołujący można przekazać wartości różnych typów danych.  
  
#### <a name="when-to-use-a-parameter-array"></a>Kiedy należy używać tablicy parametrów  
 Sięganie po `ParamArray` parametru w następujących przypadkach:  
  
-   Nie jesteś w stanie przewidzieć liczbę wartości, kod wywołujący można przekazać do tablicy parametrów i może być duża liczba.  
  
-   Logika procedury pozwala na przechodzenie przez wszystkie wartości, które przekazuje kodu wywołującego, wykonywanie zasadniczo tej samej operacji na każdej wartości.  
  
 Aby uzyskać więcej informacji, zobacz [Parameter — tablice](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Niejawne przeładowania dla parametrów opcjonalnych  
 Procedury z [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametr jest równoważny dwóch procedur przeciążona, jeden z opcjonalnym parametrem i jedną bez niego. Nie mogą przeciążać takiej procedury z listą parametrów odpowiadający jedną z tych wersji. Następujące deklaracje pokazują to.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 Procedury z więcej niż jeden parametr opcjonalny istnieje zestaw niejawne przeładowania, dotarły przez logikę, podobnie jak w poprzednim przykładzie.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Niejawne przeładowania dla ParamArray parametru  
 Kompilator traktuje procedury z [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru, aby mieć nieograniczoną liczbę przeciążeń, różniące się od siebie nawzajem co kod wywołujący przekazuje do tablicy parametrów w następujący sposób:  
  
-   Gdy kod wywołujący nie podać argument do jednego przeciążenia `ParamArray`  
  
-   Gdy kod wywołujący dostarcza Jednowymiarowa tablica jednego przeciążenia `ParamArray` typ elementu  
  
-   Dla każdego dodatnią liczbą całkowitą jednego przeciążenia dla gdy kod wywołujący dostarcza tę liczbę argumentów, każdy z `ParamArray` typ elementu  
  
 Następujące deklaracje pokazują te niejawne przeładowania.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Nie można przeciążyć procedury z listą parametrów, który przyjmuje tablicę jednowymiarową dla tablicy parametrów. Można jednak użyć podpisy niejawne przeładowania. Następujące deklaracje pokazują to.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programowanie nietypowane jako alternatywę do przeciążania  
 Jeśli chcesz zezwolić na kod wywołujący, aby przekazać różne typy danych do parametru alternatywnym podejściem jest programowanie nietypowane. Można ustawić typ sprawdzania przełącznik `Off` z oboma [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) lub [/optionstrict —](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) — opcja kompilatora. Następnie trzeba zadeklarować typ danych parametru. Jednak to podejście ma następujące wady w porównaniu do przeciążania:  
  
-   Programowanie nietypowane generuje kod, mniej wydajne wykonywanie.  
  
-   Procedury należy przetestować dla każdego typu danych, które przewiduje, przekazywana.  
  
-   Kompilator nie zasygnalizować błąd, jeśli kod wywołujący przekazuje typ danych, który nie obsługuje procedury.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: Wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
