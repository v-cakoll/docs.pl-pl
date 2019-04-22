---
title: Przeciążanie procedury (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 6e8d1fa72c60c4fa3d2237ad24c2d1b4891a7bf2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828241"
---
# <a name="procedure-overloading-visual-basic"></a>Przeciążanie procedury (Visual Basic)
*Przeciążanie* procedury oznacza zdefiniowaniem go w wielu wersjach, przy użyciu takiej samej nazwie, ale listy różnych parametrów. Przeciążanie ma na celu zdefiniować kilka wersji ściśle powiązanych procedury bez konieczności odróżnić je według nazwy. Można to zrobić przez zróżnicowanie listy parametrów.  
  
## <a name="overloading-rules"></a>Przeciążanie reguły  
 Po użytkownik przeciążanie procedury, obowiązują następujące reguły:  
  
-   **Tej samej nazwie**. Każda przeciążona wersja należy użyć tej samej nazwy procedury.  
  
-   **Inny podpis**. Każda wersja przeciążona muszą różnić się od wszystkich innych przeciążone wersje w co najmniej jeden z następujących aspektach:  
  
    -   Liczba parametrów  
  
    -   Kolejność parametrów  
  
    -   Typy danych parametrów  
  
    -   Liczba parametrów typu (w przypadku ogólnych procedura)  
  
    -   Zwracany typ (tylko dla operatora konwersji)  
  
     Wraz z nazwą procedury poprzednie elementy są nazywane *podpisu* procedury. Po wywołaniu procedury przeciążenia, kompilator używa sygnatury do sprawdzenia, czy wywołanie odpowiada poprawnie definicji.  
  
-   **Elementy nie jest częścią podpisu**. Procedury nie mogą przeciążać bez zróżnicowanie podpis. W szczególności nie mogą przeciążać procedury przez zróżnicowanie tylko jeden lub więcej z następujących elementów:  
  
    -   Słowa kluczowe modyfikator procedury, takich jak `Public`, `Shared`, i `Static`  
  
    -   Parametr lub typ nazwy parametrów  
  
    -   Ograniczenia parametru typu (w przypadku ogólnych procedura)  
  
    -   Słowa kluczowe modyfikator parametrów, takich jak `ByRef` i `Optional`  
  
    -   Czy wartość jest zwracana  
  
    -   Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)  
  
     Elementy na powyższej liście nie są częścią podpis. Mimo że nie można ich użyć do rozróżnienia między przeciążone wersje, można je różnią przeciążone wersje, które są właściwie zróżnicowane według ich podpisy.  
  
-   **Z późnym wiązaniem argumenty**. Jeśli zamierzasz przekazać późno zmiennej powiązany obiekt do przeciążoną wersją, należy zadeklarować odpowiedni parametr jako <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Wielu wersji procedury  
 Załóżmy, że piszesz `Sub` procedury, aby transakcję przed saldo odbiorcy, a ma być dostępna do odwoływania się do klienta, według nazwy lub numer konta. Aby to umożliwić, należy zdefiniować dwa różne `Sub` procedury jak w poniższym przykładzie:  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a>Przeciążone wersje  
 Alternatywą jest nazwa jednej procedury przeciążenia. Możesz użyć [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe, aby zdefiniować wersję procedurę dla każdej listy parametrów w następujący sposób:  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a>Dodatkowe przeciążenia  
 Jeśli chcesz również zaakceptować ilości transakcji, albo `Decimal` lub `Single`, można dodatkowo przeciążenia `post` umożliwia dla tej odmiany. Jeśli tak, to nie do poszczególnych przeciążeń w poprzednim przykładzie należałoby cztery `Sub` procedury, wszystkie o takiej samej nazwie, ale z czterech różnych podpisów.  
  
## <a name="advantages-of-overloading"></a>Korzyści wynikające z przeciążenia  
 Zaletą przeciążanie procedury trwa elastyczność wywołania. Do użycia `post` procedury zadeklarowane w poprzednim przykładzie, kod wywołujący można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie wywołać tę samą procedurę w obu przypadkach. Ilustruje to poniższy przykład:  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Instrukcje: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: Wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
