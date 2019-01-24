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
ms.openlocfilehash: dd50435b7cbb5d3d25c0e30618e8733b4eddfe91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655078"
---
# <a name="type-list-visual-basic"></a>Lista typów (Visual Basic)
Określa *parametry typu* dla *ogólny* elementu programistycznego. Wiele parametrów są oddzielone przecinkami. Poniżej przedstawiono składnię dla jednego typu parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`genericmodifier`|Opcjonalna. Mogą być używane tylko w interfejsach ogólnych i delegatach. Można zadeklarować typu kowariantne przy użyciu [się](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) — słowo kluczowe lub kontrawariantny przy użyciu [w](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) — słowo kluczowe. Zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Wymagana. Nazwa parametru typu. Jest to symbol zastępczy, mają zostać zastąpione przez dostarczony przez odpowiedni argument typu zdefiniowanego typu.|  
|`constraintlist`|Opcjonalna. Listę wymagań, które ograniczenia typu danych, które mogą być dostarczane na potrzeby `typename`. Jeśli masz wiele ograniczeń, należy ją ująć w nawiasy klamrowe (`{ }`) i je oddzielić przecinkami. Należy wprowadzić listę ograniczenie [jako](../../../visual-basic/language-reference/statements/as-clause.md) — słowo kluczowe. Możesz użyć `As` tylko raz na początku listy.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy ogólnego elementu programistycznego, należy wykonać co najmniej jeden parametr typu. Parametr typu jest symbolem zastępczym dla określonego typu ( *element skonstruowany*) kod klienta określa, podczas tworzenia wystąpienia typu ogólnego. Można zdefiniować klasy ogólnej, struktury, interfejsu, procedury lub delegowanie.  
  
 Aby uzyskać więcej informacji o tym, kiedy do definiowania typu ogólnego, zobacz [typów ogólnych w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Aby uzyskać więcej informacji na temat nazwy parametrów typu, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>reguły  
  
-   **Nawiasy.** Jeśli podasz lista parametrów typu, należy ją ująć w nawiasy i należy wprowadzić listę [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Możesz użyć `Of` tylko raz na początku listy.  
  
-   **Ograniczenia.** Lista *ograniczenia* w danym typie parametr może zawierać następujące elementy w dowolnej kombinacji:  
  
    -   Dowolną liczbę interfejsów. Dostarczony typ musi implementować każdy interfejs na tej liście.  
  
    -   Co najwyżej jedną klasę. Dostarczony typ musi dziedziczyć z tej klasy.  
  
    -   `New` — Słowo kluczowe. Dostarczony typ musi ujawniać konstruktor bez parametrów, mogą uzyskiwać dostęp do danego typu ogólnego. Jest to przydatne, jeśli ograniczenia parametru typu przez jeden lub więcej interfejsów. Typ, który implementuje interfejsy nie ujawnia konstruktora, a następnie w zależności od poziomu dostępu do konstruktora, kod w ramach ogólnego typu nie może być uzyskiwać do niego dostęp.  
  
    -   Albo `Class` — słowo kluczowe lub `Structure` — słowo kluczowe. `Class` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wymagać wszystkich argumentów typu do niego być typem referencyjnym, na przykład ciąg, tablica lub delegata, lub obiekt utworzony z klasy. `Structure` — Słowo kluczowe ogranicza parametr typu ogólnego, aby wszystkich argumentów typu do niego typ wartości, na przykład wpisz struktury, wyliczenia lub danych podstawowych. Nie można uwzględnić jednocześnie `Class` i `Structure` w tym samym `constraintlist`.  
  
     Dostarczony typ musi spełniać wymagania, co należy uwzględnić w `constraintlist`.  
  
     Ograniczenia dotyczące każdego parametru typu są niezależne od ograniczenia dotyczące innych parametrów typu.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Podstawienia w czasie kompilacji.** Po utworzeniu skonstruowanego typu od ogólnego elementu programistycznego podajesz zdefiniowanym typem dla każdego parametru typu. Kompilator Visual Basic zastępuje podane typu każde wystąpienie `typename` w ramach ogólnego elementu.  
  
-   **Brak ograniczeń.** Jeśli nie określisz żadnych ograniczeń dla parametru typu, Twój kod jest ograniczona do operacji i obsługiwane przez elementy członkowskie [Object — typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md) dla tego parametru typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje szkielet definicji klasy generyczny słownik, w tym szkielet funkcję, aby dodać nowy wpis do słownika.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>Przykład  
 Ponieważ `dictionary` jest ogólny, kod, który korzysta z niego można tworzyć wiele obiektów z niego, każdy mających taką samą funkcjonalność, ale na inny typ danych. W poniższym przykładzie pokazano wiersz kodu, który tworzy `dictionary` obiekt z `String` wpisów i `Integer` kluczy.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje równoważnych definicji szkielet wygenerowane w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [z](../../../visual-basic/language-reference/statements/of-clause.md)
- [New, operator](../../../visual-basic/language-reference/operators/new-operator.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Object, typ danych](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [W](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
