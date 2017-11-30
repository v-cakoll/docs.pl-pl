---
title: "Zagadnienia dotyczące przeciążania procedur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c9a9a4759d4ec2dd87778c49c4fd82a08c081a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Zagadnienia dotyczące przeciążania procedur (Visual Basic)
Przeciążanie procedury, należy używać innej *podpisu* dla każdej wersji przeciążona. Zwykle oznacza to, że każda wersja należy określić inną listą parametrów. Aby uzyskać więcej informacji, zobacz "Inny podpis" w [przeciążanie procedury](./procedure-overloading.md).  
  
 Można przeciążać `Function` procedury z `Sub` procedury i na odwrót, pod warunkiem mają różnych podpisów. Dwa przeciążenia nie różnią się tylko jedna ma wartość zwracaną, a drugi nie.  
  
 Można przeciążać właściwości tak samo przeciążanie procedury i z ograniczeniami. Jednak nie mogą przeciążać procedury z właściwością lub na odwrót.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternatywy dla wersji przeciążone  
 Czasami masz alternatywy dla przeciążonej wersje, zwłaszcza w przypadku obecności argumentów jest opcjonalny, lub ich numer zmiennej.  
  
 Należy pamiętać, że argumenty opcjonalne nie są zawsze obsługiwane przez wszystkie języki, a tablice parametrów są ograniczone do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Jeśli piszesz procedury, która może być wywoływana z kodu napisanego w jednym z kilku różnych języków przeciążony oferta wersji największą elastyczność.  
  
### <a name="overloads-and-optional-arguments"></a>Przeciążenia i argumentów opcjonalnych  
 Kod wywołujący może opcjonalnie podaj lub pominąć jeden lub więcej argumentów, można zdefiniować wiele wersji przeciążone lub opcjonalne parametry.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kiedy należy używać przeciążonej wersji  
 Można rozważyć możliwość definiowania serii zastąpionej wersji w następujących przypadkach:  
  
-   Logikę w kodzie procedury znacznie różni się w zależności od tego, czy kod wywołujący dostarcza opcjonalny argument lub nie.  
  
-   Kod procedury niezawodnie nie może sprawdzić, czy kod wywołujący udostępnił opcjonalny argument. Jest to możliwe, na przykład, jeśli nie jest domyślna wartość, która nie kandydatem kod wywołujący nie należy się spodziewać umożliwiają określanie wartości.  
  
#### <a name="when-to-use-optional-parameters"></a>Kiedy należy używać następujące parametry opcjonalne  
 Można wybrać co najmniej jeden parametr opcjonalny w następujących przypadkach:  
  
-   Tylko niezbędne czynności podczas kod wywołujący nie dostarcza opcjonalny argument jest ustawić parametr na wartość domyślną. W takim przypadku kod procedura może być mniej skomplikowane, w przypadku definiowania jednej wersji co najmniej jednym `Optional` parametrów.  
  
 Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Przeciążenia i ParamArrays  
 Gdy kod wywołujący może przekazać zmienna liczba argumentów, można zdefiniować wiele wersji przeciążone lub użyj tablicy parametrów.  
  
#### <a name="when-to-use-overloaded-versions"></a>Kiedy należy używać przeciążonej wersji  
 Można rozważyć możliwość definiowania serii zastąpionej wersji w następujących przypadkach:  
  
-   Wiadomo, że kod wywołujący nigdy nie przekazuje więcej niż małej liczby wartości do tablicy parametrów.  
  
-   Logikę w kodzie procedury znacznie różni się w zależności od tego, ile wartości przekazuje kod wywołujący.  
  
-   Kod wywołujący może przekazać wartości różnych typów danych.  
  
#### <a name="when-to-use-a-parameter-array"></a>Kiedy należy używać tablicy parametrów  
 Czy można lepiej obsłużone przez `ParamArray` parametru w następujących przypadkach:  
  
-   Nie jest możliwe do prognozowania wartości ile kod wywołujący może przekazać do tablicy parametrów i może być wiele.  
  
-   Logika procedury pozwala na przechodzenie przez wszystkie wartości przekazuje kodu wywołującego, wykonywanie zasadniczo tej samej operacji w każdej wartości.  
  
 Aby uzyskać więcej informacji, zobacz [tablice parametrów](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Niejawne przeładowania dla następujące parametry opcjonalne  
 Procedury z [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametru jest odpowiednikiem dwie procedury przeciążenia, jeden z opcjonalnym parametrem i drugi bez niego. Nie można przeciążyć takiej procedury z listą parametrów odpowiadający jednego z tych. Następujące deklaracje ilustrację.  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Procedury z więcej niż jeden parametr opcjonalny jest zestaw niejawne przeładowania przez logikę, podobnie jak w poprzednim przykładzie.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Niejawne przeładowania dla parametru ParamArray  
 Kompilator uwzględnia procedury z [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru nieograniczoną liczbę przeciążenia, różniące się od siebie co kod wywołujący przekazuje do tablicy parametrów w następujący sposób:  
  
-   Przeciążeniami dla gdy kod wywołujący nie dostarcza argument`ParamArray`  
  
-   Przeciążeniami dla podczas wywoływania kodu dostarcza Jednowymiarowa tablica `ParamArray` typ elementu  
  
-   Dla każdego dodatnią liczbą całkowitą, jeden przeciążenia dla gdy kod wywołujący dostarcza tej liczby argumentów, każdy z `ParamArray` typ elementu  
  
 Następujące deklaracje ilustrują te niejawne przeładowania.  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Nie można przeciążyć procedury z listą parametrów pobierającej tablicą jednowymiarową dla tablicy parametrów. Można jednak użyć podpisy niejawne przeładowania. Następujące deklaracje ilustrację.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Alternatywą wobec przeładowanie programowanie Nietypowane  
 Jeśli chcesz zezwolić kod wywołujący do przekazania do parametru różne typy danych, alternatywne podejście jest nietypowane. Można ustawić typ sprawdzania przełącznik `Off` przy użyciu jednej [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) lub [/optionstrict —](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) — opcja kompilatora. Następnie trzeba zadeklarować typ danych parametru. Jednak ta metoda ma następujące wady w porównaniu do przeciążania:  
  
-   Programowanie nietypowane tworzy mniej wydajne wykonywania kodu.  
  
-   Dla każdego typu danych oszacowano, przekazywany jest przetestowanie procedury.  
  
-   Kompilator nie może sygnał wystąpił błąd, jeśli kod wywołujący przekazuje procedura obsługuje tylko typ danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Procedury rozwiązywania problemów](./troubleshooting-procedures.md)  
 [Porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Porady: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)  
 [Porady: przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)  
 [Przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md)
