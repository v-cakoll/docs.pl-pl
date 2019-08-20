---
title: Operatory — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588610"
---
# <a name="operators-c-programming-guide"></a>Operatory (Przewodnik programowania w języku C#)

W C#programie *operator* jest elementem programu, który jest stosowany do co najmniej jednego *operandu* w wyrażeniu lub instrukcji. Operatory przyjmujące jeden operand, takie jak operator przyrostu (`++`) lub `new`, są określane jako operatory jednoargumentowe. Operatory, które przyjmują dwa operandy, takie jak operatory`+`arytmetyczne`*`(`/`,`-`,,), są określane jako operatory *binarne* . Jeden operator, operator warunkowy (`?:`), przyjmuje trzy operandy i jest jedynym operatorem trójskładnikowych w C#.  
  
 Poniższa instrukcja języka C# zawiera jeden operator jednoargumentowy i jeden argument operacji. Operator `++`przyrostu, modyfikuje wartość operandu `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Następująca instrukcja języka C# zawiera dwa operatory dwuargumentowe, z których każdy przyjmuje dwa argumenty operacji. Operator `=`przypisania,, ma zmienną `y` integer i wyrażenie `2 + 3` jako operandy. Wyrażenie `2 + 3` składa się z operatora dodawania i dwóch operandów, `2` i `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Argument operacji może być prawidłowym wyrażeniem zawierającym kod o dowolnej długości i może składać się z dowolnej liczby podwyrażeń. W wyrażeniu zawierającym wiele operatorów kolejność, w której są stosowane operatory jest określana według *pierwszeństwa*operatorów, *łączność*i nawiasów.  

## <a name="operator-precedence"></a>Pierwszeństwo operatorów
  
Każdy operator ma zdefiniowane pierwszeństwo. W wyrażeniu zawierającym wiele operatorów, które mają różne poziomy pierwszeństwa, pierwszeństwo operatorów określa kolejność wykonywania obliczeń tych operatorów. Na przykład następująca instrukcja przypisuje 3 do `n1`:

```csharp
n1 = 11 - 2 * 4;
```

Mnożenie jest wykonywane jako pierwsze, ponieważ mnożenie ma pierwszeństwo przed odejmowaniem.

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](../../language-reference/operators/index.md).
  
## <a name="associativity"></a>Łączność

 Gdy co najmniej dwa operatory w wyrażeniu mają takie samo pierwszeństwo, są obliczane na podstawie łączności. Operatory mające łączność do lewej strony są obliczane w kolejności od lewej do prawej. Na przykład, `x * y / z` jest oceniane jako `(x * y) / z`. Operatory mające łączność do prawej strony są obliczane w kolejności od prawej do lewej. Na przykład operator przypisania ma łączność do prawej strony. Gdyby tak nie było, poniższy kod powodowałby wystąpienie błędu.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Innym przykładem jest skojarzenie operatora Trzyelementowy ([?:](../../language-reference/operators/conditional-operator.md)) z prawej strony. Większość operatorów binarnych jest polewana.  
  
 Niezależnie od tego, czy operatory w wyrażeniu mają łączność do lewej strony, czy do prawej, argumenty operacji każdego wyrażenia są obliczane najpierw od lewej strony do prawej. W poniższych przykładach pokazano kolejność obliczania operatorów i argumentów operacji.  
  
|Instrukcja|Kolejność obliczeń|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Dodawanie nawiasów

 Używając nawiasów, można zmienić kolejność określoną przez pierwszeństwo operatorów oraz łączność. Na przykład `2 + 3 * 2` zwykle jest to 8, ponieważ operatory mnożenia mają pierwszeństwo przed operatorami dodatków. Jeśli jednak wyrażenie zostanie zapisane jako `(2 + 3) * 2`, dodanie jest oceniane przed mnożeniem, a wynikiem będzie 10. W poniższych przykładach pokazano kolejność obliczania w wyrażeniach z nawiasami. Tak jak w poprzednich przykładach argumenty operacji są obliczane przed zastosowaniem operatora.  
  
|Instrukcja|Kolejność obliczeń|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Przeładowanie operatora

Można zdefiniować zachowanie niektórych operatorów dla niestandardowych klas i struktur. Ten proces jest określany mianem *przeciążenia operatora*. Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](../../language-reference/operators/operator-overloading.md).
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Instrukcje, wyrażenia i operatory](index.md)
- [Operatory języka C#](../../language-reference/operators/index.md)
