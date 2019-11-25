---
title: With...End With — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: eb8790d0d8f82232a4b10e4e0e30165745c065c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352734"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With — Instrukcja (Visual Basic)

Wykonuje szereg instrukcji, które wielokrotnie odwołują się do pojedynczego obiektu lub struktury, dzięki czemu instrukcje mogą używać uproszczonej składni podczas uzyskiwania dostępu do członków obiektu lub struktury.  When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.

## <a name="syntax"></a>Składnia

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`objectExpression`|Wymagany. Wyrażenie, które zostaje oszacowane do obiektu. Wyrażenie może być dowolnie złożone i jest sprawdzane tylko raz. Wyrażenie może być dowolnego typu danych, w tym typów podstawowych.|
|`statements`|Opcjonalny. One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.|
|`End With`|Wymagany. Terminates the definition of the `With` block.|

## <a name="remarks"></a>Uwagi

By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times. Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.

For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.

If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:

- Nie musisz szacować złożonego wyrażenia wiele razy ani przypisywać wyniku do zmiennej tymczasowej, aby odwołać się do jego członków wiele razy.

- Kod staje się bardziej czytelny dzięki eliminacji powtarzających się wyrażeń kwalifikujących.

The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.  If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.  This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.  Problem w obu przypadkach jest taki, że struktura istnieje tylko na stosie wywołań i nie ma żadnego sposobu, aby członek zmodyfikowanej struktury w takich sytuacjach mógł pisać do takich lokalizacji, żeby inny kod w programie mógł obserwować zmiany.

The `objectExpression` is evaluated once, upon entry into the block. You can't reassign the `objectExpression` from within the `With` block.

Within a `With` block, you can access the methods and properties of only the specified object without qualifying them. Możesz użyć metod i właściwości innych obiektów, ale musisz je zakwalifikować z ich nazwami obiektów.

You can place one `With...End With` statement within another. Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context. You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.

You can't branch into a `With` statement block from outside the block.

Instrukcje są wykonywane tylko raz, chyba że blok zawiera pętlę. Możesz zagnieździć różne rodzaje struktur sterujących. For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> You can use the `With` keyword in object initializers also. For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.

## <a name="example"></a>Przykład

In the following example, each `With` block executes a series of statements on a single object.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Przykład

The following example nests `With…End With` statements. Within the nested `With` statement, the syntax refers to the inner object.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic.List%601>
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
