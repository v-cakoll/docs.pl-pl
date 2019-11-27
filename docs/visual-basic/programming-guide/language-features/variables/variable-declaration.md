---
title: Deklaracja zmiennej
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
ms.openlocfilehash: b89773e9527af0d65cde53b61654f2511f5c8dde
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351762"
---
# <a name="variable-declaration-in-visual-basic"></a>Deklaracja zmiennej w Visual Basic
Należy zadeklarować zmienną, aby określić jej nazwę i cechy. Instrukcja deklaracji dla zmiennych jest [instrukcją Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Jego lokalizacja i zawartość określają cechy zmiennych.  
  
 Aby poznać zmienne reguły nazewnictwa i zagadnienia, zobacz [zadeklarowane nazwy elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Poziomy deklaracji  
  
### <a name="local-and-member-variables"></a>Zmienne lokalne i Członkowskie  
 *Zmienna lokalna* jest taka, która jest zadeklarowana w ramach procedury. *Zmienna członkowska* jest elementem członkowskim typu Visual Basic; jest on zadeklarowany na poziomie modułu, wewnątrz klasy, struktury lub modułu, ale nie w żadnej procedurze wewnętrznej dla tej klasy, struktury lub modułu.  
  
### <a name="shared-and-instance-variables"></a>Zmienne udostępnione i wystąpienia  
 W klasie lub strukturze Kategoria zmiennej składowej zależy od tego, czy jest ona udostępniona. Jeśli jest zadeklarowany za pomocą słowa kluczowego [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) , jest to *zmienna udostępniona*i istnieje w pojedynczej kopii współdzielonej między wszystkimi wystąpieniami klasy lub struktury.  
  
 W przeciwnym razie jest to *zmienna wystąpienia*, a oddzielna kopia jest tworzona dla każdego wystąpienia klasy lub struktury. Dana kopia zmiennej wystąpienia jest dostępna tylko dla wystąpienia klasy lub struktury, w której została utworzona. Jest on niezależny od kopii zmiennej wystąpienia w innym wystąpieniu klasy lub struktury.  
  
## <a name="declaring-data-type"></a>Deklarowanie typu danych  
 Klauzula [as](../../../../visual-basic/language-reference/statements/as-clause.md) w instrukcji deklaracji umożliwia zdefiniowanie typu danych lub typu obiektu deklarowanej zmiennej. Można określić dowolny z następujących typów dla zmiennej:  
  
- Podstawowy typ danych, taki jak `Boolean`, `Long`lub `Decimal`  
  
- Złożony typ danych, taki jak tablica lub struktura  
  
- Typ obiektu lub Klasa, zdefiniowane w aplikacji lub w innej aplikacji  
  
- Klasa .NET Framework, taka jak <xref:System.Windows.Forms.Label> lub <xref:System.Windows.Forms.TextBox>  
  
- Typ interfejsu, taki jak <xref:System.IComparable> lub <xref:System.IDisposable>  
  
 Można zadeklarować kilka zmiennych w jednej instrukcji bez konieczności powtarzania typu danych. W poniższych instrukcjach zmienne `i`, `j`i `k` są zadeklarowane jako `Integer`, `l` i `m` jako `Long`, a `x` i `y` jako `Single`:  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Aby uzyskać więcej informacji na temat typów danych, zobacz [typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Aby uzyskać więcej informacji na temat obiektów, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [Programowanie za pomocą składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
## <a name="local-type-inference"></a>Wnioskowanie o typie lokalnym  
 *Wnioskowanie o typie* służy do określania typów danych zmiennych lokalnych zadeklarowanych bez klauzuli `As`. Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Dzięki temu można zadeklarować zmienne bez jawnego stwierdzenia typu. W poniższym przykładzie zarówno `num1`, jak i `num2` są silnie wpisane jako liczby całkowite.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 Jeśli chcesz użyć wnioskowania o typie lokalnym, `Option Infer` musi być ustawiona na `On`. Aby uzyskać więcej informacji, zobacz [lokalne wnioskowanie o typie](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [zestawienie opcji](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Charakterystyki zadeklarowanych zmiennych  
 Okres *istnienia* zmiennej to okres czasu, w którym jest dostępny do użycia. Ogólnie rzecz biorąc, zmienna istnieje, tak długo, jak element, który deklaruje go (na przykład procedura lub Klasa), nadal istnieje. Jeśli zmienna nie musi kontynuować istniejących poza okresem istnienia elementu zawierającego, nie trzeba wykonywać żadnych specjalnych w deklaracji. Jeśli zmienna musi nadal istnieć dłużej niż jej element zawierający, można w instrukcji `Dim` dodać słowo kluczowe `Static` lub `Shared`. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Zakres* zmiennej to zestaw wszystkich kodów, które mogą odwoływać się do niego bez zakwalifikowania jego nazwy. Zakres zmiennej jest określany na podstawie tego, gdzie jest zadeklarowany. Kod znajdujący się w danym regionie może używać zmiennych zdefiniowanych w tym regionie bez konieczności kwalifikowania ich nazw. Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 *Poziom dostępu* do zmiennej to zakres kodu, który ma uprawnienia dostępu do niego. Jest to określane przez modyfikator dostępu (na przykład [Public](../../../../visual-basic/language-reference/modifiers/public.md) lub [Private](../../../../visual-basic/language-reference/modifiers/private.md)), który jest używany w instrukcji `Dim`. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie nowej zmiennej](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [Instrukcje: przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
