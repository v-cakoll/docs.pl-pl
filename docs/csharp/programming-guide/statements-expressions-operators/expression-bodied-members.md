---
title: Elementy członkowskie zabudowanych wyrażenia (C# przewodnik programowania w języku)
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 800280ed9ceaf69b825bb2a3c2c3d0d5f829922d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332757"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Elementy członkowskie zabudowanych wyrażenia (C# Podręcznik programowania)
Wyrażenie treści definicji umożliwiają implementacji członka w postaci bardzo krótkie, który może zostać odczytany. Możesz użyć definicji treści wyrażenia zawsze, gdy logiki żadnego z obsługiwanych elementów, takich jak metody lub właściwości, składa się z jednego wyrażenia. Definicja treść wyrażenia ma następującą składnię ogólne:

```csharp
member => expression;
```

gdzie *wyrażenie* jest prawidłowym wyrażeniem. 

Wprowadzono obsługę wyrażenie treści definicji dla metod i właściwości uzyskać metod dostępu w języku C# 6 i została rozszerzona w języku C# w wersji 7.0. Definicje treść wyrażenia mogą być używane z elementami członkowskimi typu wymienione w poniższej tabeli: 

|Element członkowski  |Obsługiwane począwszy od... |
|---------|---------|
|[— Metoda](#methods)  |C# 6 |
|[Konstruktor](#constructors)   |C# 7.0 |
|[Finalizator](#finalizers)     |C# 7.0 |
|[Get właściwości](#property-get-statements)  |C# 6 |
|[Zestaw właściwości](#property-set-statements)  |C# 7.0 |
|[indeksator](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda zabudowanych wyrażenie polega na jedno wyrażenie zwracające wartości, którego typ pasuje zwracany typ metody lub, w przypadku metod zwracających `void`, który wykonuje pewne operacje. Na przykład typy zastąpienie tego <xref:System.Object.ToString%2A> metody zwykle zawierają jedno wyrażenie, które zwraca reprezentację ciągu bieżącego obiektu. 

W poniższym przykładzie zdefiniowano `Person` klasy, która zastępuje <xref:System.Object.ToString%2A> metody z definicją w treści wyrażenia. Definiuje również `Show` metodę, która wyświetla nazwę do konsoli. Należy pamiętać, że `return` — słowo kluczowe nie jest używany w `ToString` definicja treść wyrażenia.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Aby uzyskać więcej informacji, zobacz [metody (C# przewodnik programowania w języku)](../classes-and-structs/methods.md).
 
## <a name="constructors"></a>Konstruktorów

Definicja treść wyrażenia konstruktora zazwyczaj składa się z wyrażenia do jednej lub wywołanie metody obsługująca argumentów konstruktora lub Inicjuje stan wystąpienia. 

W poniższym przykładzie zdefiniowano `Location` klasy, których Konstruktor ma jeden ciąg parametru o nazwie *nazwa*. Definicja treść wyrażenia przypisuje argument `Name` właściwości.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [konstruktory (C# przewodnik programowania w języku)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizatory

Definicja treść wyrażenia finalizator zwykle zawiera instrukcje oczyszczania, na przykład instrukcji, które zwolnić zasoby niezarządzane.

W poniższym przykładzie zdefiniowano finalizatora, który używa wyrażenia treści definicji w celu wskazania, finalizator został wywołany.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [finalizatory (C# przewodnik programowania w języku)](../classes-and-structs/destructors.md).

## <a name="property-get-statements"></a>Instrukcje get właściwości

Jeśli wybierzesz do wdrożenia właściwość pobierająca metoda dostępu użytkownika, można użyć wyrażenia treści definicji dla pojedynczego wyrażeń, które po prostu zwracają wartość właściwości. Należy pamiętać, że `return` instrukcja nie jest używana.

W poniższym przykładzie zdefiniowano `Location.Name` właściwości, których właściwość metoda dostępu get zwraca wartość prywatna `locationName` pola, aby utworzyć kopię zapasową właściwości. 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Właściwości tylko do odczytu, korzystających z definicji treść wyrażenia można zaimplementować bez jawnego `set` instrukcji. Składnia jest następująca:

```csharp
PropertyName => returnValue;
```

W poniższym przykładzie zdefiniowano `Location` klasy, których tylko do odczytu `Name` właściwości jest zaimplementowany jako wyrażenie definicji treści, która zwraca wartość prywatna `locationName` pola.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Aby uzyskać więcej informacji, zobacz [właściwości (C# przewodnik programowania w języku)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Instrukcje set właściwości

Jeśli zdecydujesz się na siebie zaimplementować metodą dostępu set właściwości, można użyć wyrażenia treści definicji dla wyrażenia jeden wiersz, który przypisuje wartość do pola, aby utworzyć kopię zapasową właściwości.

W poniższym przykładzie zdefiniowano `Location.Name` właściwości, których właściwość set — instrukcja przypisuje jej argument wejściowy prywatnego `locationName` pola, aby utworzyć kopię zapasową właściwości.

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Aby uzyskać więcej informacji, zobacz [właściwości (C# przewodnik programowania w języku)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Indeksatory

Podobnie jak właściwości, indeksatora get i metody dostępu set składa się z definicji treści wyrażenia metody dostępu get składa się z jednej instrukcji, która zwraca wartość lub metody dostępu set wykonuje przypisanie proste.

W poniższym przykładzie zdefiniowano klasę o nazwie `Sports` zawierającą wewnętrznego <xref:System.String> tablica, która zawiera nazwy liczba sportowych. Zarówno indeksatora get, jak i metody dostępu set są zaimplementowane jako wyrażenie treści definicji.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Aby uzyskać więcej informacji, zobacz [indeksatorów (C# przewodnik programowania w języku)](../indexers/index.md).

