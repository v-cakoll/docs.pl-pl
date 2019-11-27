---
title: Property — Instrukcja
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
ms.openlocfilehash: 80bce2442d96ecb9c548a88c8e5ee44c6258473b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346757"
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

- `attributelist`

  Opcjonalny. Lista atrybutów, które są stosowane do tej właściwości lub `Get` lub `Set`. Zobacz [listę atrybutów](attribute-list.md).

- `Default`

  Opcjonalny. Określa, że ta właściwość jest właściwością domyślną klasy lub struktury, w której jest zdefiniowana. Właściwości domyślne muszą akceptować parametry i mogą być ustawiane i pobierane bez określenia nazwy właściwości. W przypadku deklarowania właściwości jako `Default`nie można użyć `Private` we właściwości lub jednej z jej procedur właściwości.

- `accessmodifier`

  Opcjonalne w instrukcji `Property` i na co najmniej jednej instrukcji `Get` i `Set`. Może to być jeden z następujących modyfikatorów dostępu:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Private Protected](../modifiers/private-protected.md)

  Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `propertymodifiers`

  Opcjonalny. Może to być jeden z następujących modyfikatorów dostępu:

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcjonalny. Zobacz [udostępnianie](../modifiers/shared.md).

- `Shadows`

  Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).

- `ReadOnly`

  Opcjonalny. Zobacz [tylko do odczytu](../modifiers/readonly.md).

- `WriteOnly`

  Opcjonalny. Zobacz [WriteOnly](../modifiers/writeonly.md).

- `Iterator`

  Opcjonalny. Zobacz [iterator](../modifiers/iterator.md).

- `name`

  Wymagany. Nazwa właściwości. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `parameterlist`

  Opcjonalny. Lista nazw zmiennych lokalnych reprezentujących parametry tej właściwości oraz możliwe dodatkowe parametry procedury `Set`. Zobacz [listę parametrów](parameter-list.md).

- `returntype`

  Wymagane, jeśli `Option Strict` jest `On`. Typ danych wartości zwracanej przez tę właściwość.

- `Implements`

  Opcjonalny. Wskazuje, że ta właściwość implementuje jedną lub więcej właściwości, każda zdefiniowana w interfejsie implementowanym przez tę właściwość zawierającą klasę lub strukturę. Zobacz [instrukcja Implements](implements-statement.md).

- `implementslist`

  Wymagane, jeśli podano `Implements`. Lista implementowanych właściwości.

  `implementedproperty [ , implementedproperty ... ]`

  Każda `implementedproperty` ma następującą składnię i części:

  `interface.definedname`

  |Części|Opis|
  |---|---|
  |`interface`|Wymagany. Nazwa interfejsu implementowanego przez tę właściwość zawierającą klasę lub strukturę.|
  |`definedname`|Wymagany. Nazwa, przez którą właściwość jest zdefiniowana w `interface`.|

- `Get`

  Opcjonalny. Wymagane, jeśli właściwość jest oznaczona `ReadOnly`. Uruchamia procedurę właściwości `Get`, która jest używana do zwracania wartości właściwości.  Instrukcja `Get` nie jest używana z właściwościami, które są [implementowane](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `statements`

  Opcjonalny. Blok instrukcji do uruchomienia w ramach procedury `Get` lub `Set`.

- `End Get`

  Kończy procedurę właściwości `Get`.

- `Set`

  Opcjonalny. Wymagane, jeśli właściwość jest oznaczona `WriteOnly`. Uruchamia procedurę właściwości `Set`, która jest używana do przechowywania wartości właściwości.  Instrukcja `Set` nie jest używana z właściwościami, które są [implementowane](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

- `End Set`

  Kończy procedurę właściwości `Set`.

- `End Property`

  Kończy definicję tej właściwości.

## <a name="remarks"></a>Uwagi

Instrukcja `Property` wprowadza deklarację właściwości. Właściwość może mieć procedurę `Get` (tylko do odczytu), procedurę `Set` (tylko zapis) lub obie (odczyt i zapis). Możesz pominąć `Get` i `Set` procedury w przypadku użycia właściwości, która jest implementowana. Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](../../programming-guide/language-features/procedures/auto-implemented-properties.md).

`Property` można użyć tylko na poziomie klasy. Oznacza to, że *kontekst deklaracji* właściwości musi być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Domyślnie właściwości używają publicznego dostępu. Poziom dostępu do właściwości można dostosować za pomocą modyfikatora dostępu w instrukcji `Property` i opcjonalnie można dostosować jedną z jej procedur właściwości do bardziej restrykcyjnego poziomu dostępu.

Visual Basic przekazuje parametr do procedury `Set` podczas przypisywania właściwości. Jeśli nie podasz parametru dla `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`. Ten parametr zawiera wartość, która ma zostać przypisana do właściwości. Zwykle ta wartość jest przechowywana w prywatnej zmiennej lokalnej i zwracana przy każdym wywołaniu procedury `Get`.

## <a name="rules"></a>Reguły

- **Mieszane poziomy dostępu.** W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub procedury `Set`, ale nie dla obu tych opcji. W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować procedurę `Set` `Private`, ale nie `Public`.

  Jeśli definiujesz Właściwość `ReadOnly` lub `WriteOnly`, procedura pojedynczej właściwości (odpowiednio`Get` lub `Set`) reprezentuje wszystkie właściwości. Nie można zadeklarować innego poziomu dostępu dla takiej procedury, ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.

- **Typ zwracany.** Instrukcja `Property` może deklarować typ danych zwracanej wartości. Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.

  Jeśli nie określisz `returntype`, właściwość zwróci `Object`.

- **Realizacji.** Jeśli ta właściwość używa słowa kluczowego `Implements`, zawierająca klasę lub strukturę musi mieć instrukcję `Implements` bezpośrednio po instrukcji `Class` lub `Structure`. Instrukcja `Implements` musi zawierać każdy interfejs określony w `implementslist`. Jednak nazwa, za pomocą której interfejs definiuje `Property` (w `definedname`), nie musi być taka sama jak nazwa tej właściwości (w `name`).

## <a name="behavior"></a>Zachowanie

- **Powrót z procedury właściwości.** Gdy procedura `Get` lub `Set` powraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji następującej po wywołaniu instrukcji.

  Instrukcje `Exit Property` i `Return` powodują natychmiastowe wyjście z procedury właściwości. Dowolna liczba instrukcji `Exit Property` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Property` i `Return`.

- **Wartość zwracana.** Aby zwrócić wartość z procedury `Get`, można przypisać wartość do nazwy właściwości lub włączyć ją w instrukcji `Return`. Poniższy przykład przypisuje wartość zwracaną do nazwy właściwości `quoteForTheDay` a następnie używa instrukcji `Exit Property` do zwrócenia.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  Jeśli używasz `Exit Property` bez przypisywania wartości do `name`, procedura `Get` zwróci wartość domyślną dla typu danych właściwości.

  Instrukcja `Return` w tym samym czasie przypisuje `Get`ą wartość procedury i kończy procedurę. Poniższy przykład pokazuje.

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a>Przykład

Poniższy przykład deklaruje właściwość w klasie.

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a>Zobacz także

- [Właściwości zaimplementowane automatycznie](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Get, instrukcja](get-statement.md)
- [Set, instrukcja](set-statement.md)
- [Lista parametrów](parameter-list.md)
- [Default](../modifiers/default.md)
