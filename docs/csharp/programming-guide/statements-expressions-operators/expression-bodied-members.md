---
title: Elementy członkowskie z wyrażeniem - C# Programming Guide
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709994"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Elementy członkowskie z wyrażeniem (C# Podręcznik programowania)

Wyrażenie treści definicji umożliwiają zapewnienie implementacja członka w formie bardzo zwięzły, czytelny. Definicja treści wyrażenia można użyć w każdym przypadku, gdy logiki dla dowolnego z obsługiwanych elementów członkowskich, takich jak metody lub właściwości, składa się z pojedynczego wyrażenia. Definicja treści wyrażenia ma następującą składnię ogólne:

```csharp
member => expression;
```

gdzie *wyrażenie* jest prawidłowym wyrażeniem.

Wprowadzono obsługę definicji treści wyrażenia dla metod i właściwości tylko do odczytu w C# 6 i został rozszerzony w C# 7.0. Wyrażenie treści definicje mogą być używane z elementy członkowskie typu wymienione w poniższej tabeli:

|Element członkowski  |Obsługiwane, począwszy od... |
|---------|---------|
|[— Metoda](#methods)  |C# 6 |
|[Właściwość tylko do odczytu](#read-only-properties)   |C# 6  |
|[Property](#properties)  |C# 7.0 |
|[Konstruktor](#constructors)   |C# 7.0 |
|[Finalizator](#finalizers)     |C# 7.0 |
|[Indeksator](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda z wyrażeniem składa się pojedyncze wyrażenie, które zwraca wartość, którego typ jest zgodny typ zwracany metody lub, w przypadku metod zwracających `void`, który wykonuje pewne operacje. Na przykład typy zastąpienie <xref:System.Object.ToString%2A> metoda zazwyczaj zawierać pojedyncze wyrażenie, które zwraca ciąg reprezentujący bieżący obiekt.

W poniższym przykładzie zdefiniowano `Person` klasę, która zastępuje <xref:System.Object.ToString%2A> metody za pomocą definicji treści wyrażenia. Umożliwia on również definiowanie `DisplayName` metodę, która wyświetla nazwę do konsoli. Należy pamiętać, że `return` — słowo kluczowe nie jest używany w `ToString` definicja treści wyrażenia.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Aby uzyskać więcej informacji, zobacz [Methods (C# Programming Guide)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Właściwości tylko do odczytu

Począwszy od C# 6, można użyć definicji treści wyrażenia do zaimplementowania właściwość tylko do odczytu. Aby to zrobić, użyj następującej składni:

```csharp
PropertyType PropertyName => expression;
```

W poniższym przykładzie zdefiniowano `Location` klasy, których tylko do odczytu `Name` właściwość jest implementowany jako definicja treści wyrażenia, która zwraca wartość prywatna `locationName` pola:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości (C# Programming Guide)](../classes-and-structs/properties.md).

## <a name="properties"></a>Właściwości

Począwszy od C# 7.0, można użyć definicji treści wyrażenia do zaimplementowania właściwość `get` i `set` metod dostępu. Poniższy przykład pokazuje, jak to zrobić:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości (C# Programming Guide)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktorów

Definicja treści wyrażenia dla konstruktora zwykle składa się z wyrażenia przypisania pojedynczego lub wywołanie metody, która obsługuje argumentów konstruktora lub inicjuje wystąpienie przechodzi w stan.

W poniższym przykładzie zdefiniowano `Location` klasy, której Konstruktor ma jeden ciąg parametr o nazwie *nazwa*. Definicja treści wyrażenia przypisuje argument `Name` właściwości.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [konstruktorów (C# Programming Guide)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizatory

Definicja treści wyrażenia dla finalizatora zazwyczaj zawiera instrukcje czyszczenia, na przykład instrukcji, które zwolnić niezarządzane zasoby.

W poniższym przykładzie zdefiniowano finalizator, który używa definicja treści wyrażenia, aby wskazać, że finalizator została wywołana.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [finalizatory (C# Programming Guide)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indeksatory

Podobnie jak właściwości indeksatora get i set metod dostępu składają się z definicji treści wyrażenia metody dostępu get składa się z pojedynczej instrukcji, która zwraca wartość typu lub metody dostępu set wykonuje przypisanie proste.

W poniższym przykładzie zdefiniowano klasę o nazwie `Sports` zawierającą wewnętrzną <xref:System.String> tablicy, która zawiera nazwiska wielu dyscyplin sportowych. Zarówno indeksatora get, jak i metody dostępu set są implementowane jako definicje treść wyrażenia.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Aby uzyskać więcej informacji, zobacz [indeksatorów (C# Programming Guide)](../indexers/index.md).
