---
title: Operatorzy — C# przewodnik programowania
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: fd10999066f599d819ef188e09028c64c6a5e9e6
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65064052"
---
# <a name="operators-c-programming-guide"></a>Operatory (Przewodnik programowania w języku C#)

W języku C# *operator* jest elementem programu, który jest stosowany do co najmniej jednego *operandy* w wyrażeniu lub instrukcji. Operatory przyjmujące jeden argument operacji, takich jak operator inkrementacji (`++`) lub `new`, są określane jako *jednoargumentowe* operatorów. Operatory przyjmujące dwa argumenty operacji, takie jak operatory arytmetyczne (`+`,`-`,`*`,`/`), są określane jako *binarne* operatorów. Jeden operator, operator warunkowy (`?:`), przyjmuje trzy argumenty operacji i jest jedynym operatorem trójargumentowym w języku C#.  
  
 Poniższa instrukcja języka C# zawiera jeden operator jednoargumentowy i jeden argument operacji. Operator inkrementacji `++`, modyfikuje wartość argumentu operacji `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Następująca instrukcja języka C# zawiera dwa operatory dwuargumentowe, z których każdy przyjmuje dwa argumenty operacji. Operator przypisania `=`, ma zmienną całkowitą `y` i wyrażenie `2 + 3` jako argumentów. Wyrażenie `2 + 3` zawiera dodatkowy operator i dwa operandy `2` i `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Argument operacji może być prawidłowym wyrażeniem zawierającym kod o dowolnej długości i może składać się z dowolnej liczby podwyrażeń. W wyrażeniu zawierającym wiele operatorów kolejność stosowania operatorów jest ustalana *pierwszeństwo operatorów*, *kojarzenie*i nawiasy.  

## <a name="operator-precedence"></a>Pierwszeństwo operatorów
  
Każdy operator ma zdefiniowane pierwszeństwo. W wyrażeniu zawierającym wiele operatorów, które mają różne poziomy pierwszeństwa, pierwszeństwo operatorów określa kolejność wykonywania obliczeń tych operatorów. Na przykład następująca instrukcja przypisuje wartość 3 do `n1`:

```csharp
n1 = 11 - 2 * 4;
```

Mnożenie jest wykonywane jako pierwsze, ponieważ mnożenie ma pierwszeństwo przed odejmowaniem.

Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](../../language-reference/operators/index.md).
  
## <a name="associativity"></a>Łączność

 Gdy co najmniej dwa operatory w wyrażeniu mają takie samo pierwszeństwo, są obliczane na podstawie łączności. Operatory mające łączność do lewej strony są obliczane w kolejności od lewej do prawej. Na przykład `x * y / z` jest oceniane jako `(x * y) / z`. Operatory mające łączność do prawej strony są obliczane w kolejności od prawej do lewej. Na przykład operator przypisania ma łączność do prawej strony. Gdyby tak nie było, poniższy kod powodowałby wystąpienie błędu.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Innym przykładem operator trójargumentowy ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) jest łączność do prawej strony. Większość operatory dwuargumentowe mają łączność do lewej.  
  
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

 Używając nawiasów, można zmienić kolejność określoną przez pierwszeństwo operatorów oraz łączność. Na przykład `2 + 3 * 2` zazwyczaj daje w wyniku 8, ponieważ operatory mnożne pierwszeństwo przed operatorami addytywnymi. Jednak jeśli piszesz wyrażenia jako `(2 + 3) * 2`, dodawanie zostanie wykonane przed mnożeniem, a wynik to 10. W poniższych przykładach pokazano kolejność obliczania w wyrażeniach z nawiasami. Tak jak w poprzednich przykładach argumenty operacji są obliczane przed zastosowaniem operatora.  
  
|Instrukcja|Kolejność obliczeń|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Przeładowanie operatora

Można zdefiniować zachowanie operatorów dla niestandardowych klas i struktur. Ten proces jest nazywany *przeciążenia operatora*. Aby uzyskać więcej informacji, zobacz [operatory z możliwością przeciążenia](overloadable-operators.md) i [operator](../../language-reference/keywords/operator.md) artykułu — słowo kluczowe.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Instrukcje, wyrażenia i operatory](index.md)
- [Operatory języka C#](../../language-reference/operators/index.md)
- [Słowa kluczowe operatora](../../language-reference/keywords/operator-keywords.md)
