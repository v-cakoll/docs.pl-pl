---
title: Metody anonimowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 94e9f7133c9a78ece7df5bd10cfc27c79d0652c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710007"
---
# <a name="anonymous-methods-c-programming-guide"></a>Metody anonimowe (Przewodnik programowania w języku C#)
W wersjach C# przed 2.0, jedynym sposobem, aby zadeklarować [delegować](../../../csharp/language-reference/keywords/delegate.md) było jednoczesne używanie [o nazwie metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). C# w wersji 2.0 wprowadzono metod anonimowych, a w języku C# 3.0 i nowszych wyrażenia lambda zastępują metody anonimowe jako preferowanym sposobem pisania kodu wbudowanego. Jednak informacje dotyczące metod anonimowych, w tym temacie dotyczą także wyrażeń lambda. Istnieje jeden przypadek, w którym metoda anonimowa udostępnia funkcje, nie można odnaleźć w wyrażeniach lambda. Metody anonimowe umożliwiają pominąć listę parametrów. Oznacza to, że metoda anonimowa mogą być konwertowane na obiektów delegowanych z różnymi podpisami. Nie jest to możliwe za pomocą wyrażenia lambda. Aby uzyskać konkretne informacje na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Tworzenie metod anonimowych jest zasadniczo sposób przekazania bloku kodu jako parametr delegata. Poniżej przedstawiono dwa przykłady:  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 Za pomocą metod anonimowych, zmniejszasz kodowanie obciążenie, przy użyciu programu Tworzenie wystąpień obiektów delegowanych, ponieważ nie trzeba tworzyć oddzielnych metodach.  
  
 Na przykład określając blok kodu, zamiast delegata może być przydatne w sytuacji, mając do utworzenia metody mogą wydawać się niepotrzebne koszty. Dobrym przykładem może być, po uruchomieniu nowego wątku. Ta klasa tworzy wątek i również zawiera kod, który wątek wykonuje bez tworzenia dodatkową metodę dla delegata.  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a>Uwagi  
 Zakres parametry metoda anonimowa jest *anonimowe bloku metody*.  
  
 Jest błędem instrukcja skoku, takiej jak [goto](../../../csharp/language-reference/keywords/goto.md), [podziału](../../../csharp/language-reference/keywords/break.md), lub [nadal](../../../csharp/language-reference/keywords/continue.md), wewnątrz bloku metody anonimowej, jeśli element docelowy znajduje się poza blokiem. Warto również błędem instrukcja skoku, takiej jak `goto`, `break`, lub `continue`, poza bloku metody anonimowej, jeśli element docelowy znajduje się wewnątrz bloku.  
  
 Zmienne lokalne i parametry, których zakres zawiera deklarację metody anonimowej, są nazywane *zewnętrzne* zmienne metody anonimowej. Na przykład w następujących segment kodu `n` jest zewnętrzna zmienna:  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 Odwołanie do zewnętrznej zmiennej `n` jest nazywany *przechwycone* po utworzeniu obiektu delegowanego. W przeciwieństwie do zmiennych lokalnych okres istnienia zmiennej przechwyconej rozszerza, dopóki nie kwalifikuje się do wyrzucania elementów bezużytecznych delegatów, które odwołują się metody anonimowe.  
  
 Nie ma dostępu do metody anonimowej [w](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry zakresu zewnętrznego.  
  
 Nie niebezpieczny kod jest możliwy w ciągu *anonimowe bloku metody*.  
  
 Metody anonimowe nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa sposoby tworzenia wystąpienia delegata:  
  
- Skojarzenie obiektu delegowanego z metody anonimowej.  
  
- Skojarzenie obiektu delegowanego z metody nazwanej (`DoWork`).  
  
 W obu przypadkach komunikat jest wyświetlane, gdy obiekt delegowany jest wywoływany.  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
- [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Delegaci z metodami nazwanymi lub anonimowymi](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
