---
title: "Property — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af4666ecb059f141480be2295055644537819293
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-statement"></a>Property — Instrukcja
Deklaruje nazwę właściwości i procedury właściwości używane do przechowywania i pobierania wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
     Opcjonalny. Lista atrybutów, które mają zastosowanie do tej właściwości lub `Get` lub `Set` procedury. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `Default`  
  
     Opcjonalny. Określa, że ta właściwość jest właściwością domyślną dla klasy lub struktury, na którym jest zdefiniowany. Właściwości domyślne musi akceptować parametry i można ustawić i pobrać bez określania nazwy właściwości. Jeśli można zadeklarować właściwości jako `Default`, nie można użyć `Private` na właściwość lub jedną z procedur jego właściwości.  
  
-   `accessmodifier`  
  
     Opcjonalnie na `Property` instrukcji i co najwyżej jeden z `Get` i `Set` instrukcje. Może to być jedna z następujących czynności:  
  
    -   [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `propertymodifiers`  
  
     Opcjonalny. Może to być jedna z następujących czynności:  
  
    -   [Przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Możliwym do zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcjonalny. Zobacz [udostępnionych](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `ReadOnly`  
  
     Opcjonalny. Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WriteOnly`  
  
     Opcjonalny. Zobacz [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   `Iterator`  
  
     Opcjonalny. Zobacz [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Wymagany. Nazwa właściwości. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `parameterlist`  
  
     Opcjonalny. Lista nazwy zmiennych lokalnych reprezentujący parametry tej właściwości i możliwe dodatkowe parametry `Set` procedury. Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).  
  
-   `returntype`  
  
     Jeśli wymagane `Option``Strict` jest `On`. Typ danych wartości zwracanej przez tę właściwość.  
  
-   `Implements`  
  
     Opcjonalny. Wskazuje, że ta właściwość implementuje jednej lub więcej właściwości, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tej właściwości. Zobacz [implementuje instrukcji](../../../visual-basic/language-reference/statements/implements-statement.md).  
  
-   `implementslist`  
  
     Jeśli wymagane `Implements` podano. Lista właściwości implementowana.  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     Każdy `implementedproperty` ma następujące składni i części:  
  
     `interface.definedname`  
  
    |Część|Opis|  
    |---|---|  
    |`interface`|Wymagany. Nazwa interfejsu implementowanego przez tę właściwość zawierającego klasy lub struktury.|  
    |`definedname`|Wymagany. Nazwa, przez którą właściwość jest zdefiniowana w `interface`.|  
  
-   `Get`  
  
     Opcjonalny. Wymagane, jeśli właściwość jest oznaczona jako `WriteOnly`. Uruchamia `Get` procedury właściwości, która służy do zwracania wartości właściwości.  
  
-   `statements`  
  
     Opcjonalny. Blok instrukcji do uruchomienia w ramach `Get` lub `Set` procedury.  
  
-   `End Get`  
  
     Kończy `Get` procedury właściwości.  
  
-   `Set`  
  
     Opcjonalny. Wymagane, jeśli właściwość jest oznaczona jako `ReadOnly`. Uruchamia `Set` procedury właściwości, która jest używana do przechowywania wartości właściwości.  
  
-   `End Set`  
  
     Kończy `Set` procedury właściwości.  
  
-   `End Property`  
  
     Kończy definicję tej właściwości.  
  
## <a name="remarks"></a>Uwagi  
 `Property` Instrukcji wprowadzono deklaracji właściwości. Może mieć właściwości `Get` procedury (tylko do odczytu), `Set` procedura (tylko do zapisu) lub obu (odczytu i zapisu). Można pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości. Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Można użyć `Property` tylko na poziomie klasy. Oznacza to, że *kontekście deklaracji* właściwość musi być klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Domyślnie właściwości używają dostępu publicznego. Można dostosować poziom dostępu do właściwości z modyfikatora dostępu w `Property` instrukcji i opcjonalnie można dostosować jedną z procedur jej właściwości na bardziej restrykcyjne poziom dostępu.  
  
 Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości. Jeśli nie podasz parametru `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`. Ten parametr zawiera wartość do przypisania do właściwości. Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatnych i przywrócić go przy każdym `Get` procedura jest wywoływana.  
  
## <a name="rules"></a>Reguły  
  
-   **Mieszanymi poziomami dostępu.** Jeśli definiujesz właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu różnych jednego `Get` lub `Set` procedura, ale nie oba. Jeśli to zrobisz, poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowany jako `Friend`, mogą zadeklarować `Set` procedury `Private`, ale nie `Public`.  
  
     Jeśli definiujesz `ReadOnly` lub `WriteOnly` właściwości, procedura jednej właściwości (`Get` lub `Set`odpowiednio) reprezentuje wszystkie właściwości. Nie można zadeklarować poziom dostępu różnych dla takiej procedury, ponieważ który ustawiał dwa poziomy dostępu dla właściwości.  
  
-   **Typ zwracany.** `Property` Instrukcji można zadeklarować typu danych zwracanych wartości. Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.  
  
     Jeśli nie określisz `returntype`, zwraca właściwość `Object`.  
  
-   **Implementacja.** Jeśli ta właściwość używa `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć `Implements` instrukcji bezpośrednio po jego `Class` lub `Structure` instrukcji. `Implements` Instrukcja musi zawierać każdego interfejsu w `implementslist`. Jednak nazwy za pomocą którego definiuje interfejs `Property` (w `definedname`) musi być taka sama jak nazwa tej właściwości (w `name`).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zwracanie z procedury właściwości.** Gdy `Get` lub `Set` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała go.  
  
     `Exit Property` i `Return` instrukcje spowodować natychmiastowe wyjścia z procedury właściwości. Dowolną liczbę `Exit Property` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Property` i `Return` instrukcje.  
  
-   **Wartość zwracana.** Zwraca wartość z `Get` procedury, można przypisać wartości do nazwy właściwości lub dołączyć go w `Return` instrukcji. Poniższy przykład przypisuje wartość zwracana do nazwy właściwości `quoteForTheDay` , a następnie używa `Exit Property` instrukcji do zwrócenia.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     Jeśli używasz `Exit Property` bez przypisywanie wartości do `name`, `Get` procedury zwraca wartość domyślna dla typu danych właściwości.  
  
     `Return` Instrukcja w tym samym czasie przypisuje `Get` procedura zwraca wartość i kończy procedurę. W poniższym przykładzie pokazano to.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje właściwości w klasie.  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości zaimplementowane automatycznie](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Get — instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set — instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Domyślne](../../../visual-basic/language-reference/modifiers/default.md)
