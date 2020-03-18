---
title: Elementy członkowskie zabudowane wyrażeniem — przewodnik programowania języka C#
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711990"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Elementy członkowskie zabudowane wyrażeniem (przewodnik programowania Języka C#)

Definicje treści wyrażeń umożliwiają podanie implementacji członka w bardzo zwięzłej, czytelnej formie. Definicji treści wyrażenia można użyć zawsze, gdy logika dla dowolnego obsługiwanego elementu członkowskiego, takiego jak metoda lub właściwość, składa się z pojedynczego wyrażenia. Definicja treści wyrażenia ma następującą ogólną składnię:

```csharp
member => expression;
```

gdzie *wyrażenie* jest prawidłowym wyrażeniem.

Obsługa definicji treści wyrażeń została wprowadzona dla metod i właściwości tylko do odczytu w języku C# 6 i została rozszerzona w języku C# 7.0. Definicje treści wyrażeń mogą być używane z członkami typu wymienionymi w poniższej tabeli:

|Członek  |Obsługiwane od... |
|---------|---------|
|[Metoda](#methods)  |C# 6 |
|[Właściwość tylko do odczytu](#read-only-properties)   |C# 6  |
|[Właściwość](#properties)  |C# 7.0 |
|[Konstruktor](#constructors)   |C# 7.0 |
|[Finalizatorów](#finalizers)     |C# 7.0 |
|[Indeksator](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda zabudowana wyrażeniem składa się z pojedynczego wyrażenia, które zwraca wartość, której typ `void`pasuje do typu zwracanego metody, lub dla metod, które zwracają , który wykonuje niektóre operacje. Na przykład typy, które <xref:System.Object.ToString%2A> zastępują metodę zazwyczaj zawierają pojedyncze wyrażenie, które zwraca reprezentację ciągu bieżącego obiektu.

W poniższym `Person` przykładzie definiuje klasę, <xref:System.Object.ToString%2A> która zastępuje metodę z definicji treści wyrażenia. Definiuje również `DisplayName` metodę, która wyświetla nazwę konsoli. Należy zauważyć, że `return` słowo `ToString` kluczowe nie jest używany w definicji treści wyrażenia.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Aby uzyskać więcej informacji, zobacz [Metody (Przewodnik programowania C#)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Właściwości tylko do odczytu

Począwszy od języka C# 6, można użyć definicji treści wyrażenia do zaimplementowania właściwości tylko do odczytu. Aby to zrobić, należy użyć następującej składni:

```csharp
PropertyType PropertyName => expression;
```

W poniższym `Location` przykładzie zdefiniowano `Name` klasę, której właściwość tylko do odczytu jest `locationName` implementowana jako definicja treści wyrażeń, która zwraca wartość pola prywatnego:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości (Przewodnik programowania C#)](../classes-and-structs/properties.md).

## <a name="properties"></a>Właściwości

Począwszy od języka C# 7.0, można użyć `get` `set` definicji treści wyrażenia do zaimplementowania właściwości i akcesorów. W poniższym przykładzie pokazano, jak to zrobić:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości (Przewodnik programowania C#)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktorów

Definicja treści wyrażenia dla konstruktora zazwyczaj składa się z pojedynczego wyrażenia przypisania lub wywołania metody, który obsługuje argumenty konstruktora lub inicjuje stan wystąpienia.

Poniższy przykład definiuje `Location` klasę, której konstruktor ma parametr pojedynczego ciągu *o*nazwie . Definicja treści wyrażenia przypisuje argument `Name` do właściwości.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [Konstruktory (C# Programming Guide)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizatory

Definicja treści wyrażenia dla finalizatora zazwyczaj zawiera instrukcje oczyszczania, takie jak instrukcje zwalniające zasoby niezarządzane.

W poniższym przykładzie definiuje finalizator, który używa definicji treści wyrażenia, aby wskazać, że finalizator został wywołany.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [Finalizatory (C# Programming Guide)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indexers (Indeksatory)

Podobnie jak w przypadku `get` `set` właściwości indeksatora i akcesorów składa się z definicji treści wyrażenia, jeśli `get` akcesor składa się z pojedynczego wyrażenia, które zwraca wartość lub `set` akcesor wykonuje proste przypisanie.

W poniższym przykładzie zdefiniowano klasę o nazwie, `Sports` która zawiera tablicę wewnętrzną, <xref:System.String> która zawiera nazwy liczby sportowych. Zarówno indeksatora `get` i `set` akcesorów są implementowane jako definicje treści wyrażeń.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Aby uzyskać więcej informacji, zobacz [Indeksatory (C# Programming Guide)](../indexers/index.md).
