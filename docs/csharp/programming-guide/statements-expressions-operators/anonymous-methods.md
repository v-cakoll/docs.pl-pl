---
title: Metody anonimowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 7f6c596dcc73cdfb335071f57aab18e836ceaae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-methods-c-programming-guide"></a>Metody anonimowe (Przewodnik programowania w języku C#)
W wersjach C# przed 2.0, jedynym sposobem, aby zadeklarować [delegować](../../../csharp/language-reference/keywords/delegate.md) było jednoczesne używanie [o nazwie metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). C# 2.0 wprowadzono metody anonimowe i w języku C# 3.0 lub nowszej, wyrażenia lambda zastępują metod anonimowych jako preferowany sposób pisania kodu wbudowanego. Jednak informacje o metodach anonimowy w tym temacie dotyczą również wyrażenia lambda. Istnieje jeden przypadek, w którym metody anonimowej udostępnia funkcje nie znaleziono w wyrażeniach lambda. Metody anonimowe umożliwiają Pomiń listy parametrów. Oznacza to, że metody anonimowej można przekonwertować na delegatów o różnych podpisów. To nie jest możliwe za pomocą wyrażenia lambda. Aby uzyskać więcej informacji, w szczególności o wyrażenia lambda, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Tworzenie metody anonimowe to zasadniczo sposób przekazać jako parametru delegowanego blok kodu. Poniżej przedstawiono dwa przykłady:  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 Za pomocą metody anonimowe, można zmniejszyć kodowanie nakładów pracy, w tworzenie wystąpień obiektów delegowanych, ponieważ nie należy utworzyć oddzielny — metoda.  
  
 Na przykład określenie blok kodu zamiast Delegat może być przydatne w sytuacji, gdy konieczności tworzenia metody mogą wydawać się niepotrzebne koszty. Dobrym przykładem może być, po uruchomieniu nowego wątku. Tworzy wątku tej klasy, a także zawiera kod, który wykonuje wątek bez tworzenia dodatkową metodę dla obiektu delegowanego.  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>Uwagi  
 Zakres parametrów metody anonimowej jest *anonimowych bloku metody*.  
  
 Błąd ma zestawienie szybkiego dostępu, takich jak [goto](../../../csharp/language-reference/keywords/goto.md), [podziału](../../../csharp/language-reference/keywords/break.md), lub [kontynuować](../../../csharp/language-reference/keywords/continue.md), wewnątrz bloku metody anonimowej, jeśli element docelowy jest poza blokiem. Istnieje również błąd ma zestawienie szybkiego dostępu, takich jak `goto`, `break`, lub `continue`, spoza bloku metody anonimowej, jeśli element docelowy znajduje się wewnątrz bloku.  
  
 Zmienne lokalne i parametrów, których zakres zawiera deklarację metody anonimowej są nazywane *zewnętrzne* zmienne metody anonimowej. Na przykład w następujących segment kodu `n` jest zmienną zewnętrznych:  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Odwołanie do zmiennej zewnętrzne `n` jest określany jako *przechwycone* utworzenia delegata. W przeciwieństwie do zmiennych lokalnych okres istnienia przechwyconej zmiennej rozszerza do momentu przyznania wyrzucanie elementów bezużytecznych delegatów, które odwołują się metody anonimowe.  
  
 Nie ma dostępu do metody anonimowej [w](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry zewnętrznym zakresie.  
  
 Nie niebezpieczny kod jest dostępny w ramach *anonimowych bloku metody*.  
  
 Metody anonimowe nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa sposoby tworzenia wystąpienia delegata:  
  
-   Skojarzenie delegata z metody anonimowej.  
  
-   Skojarzenie delegata z metodę o nazwie (`DoWork`).  
  
 W każdym przypadku gdy jest wywoływany delegat zostanie wyświetlony komunikat.  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
 [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Delegaci z metodami nazwanymi lub anonimowymi](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
