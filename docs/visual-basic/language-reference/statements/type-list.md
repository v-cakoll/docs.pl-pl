---
title: Lista typów (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 5fbb07154fce27feb257b431c1726446b42fbfe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605293"
---
# <a name="type-list-visual-basic"></a>Lista typów (Visual Basic)
Określa *parametry typu* dla *ogólnego* elementu programistycznego. Wiele parametrów są oddzielone przecinkami. Poniżej przedstawiono składnię dla parametru typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`genericmodifier`|Opcjonalna. Może być używana tylko w interfejsach i delegatów. Można zadeklarować typu kowariantnego przy użyciu [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) — słowo kluczowe lub kontrawariantnego przy użyciu [w](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) — słowo kluczowe. Zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Wymagana. Nazwa parametru typu. Jest to symbol zastępczy, mają zostać zastąpione przez zdefiniowanego typu dostarczonych przez argument odpowiedniego typu.|  
|`constraintlist`|Opcjonalna. Listę wymagań, które ograniczenia typu danych, które mogą być dostarczane na potrzeby `typename`. Jeśli masz wiele ograniczeń, ujmij ją w nawiasy klamrowe (`{ }`) i oddziel je przecinkami. Należy wprowadzić listę powiązanych z [jako](../../../visual-basic/language-reference/statements/as-clause.md) — słowo kluczowe. Możesz użyć `As` tylko jeden raz na początku listy.|  
  
## <a name="remarks"></a>Uwagi  
 Co ogólnego elementu programistycznego musi mieć co najmniej jeden parametr typu. Parametr typu jest symbolem zastępczym dla określonego typu ( *skonstruowane elementu*) kodu klienta określa, kiedy tworzy wystąpienie typu ogólnego. Można zdefiniować klasy ogólnej, struktury, interfejsu, procedury lub delegowanie.  
  
 Aby uzyskać więcej informacji o tym, kiedy do definiowania typu ogólnego, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Aby uzyskać więcej informacji dotyczących nazwy parametrów typu, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Nawiasy.** Jeśli możesz podać listę parametrów typu, należy ująć go w nawiasy i należy wprowadzić listę z [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Możesz użyć `Of` tylko jeden raz na początku listy.  
  
-   **Ograniczenia.** Lista *ograniczenia* na typ parametru mogą obejmować następujące elementy w dowolnej kombinacji:  
  
    -   Dowolna liczba interfejsów. Dostarczony typ musi implementować interfejs co na tej liście.  
  
    -   Co najwyżej jedną klasę. Dostarczony typ musi dziedziczyć z tej klasy.  
  
    -   `New` — Słowo kluczowe. Dostarczony typ musi ujawniać konstruktor bez parametrów, dostępnym dla danego typu ogólnego. Jest to przydatne, jeśli w przypadku ograniczenia parametru typu, przez co najmniej jeden interfejs. Typ, który implementuje interfejsy nie ujawnia konstruktora, a w zależności od poziomu dostępu konstruktora kod w typie ogólnym może okazać się niemożliwe do niego dostęp.  
  
    -   Albo `Class` — słowo kluczowe lub `Structure` — słowo kluczowe. `Class` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagać przekazywania do niej wszystkich argumentów typu być typem referencyjnym, na przykład ciąg, tablicy lub delegatem, lub obiekt utworzony z klasy. `Structure` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagał przekazywania do niej wszystkich argumentów typu jako typów wartości, na przykład typ struktury, wyliczenia lub podstawowym danych. Nie może zawierać jednocześnie `Class` i `Structure` w tym samym `constraintlist`.  
  
     Dostarczony typ musi spełniać wymagania, co w `constraintlist`.  
  
     Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczenia dotyczące innych parametrów typu.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Podstawienia w czasie kompilacji.** Po utworzeniu skonstruowanego typu z ogólnego elementu programistycznego, należy podać dla każdego parametru typu zdefiniowanego typu. Kompilator Visual Basic zastępuje typu dostarczonego dla wszystkich wystąpień `typename` w elemencie ogólnego.  
  
-   **Brak ograniczenia.** Jeśli nie określisz żadnych ograniczeń dla parametru typu kodu jest ograniczona do operacji i elementy obsługiwane przez [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md) dla tego parametru typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia definicję szkielet klasy ogólnego słownika, włączając funkcję szkielet, aby dodać nowy wpis do słownika.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>Przykład  
 Ponieważ `dictionary` jest ogólny, kod, który korzysta z niego można tworzyć wiele obiektów z niego, każdy mających taką samą funkcję, ale na inny typ danych. W poniższym przykładzie przedstawiono wiersza kodu, który tworzy `dictionary` obiekt z `String` wpisy i `Integer` kluczy.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia równoważne definicji szkielet generowane przez w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [z](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Operator New](../../../visual-basic/language-reference/operators/new-operator.md)  
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Object, typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
