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
ms.openlocfilehash: 699737ffbe0b136af8862931fadacec26772b928
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833285"
---
# <a name="variable-declaration-in-visual-basic"></a>Deklaracja zmiennej w Visual Basic
Można zadeklarować zmiennej do określenia nazwy i właściwości. Instrukcji deklaracji zmiennych jest [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Jej lokalizacja i zawartości należy określić charakterystyki zmiennej.  
  
 Reguły nazewnictwa zmiennych i zagadnienia, zobacz [zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Poziomy deklaracji  
  
### <a name="local-and-member-variables"></a>Lokalne i zmienne Członkowskie  
 A *zmienna lokalna* to taki, który jest zadeklarowany w procedurze. A *zmiennej składowej* jest elementem członkowskim typu języka Visual Basic; jest zadeklarowany na poziomie modułu, wewnątrz klasy, struktury lub modułu, ale nie w ramach dowolnej procedury wewnętrzne dla tej klasy, struktury lub modułu.  
  
### <a name="shared-and-instance-variables"></a>Udostępnione i zmienne wystąpienia  
 W klasie lub strukturze kategorii zmiennej elementu członkowskiego zależy od tego, czy jest udostępniony. Jeśli jest zadeklarowana za pomocą [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) — słowo kluczowe, jest *współdzielonej zmiennej*, i istnieje on w pojedynczej kopii współużytkowane przez wszystkie wystąpienia klasy lub struktury.  
  
 W przeciwnym razie jest *zmienną instance*, i oddzielna kopia jest tworzony dla każdego wystąpienia klasy lub struktury. Dany kopię zmiennej wystąpienia jest dostępna tylko dla wystąpienia klasy lub struktury, w której został utworzony. Jest ono niezależne od kopię zmiennej instancji w przypadku dowolnego innego wystąpienia klasy lub struktury.  
  
## <a name="declaring-data-type"></a>Deklarowanie typu danych  
 [Jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli w instrukcji deklaracji pozwala na zdefiniowanie typu danych lub typ obiektu są deklarowanie zmiennej. Można określić jedną z następujących typów dla zmiennej:  
  
-   Typ danych podstawowych, takich jak `Boolean`, `Long`, lub `Decimal`  
  
-   Złożony typ danych, takich jak tablica lub struktury  
  
-   Typ obiektu lub klasy, zdefiniowanej w aplikacji lub w innej aplikacji  
  
-   A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy, takie jak <xref:System.Windows.Forms.Label> lub <xref:System.Windows.Forms.TextBox>  
  
-   Typ interfejsu, takich jak <xref:System.IComparable> lub <xref:System.IDisposable>  
  
 Bez konieczności powtarzania typu danych, można zadeklarować kilku zmiennych w jednej instrukcji. W następujących instrukcjach zmienne `i`, `j`, i `k` są deklarowane jako typ `Integer`, `l` i `m` jako `Long`, i `x` i `y` jako `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Aby uzyskać więcej informacji na temat typów danych, zobacz [typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Aby uzyskać więcej informacji na temat obiektów, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [Programowanie przy użyciu składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
## <a name="local-type-inference"></a>Wnioskowanie o typie lokalnym  
 *Wnioskowanie o typie* służy do określania typów danych zmiennych lokalnych zadeklarowana bez `As` klauzuli. Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Dzięki temu można deklarować zmienne bez jawne określenie typu. W poniższym przykładzie zarówno `num1` i `num2` są silnie typizowane jako liczby całkowite.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 Jeśli chcesz używać w przypadku wnioskowanie o typie lokalnym `Option Infer` musi być równa `On`. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Charakterystyka zadeklarowanych zmiennych  
 *Okres istnienia* zmiennej jest okres, podczas którego jest dostępny do użytku. Ogólnie rzecz biorąc istnieje zmienna tak długo, jak długo element, który deklaruje go (np. procedury lub klasy), nadal istnieje. Jeśli zmienna nie wymaga kontynuować, istniejące poza okres istnienia jej elementu zawierającego, nie musisz wykonywać żadnych specjalnych w deklaracji czynności. Jeśli zmienna musi nadal istnieje dłużej niż jego element zawierający, można dołączyć `Static` lub `Shared` — słowo kluczowe w jego `Dim` instrukcji. Aby uzyskać więcej informacji, zobacz [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Zakres* zmiennej to zbiór cały kod, który może odwoływać się do niego bez kwalifikowania nazwy. Zmienna zakresu jest określany przez którym jest zdeklarowana. Kod znajduje się w danym regionie, można użyć zmiennych zdefiniowanych w danym regionie bez kwalifikowania ich nazwy. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Zmienna *poziom dostępu* jest w zakresie kodu, który ma uprawnienia dostępu do niego. Jest to określane przez modyfikator dostępu (takich jak [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md)) używanego w `Dim` instrukcji. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Utwórz nową zmienną](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [Instrukcje: Przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
