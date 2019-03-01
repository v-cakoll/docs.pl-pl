---
title: Property — instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 0b8bec965e5a149466863cde7a2646128469cbd0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972173"
---
# <a name="property-statement"></a>Property — Instrukcja
Deklaruje nazwę właściwości i procedury właściwości używane do przechowywania i pobierania wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a>Części  
  
-   `attributelist`  
  
     Opcjonalna. Lista atrybutów, które są stosowane do tej właściwości lub `Get` lub `Set` procedury. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     Opcjonalna. Określa, że ta właściwość jest właściwością domyślną dla klasy lub struktury, na którym jest zdefiniowana. Domyślne właściwości muszą akceptować parametry można ustawić i pobrać bez określenia nazwy właściwości. Jeśli zadeklarować właściwości jako `Default`, nie można użyć `Private` na właściwość lub jednej z jego procedur właściwość.  
  
-   `accessmodifier`  
  
     Opcjonalnie na `Property` instrukcji i co najwyżej jeden z `Get` i `Set` instrukcji. Może to być jeden z następujących elementów:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md) 

    - [Private Protected](../../language-reference/modifiers/private-protected.md)
  
     Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `propertymodifiers`  
  
     Opcjonalna. Może to być jeden z następujących elementów:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcjonalna. Zobacz [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     Opcjonalna. Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     Opcjonalna. Zobacz [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     Opcjonalna. Zobacz [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Wymagana. Nazwa właściwości. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     Opcjonalna. Lista reprezentującą parametry tej właściwości i możliwe dodatkowe parametry nazwy zmiennych lokalnych `Set` procedury. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Jeśli wymagane `Option Strict` jest `On`. Typ danych wartości zwracanej przez tę właściwość.  
  
-   `Implements`  
  
     Opcjonalna. Wskazuje, że ta właściwość implementuje jedną lub więcej właściwości, każdy z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierający tę właściwość. Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Jeśli wymagane `Implements` podano. Lista właściwości, które są zaimplementowane.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Każdy `implementedproperty` ma następujące składni i części:  
  
     `interface.definedname`  
  
    |Część|Opis|  
    |---|---|  
    |`interface`|Wymagana. Nazwa interfejsu implementowany przez tę właściwość zawierający klasy lub struktury.|  
    |`definedname`|Wymagana. Nazwa, przez którą właściwość jest zdefiniowana w `interface`.|  
  
-   `Get`  
  
     Opcjonalna. Wymagane, jeśli właściwość jest oznaczona `WriteOnly`. Uruchamia `Get` procedury właściwość, która służy do zwracania wartości właściwości.  
  
-   `statements`  
  
     Opcjonalna. Blok instrukcji do uruchomienia w ramach `Get` lub `Set` procedury.  
  
-   `End Get`  
  
     Kończy `Get` procedury właściwości.  
  
-   `Set`  
  
     Opcjonalna. Wymagane, jeśli właściwość jest oznaczona `ReadOnly`. Uruchamia `Set` procedury właściwości, który jest używany do przechowywania wartości właściwości.  
  
-   `End Set`  
  
     Kończy `Set` procedury właściwości.  
  
-   `End Property`  
  
     Kończy definicję tej właściwości.  
  
## <a name="remarks"></a>Uwagi  
 `Property` Instrukcji wprowadza deklaracja właściwości. Właściwość może mieć `Get` (tylko odczyt), procedury `Set` procedury (tylko do zapisu) lub obu (odczyt zapis). Możesz pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości. Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Możesz użyć `Property` tylko na poziomie klasy. Oznacza to, że *kontekst deklaracji* dla właściwości muszą być klasy, struktury, modułu lub interfejsu, a nie może być plik źródłowy, przestrzeń nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Domyślnie właściwości używają dostępu publicznego. Możesz dostosować poziom dostępu do właściwości przy użyciu modyfikatora dostępu na `Property` instrukcji, a opcjonalnie dostosować jeden z jego właściwości procedury bardziej restrykcyjny poziom dostępu.  
  
 Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości. Jeśli parametr nie zostanie podana `Set`, zintegrowanego środowiska programistycznego (IDE) korzysta z niejawny parametr o nazwie `value`. Ten parametr zawiera wartość do przypisania do właściwości. Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatne i przywrócić go zawsze wtedy, gdy `Get` procedura jest wywoływana.  
  
## <a name="rules"></a>reguły  
  
-   **Mieszanymi poziomami dostępu.** Jeśli zamierzasz zdefiniować właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu do różnych dla dowolnego `Get` lub `Set` procedury, ale nie oba. Jeśli to zrobisz, procedura poziom dostępu musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować `Set` procedury `Private`, ale nie `Public`.  
  
     Jeśli definiujesz `ReadOnly` lub `WriteOnly` właściwość, procedura pojedynczej właściwości (`Get` lub `Set`odpowiednio) reprezentuje wszystkie właściwości. Nie można zadeklarować na poziom dostępu innej procedury, ponieważ, ustawić dwa poziomy dostępu dla właściwości.  
  
-   **Typ zwracany.** `Property` Instrukcji można zadeklarować typ danych zwracanych wartości. Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.  
  
     Jeśli nie określisz `returntype`, zwraca właściwości `Object`.  
  
-   **Implementacja.** Jeśli ta właściwość używa `Implements` — słowo kluczowe, zawierający klasy lub struktury, musi mieć `Implements` instrukcji natychmiast po jego `Class` lub `Structure` instrukcji. `Implements` Instrukcja musi zawierać każdy interfejs określony w `implementslist`. Jednak nazwy za pomocą którego interfejs definiuje `Property` (w `definedname`) musi być taka sama jak nazwa tej właściwości (w `name`).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zwracanie z procedury właściwości.** Gdy `Get` lub `Set` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, które je wywołało.  
  
     `Exit Property` i `Return` instrukcji powodują natychmiastowego wyjścia z procedury właściwości. Dowolną liczbę `Exit Property` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Property` i `Return` instrukcji.  
  
-   **Zwraca wartość.** Aby zwrócić wartość z zakresu od `Get` procedury, można przypisać wartości do danej nazwy właściwości lub uwzględnić go w `Return` instrukcji. Poniższy przykład przypisuje wartość zwracaną do danej nazwy właściwości `quoteForTheDay` , a następnie używa `Exit Property` instrukcji, aby zwrócić.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     Jeśli używasz `Exit Property` bez przypisywania wartości do `name`, `Get` procedura zwraca wartość domyślna dla typu danych właściwości.  
  
     `Return` Przypisuje instrukcji w tym samym czasie `Get` procedury zwracać wartości i kończy procedurę. Poniższy przykład przedstawia to.  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje właściwości w klasie.  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a>Zobacz także
- [Właściwości zaimplementowane automatycznie](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
- [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Default](../../../visual-basic/language-reference/modifiers/default.md)
