---
title: Składowe w postaci wyrażeń — C# Przewodnik programowania
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711990"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Elementy członkowskie z wyrażeniami (C# Przewodnik programowania)

Definicje treści wyrażenia pozwalają zapewnić implementację elementu członkowskiego w bardzo zwięzłej, czytelnej postaci. Można użyć definicji treści wyrażenia za każdym razem, gdy logika dowolnego obsługiwanego elementu członkowskiego, takiego jak metoda lub właściwość, składa się z jednego wyrażenia. Definicja treści wyrażenia ma następującą składnię ogólną:

```csharp
member => expression;
```

*wyrażenie* WHERE jest prawidłowym wyrażeniem.

Obsługa definicji treści wyrażenia została wprowadzona dla metod i właściwości tylko do odczytu w C# 6 i została rozwinięta w C# 7,0. Definicje treści wyrażenia mogą być używane z elementami członkowskimi typu wymienionymi w poniższej tabeli:

|Element członkowski  |Obsługiwane przez... |
|---------|---------|
|[— Metoda](#methods)  |C# 6 |
|[Właściwość tylko do odczytu](#read-only-properties)   |C# 6  |
|[Property](#properties)  |C# 7.0 |
|[Konstruktora](#constructors)   |C# 7.0 |
|[Finalizator](#finalizers)     |C# 7.0 |
|[Indeksator](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda zabudowana wyrażenia składa się z pojedynczego wyrażenia, które zwraca wartość, której typ pasuje do typu zwracanego metody, lub dla metod, które zwracają `void`, który wykonuje pewne operacje. Na przykład typy, które zastępują metodę <xref:System.Object.ToString%2A>, zazwyczaj zawierają pojedyncze wyrażenie, które zwraca reprezentację ciągu bieżącego obiektu.

W poniższym przykładzie zdefiniowano klasę `Person`, która zastępuje metodę <xref:System.Object.ToString%2A> z definicją treści wyrażenia. Definiuje również metodę `DisplayName`, która wyświetla nazwę konsoli programu. Należy zauważyć, że słowo kluczowe `return` nie jest używane w definicji treści wyrażenia `ToString`.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Aby uzyskać więcej informacji, zobacz [metodyC# (Przewodnik programowania)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Właściwości tylko do odczytu

Począwszy od C# 6, można użyć definicji treści wyrażenia, aby zaimplementować właściwość tylko do odczytu. W tym celu należy użyć następującej składni:

```csharp
PropertyType PropertyName => expression;
```

W poniższym przykładzie zdefiniowano klasę `Location`, której Właściwość `Name` tylko do odczytu jest zaimplementowana jako definicja treści wyrażenia, która zwraca wartość pola `locationName` prywatnego:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości (C# Przewodnik programowania)](../classes-and-structs/properties.md).

## <a name="properties"></a>Właściwości

Począwszy od C# 7,0, można użyć definicji treści wyrażenia do implementowania właściwości `get` i `set` metod dostępu. Poniższy przykład ilustruje, jak to zrobić:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości (C# Przewodnik programowania)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktorzy

Definicja treści wyrażenia dla konstruktora zwykle składa się z pojedynczego wyrażenia przypisania lub wywołania metody, które obsługuje argumenty konstruktora lub inicjuje stan wystąpienia.

W poniższym przykładzie zdefiniowano klasę `Location`, której Konstruktor ma jeden parametr ciągu o nazwie *name*. Definicja treści wyrażenia przypisuje argument do właściwości `Name`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [konstruktory (C# Przewodnik programowania)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizatory

Definicja treści wyrażenia dla finalizatora zwykle zawiera instrukcje czyszczenia, takie jak instrukcje zwalniania niezarządzanych zasobów.

W poniższym przykładzie zdefiniowano finalizator, który używa definicji treści wyrażenia, aby wskazać, że finalizator został wywołany.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [finalizatoryC# (Przewodnik programowania)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indeksatory

Podobnie jak w przypadku właściwości, `get` indeksatora i Akcesory `set` składają się z definicji treści wyrażenia, jeśli metoda dostępu `get` składa się z jednego wyrażenia, które zwraca wartość lub metoda dostępu `set` wykonuje proste przypisanie.

W poniższym przykładzie zdefiniowano klasę o nazwie `Sports`, która zawiera wewnętrzną tablicę <xref:System.String>, która zawiera nazwy wielu sportów. Zarówno metody dostępu indeksatora `get`, jak i `set` są implementowane jako definicje treści wyrażenia.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Aby uzyskać więcej informacji, zobacz [IndeksatoryC# (Przewodnik programowania)](../indexers/index.md).
