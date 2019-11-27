---
title: Procedury własności
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352563"
---
# <a name="property-procedures-visual-basic"></a>Procedury własności (Visual Basic)

Procedura właściwości to seria Visual Basic instrukcji, które manipulują właściwością niestandardową w module, klasie lub strukturze. Procedury właściwości są również znane jako metody *dostępu do właściwości*.

Visual Basic zapewnia następujące procedury właściwości:

- Procedura `Get` zwraca wartość właściwości. Jest wywoływana, gdy uzyskujesz dostęp do właściwości w wyrażeniu.
- Procedura `Set` ustawia właściwość na wartość, łącznie z odwołaniem do obiektu. Jest wywoływana, gdy przypiszesz wartość do właściwości.

Zazwyczaj definiuje się procedury właściwości w parach przy użyciu instrukcji `Get` i `Set`, ale można zdefiniować pojedynczą procedurę, jeśli właściwość jest tylko do odczytu ([Get instrukcji](../../../../visual-basic/language-reference/statements/get-statement.md)) lub tylko do zapisu ([instrukcja set](../../../../visual-basic/language-reference/statements/set-statement.md)).

Możesz pominąć `Get` i `Set` procedury w przypadku użycia właściwości, która jest implementowana. Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](./auto-implemented-properties.md).

Można definiować właściwości w klasach, strukturach i modułach. Właściwości są domyślnie `Public`, co oznacza, że można je wywoływać z dowolnego miejsca w aplikacji, która może uzyskiwać dostęp do kontenera właściwości.

Porównanie właściwości i zmiennych można znaleźć [w temacie różnice między właściwościami i zmiennymi w Visual Basic](differences-between-properties-and-variables.md).

## <a name="declaration-syntax"></a>Składnia deklaracji

Sama właściwość jest definiowana przez blok kodu ujęty w [instrukcji Property](../../../../visual-basic/language-reference/statements/property-statement.md) i instrukcji `End Property`. Wewnątrz tego bloku każda procedura właściwości jest wyświetlana jako wewnętrzny blok ujęty w instrukcji deklaracji (`Get` lub `Set`) i pasującej deklaracji `End`.

Składnia do deklarowania właściwości i jej procedur jest następująca:

```vb
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]
    [AccessLevel] Get
        ' Statements of the Get procedure.
        ' The following statement returns an expression as the property's value.
        Return Expression
    End Get
    [AccessLevel] Set[(ByVal NewValue As DataType)]
        ' Statements of the Set procedure.
        ' The following statement assigns newvalue as the property's value.
        LValue = NewValue
    End Set
End Property
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

`Modifiers` można określić poziom dostępu i informacje dotyczące przeciążenia, przesłaniania, udostępniania i przesłaniania, a także określić, czy właściwość jest tylko do odczytu, czy tylko do zapisu. `AccessLevel` w procedurze `Get` lub `Set` może być dowolnym poziomem, który jest bardziej restrykcyjny niż poziom dostępu określony dla samej właściwości. Aby uzyskać więcej informacji, zobacz [instrukcja właściwości](../../../../visual-basic/language-reference/statements/property-statement.md).

### <a name="data-type"></a>Typ danych

Typ danych właściwości i poziom dostępu podmiotu zabezpieczeń są zdefiniowane w instrukcji `Property`, a nie w procedurach właściwości. Właściwość może mieć tylko jeden typ danych. Na przykład nie można zdefiniować właściwości do przechowywania wartości `Decimal`, ale pobrać `Double` wartość.

### <a name="access-level"></a>Poziom dostępu

Można jednak zdefiniować poziom dostępu podmiotu zabezpieczeń dla właściwości i jeszcze bardziej ograniczyć poziom dostępu w jednej z jej procedur dotyczących właściwości. Na przykład można zdefiniować Właściwość `Public`, a następnie zdefiniować procedurę `Private Set`. Procedura `Get` pozostanie `Public`. Poziom dostępu można zmienić tylko w jednej z procedur dotyczących właściwości i można uczynić go bardziej restrykcyjnym niż główny poziom dostępu. Aby uzyskać więcej informacji, zobacz [jak: deklarowanie właściwości z mieszanymi poziomami dostępu](how-to-declare-a-property-with-mixed-access-levels.md).

## <a name="parameter-declaration"></a>Deklaracja parametru

Każdy parametr należy zadeklarować w taki sam sposób jak [procedury Sub](sub-procedures.md), z tą różnicą, że mechanizm przekazywania musi być `ByVal`.

Składnia każdego parametru na liście parametrów jest następująca:

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

Jeśli parametr jest opcjonalny, należy również podać wartość domyślną w ramach swojej deklaracji. Składnia określająca wartość domyślną jest następująca:

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a>Wartość właściwości

W procedurze `Get` wartość zwracana jest przekazywana do wyrażenia wywołującego jako wartość właściwości.

W procedurze `Set` nowa wartość właściwości jest przenoszona do parametru instrukcji `Set`. Jeśli jawnie deklarujesz parametr, musisz zadeklarować go przy użyciu tego samego typu danych co właściwość. Jeśli parametr nie zostanie zadeklarowany, kompilator używa niejawnego parametru `Value` do reprezentowania nowej wartości, która ma zostać przypisana do właściwości.

## <a name="calling-syntax"></a>Składnia wywołania

Wywoływanie procedury właściwości niejawnie przez utworzenie odwołania do właściwości. Nazwa właściwości jest używana w taki sam sposób, jak przy użyciu nazwy zmiennej, z tą różnicą, że należy podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach. Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.

Składnia niejawnego wywołania procedury `Set` jest następująca:

```vb
propertyname[(argumentlist)] = expression
```

Składnia niejawnego wywołania procedury `Get` jest następująca:

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołania

Następująca właściwość przechowuje pełną nazwę jako dwie nazwy składników, imię i nazwisko. Gdy wywołujący kod odczytuje `fullName`, procedura `Get` łączy dwa nazwy składników i zwraca pełną nazwę. Gdy wywołujący kod przypisze nową pełną nazwę, procedura `Set` próbuje podzielić ją na dwie nazwy składników. Jeśli nie znajdzie miejsca, będzie ono przechowywane jako imię i nazwisko.

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

W poniższym przykładzie przedstawiono typowe wywołania procedur właściwości `fullName`:

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a>Zobacz także

- [Procedury](index.md)
- [Procedury funkcji](function-procedures.md)
- [Procedury operatorów](operator-procedures.md)
- [Parametry i argumenty procedur](procedure-parameters-and-arguments.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](how-to-create-a-property.md)
- [Instrukcje: wywoływanie procedury właściwości](how-to-call-a-property-procedure.md)
- [Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](how-to-declare-and-call-a-default-property.md)
- [Instrukcje: umieszczanie wartości we właściwości](how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](how-to-get-a-value-from-a-property.md)
