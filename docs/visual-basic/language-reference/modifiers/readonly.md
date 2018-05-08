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
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Określa, że zmienna lub właściwość mogą być odczytywane, ale nie są zapisywane.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `ReadOnly` tylko na poziomie modułu. Oznacza to, że w kontekście deklaracji `ReadOnly` elementu musi być klasą, strukturą lub modułu i nie może być plik źródłowy, przestrzeni nazw lub procedury.  
  
-   **Łączna modyfikatorów.** Nie można określić `ReadOnly` razem z `Static` w tej samej deklaracji.  
  
-   **Przypisywanie wartości.** Korzystanie z kodu `ReadOnly` właściwości nie można ustawić jej wartości. Jednak kod, który ma dostęp do powiązany magazyn można przypisać lub zmień wartość w dowolnym momencie.  
  
     Można przypisać wartości do `ReadOnly` zmiennej tylko w jego deklaracji lub w konstruktorze klasy lub struktury, w którym jest zdefiniowany.  
  
## <a name="when-to-use-a-readonly-variable"></a>Kiedy należy użyć zmiennej tylko do odczytu  
 Istnieją sytuacje, w których nie można użyć [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md) Aby zadeklarować i przypisać wartość stałą. Na przykład `Const` instrukcja nie może zaakceptować typu danych, którego chcesz przypisać lub nie można obliczyć wartość w czasie kompilacji z wyrażeniem stałym. Możesz nawet nie wiedzieć, wartość w czasie kompilacji. W takich przypadkach można użyć `ReadOnly` zmienną do przechowywania wartości stałej.  
  
> [!IMPORTANT]
>  Jeśli typ danych zmiennej jest typem referencyjnym, takich jak tablica lub wystąpienia klasy, nawet jeśli jest samej zmiennej można zmienić jej elementów członkowskich `ReadOnly`. Ilustruje to poniższy przykład.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Podczas inicjowania tablicy wskazywana przez `characterArray()` blokad "x", "y" i "z". Ponieważ zmiennej `characterArray` jest `ReadOnly`, jego wartość nie można zmienić po jego inicjowania; będący, nowej tablicy nie można przypisać do niej. Można jednak zmienić wartości co najmniej jeden z elementów tablicy. Po wywołaniu procedury `changeArrayElement`, tablicy wskazywana przez `characterArray()` blokad "x", "M" i "z".  
  
 Należy pamiętać, że jest to podobne do deklarowaniu parametru procedury należy [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), który uniemożliwia zmianę z samym argumentem wywołania procedury, ale pozwala zmienić jej elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `ReadOnly` właściwości data, na którym został dzierżawione pracownika. Magazynów klas właściwość wartość wewnętrznie jako `Private` kodu zmiennej i tylko wewnątrz klasy można zmienić tę wartość. Właściwość jest jednak `Public`, i kodu, który można uzyskać dostępu do klasy mogą odczytać właściwości.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 `ReadOnly` Modyfikatora można używać w tych sytuacjach:  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
