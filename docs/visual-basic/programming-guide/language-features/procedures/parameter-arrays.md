---
title: "Parameter — Tablice (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a>Parameter — Tablice (Visual Basic)
Zazwyczaj nie można wywołać procedury z więcej argumentów niż określa deklaracji procedury. Jeśli potrzebujesz nieokreśloną liczbę argumentów można zadeklarować *tablicy parametrów*, dzięki czemu procedury zaakceptować tablicy wartości parametru. Nie trzeba znać liczba elementów w tablicy parametrów podczas definiowania procedury. Rozmiar tablicy jest ustalana indywidualnie przy każdym wywołaniu procedury.  
  
## <a name="declaring-a-paramarray"></a>Deklarowanie ParamArray  
 Możesz użyć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) — słowo kluczowe do oznaczania tablicy parametrów na liście parametrów. Mają zastosowanie następujące zasady:  
  
-   Procedurę można zdefiniować tylko jedną tablicy parametrów, a musi być ostatnim parametrem Definicja procedury.  
  
-   Tablica parametrów muszą być przekazywane przez wartość. Jest dobrą praktyką jawnie włączyć programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) — słowo kluczowe w definicji procedury.  
  
-   Tablica parametrów jest automatycznie opcjonalne. Wartość domyślną jest pusta tablica jednowymiarowa typ elementu tablicy parametrów.  
  
-   Wszystkie parametry poprzedzających Tablica parametrów musi być wymagane. Tablica parametrów musi być tylko opcjonalny parametr.  
  
## <a name="calling-a-paramarray"></a>Wywoływanie ParamArray  
 Po wywołaniu procedury, która definiuje tablicy parametrów, możesz podać argument w jednym z następujących sposobów:  
  
-   Nothing — to znaczy, można pominąć [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumentu. W takim przypadku pusta tablica jest przekazywany do procedury. Można również przekazać [nic](../../../../visual-basic/language-reference/nothing.md) — słowo kluczowe, w tym samym celu.  
  
-   Lista dowolnej liczby argumentów rozdzielonych przecinkami. Należy umożliwiają niejawnej konwersji na typ danych argumentu `ParamArray` typ elementu.  
  
-   Tablica z tego samego typu elementu jako typ elementu tablicy parametrów.  
  
 We wszystkich przypadkach kodu w ramach procedury traktuje tablicy parametrów jako tablicą jednowymiarową z elementami typu danych jako `ParamArray` — typ danych.  
  
> [!IMPORTANT]
>  Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji. Jeśli akceptujesz tablicy parametrów, należy przetestować rozmiaru tablicy, która kod wywołujący przekazana do niej. Jeśli jest ona za duża dla aplikacji, należy podjąć odpowiednie kroki. Aby uzyskać więcej informacji, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie definiuje i wywołuje funkcję `calcSum`. `ParamArray` Modyfikator parametru `args` włącza funkcję zaakceptować zmienną liczbę argumentów.  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 Poniższy przykład definiuje procedurę z tablicą parametrów, a następnie generuje wartości elementów tablicy przekazany do tablicy parametrów.  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Opcjonalne](../../../../visual-basic/language-reference/modifiers/optional.md)
