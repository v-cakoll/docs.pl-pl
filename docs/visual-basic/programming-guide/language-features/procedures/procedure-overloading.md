---
title: "Przeciążanie procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65fd5a6763752c616f13891bfa5acabff6115d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-overloading-visual-basic"></a>Przeciążanie procedury (Visual Basic)
*Przeciążanie* procedury oznacza Definiowanie wielu wersji przy użyciu tej samej nazwie, ale listy różnych parametrów. Przeciążanie służy do definiowania kilka wersji blisko związane procedury bez konieczności odróżnić je według nazwy. W tym celu zróżnicowanie listy parametrów.  
  
## <a name="overloading-rules"></a>Przeciążanie reguły  
 Przeciążanie procedury, mają zastosowanie następujące reguły:  
  
-   **Tej samej nazwy**. Każdej zastąpionej wersji należy użyć tej samej nazwy procedury.  
  
-   **Inny podpis**. Każda wersja przeciążone musi różnić się od innych wersji przeciążone w co najmniej jeden z następujących aspektach:  
  
    -   Liczba parametrów  
  
    -   Kolejność parametrów  
  
    -   Typy danych parametrów  
  
    -   Liczba parametrów typu (dla procedury ogólny)  
  
    -   Zwracany typ (tylko dla operatora konwersji)  
  
     Wraz z nazwą procedury poprzednie elementy są nazywane *podpisu* procedury. Po wywołaniu procedury przeciążenia kompilator używa podpis do sprawdzenia, czy wywołanie poprawnie odpowiada definicji.  
  
-   **Elementy nie jest częścią podpisu**. Procedury nie mogą przeciążać bez zróżnicowanie podpisu. W szczególności nie mogą przeciążać procedury przez zróżnicowanie tylko jeden lub więcej z następujących elementów:  
  
    -   Słowa kluczowe modyfikator procedury, takich jak `Public`, `Shared`, i`Static`  
  
    -   Parametr lub typ nazwy parametrów  
  
    -   Ograniczenia parametru typu (dla procedury ogólny)  
  
    -   Słowa kluczowe modyfikator parametrów, takich jak `ByRef` i`Optional`  
  
    -   Określa, czy wartość jest zwracana  
  
    -   Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)  
  
     Elementy na liście powyżej nie są częścią podpisu. Mimo że nie można użyć ich do rozróżniania zastąpionej wersji, można je różnią przeciążone wersje, które są właściwie zróżnicowane przez ich podpisów.  
  
-   **Późnym wiązaniem argumenty**. Jeśli zamierzasz przekazać późne zmiennej obiektu związanego z wersją przeciążona, należy zadeklarować jako odpowiedni parametr <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Wielu wersji procedury  
 Załóżmy, że pisania `Sub` procedury można opublikować transakcji przed Saldo klienta i ma być możliwe do odwoływania się do klienta według nazwy lub numeru konta. Aby to umożliwić, możesz zdefiniować dwa różne `Sub` procedur, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a>Wersje przeciążone  
 Alternatywą jest nazwa jednej procedury przeciążenia. Można użyć [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe, aby zdefiniować wersji procedury na wszystkich listach parametrem w następujący sposób:  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a>Dodatkowe przeciążenia  
 Jeśli chcesz także zaakceptować kwota transakcji, albo `Decimal` lub `Single`, można dodatkowo przeciążenia `post` do obsługi tej zmiany. Jeśli tak, to nie wszystkie przeciążenia w poprzednim przykładzie należałoby cztery `Sub` procedur, wszystkie o takiej samej nazwie, ale z czterech różnych podpisów.  
  
## <a name="advantages-of-overloading"></a>Korzyści wynikające z przeciążenia  
 Zaletą przeciążanie procedury jest elastyczność wywołania. Do użycia `post` procedury zadeklarowany w poprzednim przykładzie kodu wywołującego, można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie wywołaj tę samą procedurę w każdym przypadku. Poniższy przykład przedstawia to:  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Porady: wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)  
 [Porady: przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)  
 [Przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
