---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825394"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Określa, że zmiennej lub właściwości mogą być odczytywane, ale nie jest zapisywany.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Możesz użyć `ReadOnly` tylko na poziomie modułu. Oznacza to, że kontekst deklaracji `ReadOnly` elementu musi być klasy, struktury lub modułu, a nie może być plikiem źródłowym, przestrzeń nazw lub procedury.  
  
-   **Modyfikatory połączone.** Nie można określić `ReadOnly` wraz z `Static` w tej samej deklaracji.  
  
-   **Przypisywanie wartości.** Korzystanie z kodu `ReadOnly` właściwości nie można ustawić jej wartość. Jednak kod, który ma dostęp do podstawowej magazynu można przypisać lub zmień wartość w dowolnym momencie.  
  
     Można przypisać wartości do `ReadOnly` zmiennych, tylko w jego deklaracji lub w konstruktorze klasy lub struktury, w którym jest zdefiniowany.  
  
## <a name="when-to-use-a-readonly-variable"></a>Kiedy należy używać zmiennej tylko do odczytu  
 Istnieją sytuacje, w których nie można użyć [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md) zadeklarować i przypisać wartość stałą. Na przykład `Const` instrukcji, nie może zaakceptować typu danych, którą chcesz przypisać lub mogą być gotowy do obliczenia wartości w czasie kompilacji z wyrażeniem stałym. Możesz nawet nie wiedzieć, wartość w czasie kompilacji. W takich przypadkach można użyć `ReadOnly` zmienną do przechowywania wartości stałej.  
  
> [!IMPORTANT]
>  Jeśli typ danych zmiennej jest typem referencyjnym, takich jak tablica lub wystąpienia klasy, jej członków można zmienić, nawet jeśli sama zmienna jest `ReadOnly`. Ilustruje to poniższy przykład.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Podczas inicjowania tablicy, wskazywana przez `characterArray()` przechowuje "x", "y" i "z". Ponieważ zmienna `characterArray` jest `ReadOnly`, jego wartość nie można zmienić po jego zainicjowaniu; będącego, nowej tablicy nie można przypisać do niej. Można jednak zmienić wartości co najmniej jednego elementy członkowskie tablicy. Po wywołaniu do procedury `changeArrayElement`, tablicy wskazywany przez `characterArray()` przechowuje "x", "M" i "z".  
  
 Należy pamiętać, że jest to podobne do deklarowania parametr procedury, aby być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), które uniemożliwia zmianę z samym argumentem wywoływania procedury, ale pozwala zmienić jej członków.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `ReadOnly` właściwości daty, na którym został zatrudniony pracownika. Magazyny klasy wartość wewnętrznie jako `Private` zmiennej, a tylko kod wewnątrz klasy może zmienić tę wartość. Jednak właściwość jest `Public`, i wszelki kod, który mogą uzyskiwać dostęp do tej klasy może być odczytana właściwość.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` Modyfikator mogą być używane w tych kontekstach:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
