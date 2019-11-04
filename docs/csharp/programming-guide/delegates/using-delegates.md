---
title: Korzystanie z delegatów — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: a0422b5cd3083f351bde44deae5871599a649140
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423298"
---
# <a name="using-delegates-c-programming-guide"></a>Używanie delegatów (Przewodnik programowania w języku C#)

[Delegat](../../language-reference/builtin-types/reference-types.md) jest typem, który bezpiecznie hermetyzuje metodę, podobną do wskaźnika funkcji w C i C++. W przeciwieństwie do wskaźników funkcji języka C, Delegaty są zorientowane obiektowo, typu bezpieczne i bezpieczne. Typ delegata jest definiowany przy użyciu nazwy delegata. Poniższy przykład deklaruje delegata o nazwie `Del`, który może hermetyzować metodę, która pobiera [ciąg](../../language-reference/builtin-types/reference-types.md) jako argument i zwraca wartość [void](../../language-reference/keywords/void.md):

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Obiekt delegata jest zwykle tworzony przez podanie nazwy metody, która zostanie zawinięty przez delegata, lub za pomocą [funkcji anonimowej](../statements-expressions-operators/anonymous-functions.md). Po utworzeniu wystąpienia delegata wywołanie metody przesłane do delegata zostanie przesłane przez delegata do tej metody. Parametry przesłane do delegata przez obiekt wywołujący są przesyłane do metody, a wartość zwracana, jeśli istnieje, jest zwracana do obiektu wywołującego przez delegata. Jest to nazywane wywołaniem delegata. Obiekt delegowany skonkretyzowany może być wywoływany tak, jakby była metodą opakowaną. Na przykład:

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

Typy delegatów są wyprowadzane z klasy <xref:System.Delegate> w .NET Framework. Typy delegatów są [zapieczętowane](../../language-reference/keywords/sealed.md)— nie mogą być wyprowadzane z — i nie można utworzyć klas niestandardowych z <xref:System.Delegate>. Ponieważ delegat skonkretyzowany jest obiektem, może być przekazane jako parametr lub przypisany do właściwości. Dzięki temu Metoda akceptuje delegata jako parametr i Wywołaj delegata w późniejszym czasie. Jest to znane jako asynchroniczne wywołanie zwrotne i jest typową metodą powiadamiania obiektu wywołującego po zakończeniu długotrwałego procesu. Gdy delegat jest używany w ten sposób, kod korzystający z delegata nie potrzebuje żadnej znajomości implementacji używanej metody. Funkcje są podobne do interfejsów hermetyzacji.

Innym typowym użyciem wywołań zwrotnych jest Definiowanie niestandardowej metody porównania i przekazywanie tego delegata do metody sortowania. Pozwala na to, aby kod obiektu wywołującego stał się częścią algorytmu sortowania. W poniższym przykładzie metoda używa typu `Del` jako parametru:

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Następnie można przekazać delegata utworzony powyżej do tej metody:

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

i otrzymają następujące dane wyjściowe do konsoli:

```console
The number is: 3
```

Przy użyciu delegata jako abstrakcji `MethodWithCallback` nie musi bezpośrednio wywoływać konsoli — nie musi być ona zaprojektowana z uwzględnieniem konsoli. Co `MethodWithCallback` to po prostu przygotowanie ciągu i przekazanie ciągu do innej metody. Jest to szczególnie zaawansowane, ponieważ metoda delegowana może używać dowolnej liczby parametrów.

Gdy delegat jest skonstruowany do zawijania metody instancji, delegat odwołuje się zarówno do wystąpienia, jak i metody. Delegat nie ma informacji o typie wystąpienia poza metodą, która go otacza, więc delegat może odwoływać się do dowolnego typu obiektu, o ile istnieje metoda dla tego obiektu, która pasuje do sygnatury delegata. Gdy delegat jest skonstruowany do zawijania metody statycznej, odwołuje się tylko do metody. Rozważ następujące deklaracje:

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

Wraz ze statyczną `DelegateMethod` pokazana wcześniej, mamy teraz trzy metody, które mogą być opakowane przez wystąpienie `Del`.

Delegat może wywołać więcej niż jedną metodę w przypadku wywołania. Nazywa się to multiemisją. Aby dodać dodatkową metodę do listy metod delegatów — Lista wywołań — wystarczy dodać dwa Delegaty przy użyciu operatora przypisania dodawania lub dodawania ("+" lub "+ ="). Na przykład:

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

W tym momencie `allMethodsDelegate` zawiera trzy metody na liście wywołań — `Method1`, `Method2` i `DelegateMethod`. Oryginalne trzy Delegaty, `d1`, `d2` i `d3`, pozostaną bez zmian. Gdy zostanie wywołana `allMethodsDelegate`, wszystkie trzy metody są wywoływane w kolejności. Jeśli delegat używa parametrów referencyjnych, odwołanie jest przesyłane sekwencyjnie do każdej z trzech metod z kolei, a wszelkie zmiany według jednej metody są widoczne dla następnej metody. Gdy którakolwiek z metod zgłasza wyjątek, który nie jest przechwytywany w ramach metody, ten wyjątek jest przesyłany do obiektu wywołującego delegata i nie są wywoływane kolejne metody z listy wywołań. Jeśli delegat ma wartość zwracaną i/lub parametry out, zwraca wartość zwracaną i parametry ostatniej wywołanej metody. Aby usunąć metodę z listy wywołań, użyj [operatorów odejmowania lub odejmowania](../../language-reference/operators/subtraction-operator.md) (`-` lub `-=`). Na przykład:

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Ponieważ typy delegatów pochodzą z `System.Delegate`, metody i właściwości zdefiniowane przez tę klasę mogą być wywoływane w delegatze. Na przykład aby znaleźć liczbę metod na liście wywołań delegata, można napisać:

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Delegaty z więcej niż jedną metodą na liście wywołań pochodzą z <xref:System.MulticastDelegate>, która jest podklasą `System.Delegate`. Powyższy kod działa w obu przypadkach, ponieważ obie klasy obsługują `GetInvocationList`.

Delegaty multiemisji są szeroko używane w obsłudze zdarzeń. Obiekty źródłowe zdarzeń wysyłają powiadomienia o zdarzeniach do obiektów adresatów, które zostały zarejestrowane w celu otrzymania tego zdarzenia. Aby zarejestrować się na potrzeby zdarzenia, odbiorca tworzy metodę zaprojektowaną do obsługi zdarzenia, a następnie tworzy delegata dla tej metody i przekazuje delegata do źródła zdarzeń. Źródło wywołuje delegata, gdy wystąpi zdarzenie. Delegat następnie wywołuje metodę obsługi zdarzeń na odbiorcy, dostarczając dane zdarzenia. Typ delegata dla danego zdarzenia jest definiowany przez Źródło zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../events/index.md).

Porównywanie delegatów dwóch różnych typów przypisanych w czasie kompilacji spowoduje błąd kompilacji. Jeśli wystąpienia delegatów są statycznie typu `System.Delegate`, wówczas porównanie jest dozwolone, ale zwróci wartość false w czasie wykonywania. Na przykład:

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Delegaci](./index.md)
- [Korzystanie z wariancji w delegatach](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Wariancje w delegatach](../concepts/covariance-contravariance/variance-in-delegates.md)
- [Korzystanie z wariancji dla delegatów ogólnych Func i Action](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Zdarzenia](../events/index.md)
