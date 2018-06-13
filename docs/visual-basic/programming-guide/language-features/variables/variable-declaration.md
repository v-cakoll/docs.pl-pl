---
title: Deklaracja zmiennej w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 6890ddfd8b463cd731ab3d8f39565b50a31a1192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656142"
---
# <a name="variable-declaration-in-visual-basic"></a>Deklaracja zmiennej w Visual Basic
Można zadeklarować zmiennej do określenia nazwy i właściwości. Instrukcja deklaracji zmiennych jest [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Jej lokalizacja i zawartość należy określić charakterystyki zmiennej.  
  
 Reguły nazewnictwa zmiennych i zagadnienia, zobacz [zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Poziomy deklaracji  
  
### <a name="local-and-member-variables"></a>Lokalne i zmienne Członkowskie  
 A *zmiennej lokalnej* to taki, który jest zadeklarowana w obrębie procedury. A *zmiennej członkowskiej* jest elementem członkowskim typu Visual Basic; jest zadeklarowany na poziomie modułu, wewnątrz klasy, struktury lub moduł, ale nie w dowolnej procedury wewnętrzne dla tej klasy, struktury lub modułu.  
  
### <a name="shared-and-instance-variables"></a>Udostępnione i wystąpienie zmiennych  
 W klasie lub strukturze kategorii zmiennej członkowskiej zależy od tego, czy są one udostępniane. Jeśli jest ona zadeklarowana z [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) — słowo kluczowe, jest *współdzielonej zmiennej*, i istnieje on w pojedynczej kopii współdzielona przez wszystkie wystąpienia klasy lub struktury.  
  
 W przeciwnym razie jest *zmienna wystąpienia*, i osobną kopię jest tworzony dla każdego wystąpienia klasy lub struktury. Kopię danego zmienna wystąpienia jest dostępna tylko dla wystąpienia klasy lub struktury, w której został utworzony. Jest niezależna od kopię zmienna wystąpienia w wszystkie inne wystąpienia klasy lub struktury.  
  
## <a name="declaring-data-type"></a>Deklarowanie typu danych  
 [Jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli w instrukcji deklaracji można zdefiniować typu danych lub typ obiektu są deklarowanie zmiennej. Można określić jedną z następujących typów dla zmiennej:  
  
-   Typ danych podstawowych, takich jak `Boolean`, `Long`, lub `Decimal`  
  
-   Złożonego typu danych, takich jak tablica lub struktury  
  
-   Typ obiektu lub klasa zdefiniowana w aplikacji lub w innej aplikacji  
  
-   A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy, takie jak <xref:System.Windows.Forms.Label> lub <xref:System.Windows.Forms.TextBox>  
  
-   Typ interfejsu, takich jak <xref:System.IComparable> lub <xref:System.IDisposable>  
  
 Kilku zmiennych w jednej instrukcji można zadeklarować bez konieczności powtarzania typu danych. W poniższych instrukcjach, zmienne `i`, `j`, i `k` został zadeklarowany jako typ `Integer`, `l` i `m` jako `Long`, i `x` i `y` jako `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Aby uzyskać więcej informacji o typach danych, zobacz [typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Aby uzyskać więcej informacji dotyczących obiektów, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [programowania ze składnikami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Wnioskowanie o typie lokalnym  
 *Wnioskowanie o typie* służy do określania typów danych zmienna lokalna zadeklarowana bez `As` klauzuli. Kompilator wnioskuje typ zmiennej typu wyrażenia inicjowania. Dzięki temu można zadeklarować zmienne bez jawne określenie typu. W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane liczbami całkowitymi.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Jeśli chcesz użyć wnioskowanie o typie lokalnym, `Option Infer` musi mieć ustawioną `On`. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Właściwości zadeklarowane zmienne  
 *Okres istnienia* zmiennej jest okres, w którym jest dostępny do użytku. Ogólnie rzecz biorąc istnieje zmienna, jak długo element, który deklaruje on (np. procedury lub klasy) nadal istnieje. Zmienna nie trzeba kontynuować istniejące poza okres istnienia jego zawierający element, nie trzeba wykonywać żadnych czynności specjalne w deklaracji. Jeśli zmienna musi nadal istnieje dłużej niż jego zawierający element, należą `Static` lub `Shared` — słowo kluczowe w jego `Dim` instrukcji. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Zakres* zmiennej to zbiór wszystkich kod, który może odwoływać się do niego bez kwalifikujących się jego nazwę. Zakres zmiennej jest określana przez którym jest zadeklarowany. Kod znajdujący się w danym regionie można używać zmiennych zdefiniowanych w tym regionie bez konieczności kwalifikują się ich nazw. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Zmienna *poziom dostępu* jest zakres kodu, który ma uprawnienia dostępu do niego. Jest to określane przez modyfikator dostępu (takich jak [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md)) używanego w `Dim` instrukcji. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie nowej zmiennej](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [Instrukcje: przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
