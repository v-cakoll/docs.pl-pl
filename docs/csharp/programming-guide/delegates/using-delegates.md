---
title: Korzystanie z delegatów — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: dcc73aba738d6296a44c48aad8b66cd6fc7f4a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77448442"
---
# <a name="using-delegates-c-programming-guide"></a>Używanie delegatów (Przewodnik programowania w języku C#)

[Delegat](../../language-reference/builtin-types/reference-types.md) jest typem, który bezpiecznie hermetyzuje metodę, podobną do wskaźnika funkcji w języku C i C++. W przeciwieństwie do wskaźników funkcji C delegatów są zorientowane obiektowe, typu bezpieczne i bezpieczne. Typ pełnomocnika jest zdefiniowany przez nazwę pełnomocnika. W poniższym przykładzie deklaruje `Del` delegata o nazwie, który może hermetyzować metodę, która przyjmuje [ciąg](../../language-reference/builtin-types/reference-types.md) jako argument i zwraca [void:](../../language-reference/builtin-types/void.md)

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Obiekt delegata jest zwykle konstruowany przez podanie nazwy metody, która zostanie zawinięta przez pełnomocnika, lub z [funkcją anonimową.](../statements-expressions-operators/anonymous-functions.md) Po wystąpieniu pełnomocnika wywołanie metody wprowadzone do delegata zostaną przekazane przez pełnomocnika do tej metody. Parametry przekazywane do delegata przez obiekt wywołujący są przekazywane do metody, a wartość zwracana, jeśli istnieje, z metody jest zwracana do obiektu wywołującego przez pełnomocnika. Jest to nazywane wywoływaniem delegata. Wystąpienia pełnomocnika można wywołać tak, jakby była opakowaną metodą. Przykład:

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

Typy delegatów są uzyskiwane z <xref:System.Delegate> klasy w .NET Framework. Typy delegatów są [zapieczętowane](../../language-reference/keywords/sealed.md)— nie można ich wyprowadzić — i <xref:System.Delegate>nie można wyprowadzić klas niestandardowych z . Ponieważ wystąpienie delegata jest obiektem, może być przekazywany jako parametr lub przypisany do właściwości. Dzięki temu metoda do zaakceptowania delegata jako parametr i wywołać delegata w późniejszym czasie. Jest to nazywane wywołaniem asynchronicznym i jest częstą metodą powiadamiania obiektu wywołującego po zakończeniu długiego procesu. Gdy delegat jest używany w ten sposób, kod przy użyciu delegata nie wymaga żadnej wiedzy na temat implementacji metody używane. Funkcja jest podobna do interfejsów hermetyzacji.

Innym typowym użyciem wywołań wywołania wstecznego jest definiowanie niestandardowej metody porównania i przekazywanie tego delegata do metody sortowania. Umożliwia kod wywołującego, aby stać się częścią algorytmu sortowania. Następująca przykładowa `Del` metoda używa tego typu jako parametru:

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Następnie można przekazać pełnomocnika utworzonego powyżej do tej metody:

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

i odbieraj następujące dane wyjściowe do konsoli:

```console
The number is: 3
```

Używanie pełnomocnika jako abstrakcji `MethodWithCallback` nie musi bezpośrednio wywoływać konsoli — nie musi być zaprojektowane z myślą o konsoli. Co `MethodWithCallback` to po prostu przygotować ciąg i przekazać ciąg do innej metody. Jest to szczególnie przydatne, ponieważ delegowana metoda może używać dowolnej liczby parametrów.

Gdy pełnomocnik jest konstruowany w celu zawijania metody wystąpienia, delegat odwołuje się zarówno do wystąpienia, jak i do metody. Delegat nie ma wiedzy o typie wystąpienia oprócz metody, którą otacza, więc delegat może odwoływać się do dowolnego typu obiektu, o ile istnieje metoda na tym obiekcie, która pasuje do podpisu delegata. Gdy pełnomocnik jest skonstruowany w celu zawijania metody statycznej, odwołuje się tylko do metody. Rozważ następujące deklaracje:

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

Wraz z `DelegateMethod` statyczne pokazane wcześniej, mamy teraz trzy metody, `Del` które mogą być opakowane przez wystąpienie.

Delegat może wywołać więcej niż jedną metodę podczas wywoływania. Jest to określane jako multicasting. Aby dodać dodatkową metodę do listy metod pełnomocnika — listy wywołania — wystarczy dodać dwóch delegatów przy użyciu operatorów dodawania lub dodawania przypisania ("+" lub "+="). Przykład:

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

W tym `allMethodsDelegate` momencie zawiera trzy metody na`Method1` `Method2`liście `DelegateMethod`wywołania — , i . Pierwotna trójka `d1` `d2`delegatów `d3`, , i , pozostają niezmienione. Gdy `allMethodsDelegate` jest wywoływana, wszystkie trzy metody są wywoływane w kolejności. Jeśli pełnomocnik używa parametrów odwołania, odwołanie jest przekazywane sekwencyjnie do każdej z trzech metod z kolei, a wszelkie zmiany za pomocą jednej metody są widoczne dla następnej metody. Gdy którakolwiek z metod zgłasza wyjątek, który nie jest przechwycony w ramach metody, ten wyjątek jest przekazywany do obiektu wywołującego delegata i nie są wywoływane żadne kolejne metody na liście wywołania. Jeśli pełnomocnik ma wartość zwracaną i/lub out parametry, zwraca wartość zwracaną i parametry ostatniej wywoływanej metody. Aby usunąć metodę z listy wywołania, użyj [operatorów przypisania odejmowania lub odejmowania](../../language-reference/operators/subtraction-operator.md) (`-` lub `-=`). Przykład:

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Ponieważ typy delegatów są `System.Delegate`uzyskiwane z , metody i właściwości zdefiniowane przez tę klasę mogą być wywoływane na delegata. Na przykład, aby znaleźć liczbę metod na liście wywołania delegata, można napisać:

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Delegaci z więcej niż jedną metodą <xref:System.MulticastDelegate>na liście wywołania `System.Delegate`pochodzą z , który jest podklasą . Powyższy kod działa w obu `GetInvocationList`przypadkach, ponieważ obie klasy obsługują .

Delegatów multiemisji są szeroko stosowane w obsłudze zdarzeń. Obiekty źródła zdarzeń wysyłają powiadomienia o zdarzeniach do obiektów adresatów, które zostały zarejestrowane w celu odebrania tego zdarzenia. Aby zarejestrować się dla zdarzenia, odbiorca tworzy metodę przeznaczoną do obsługi zdarzenia, a następnie tworzy pełnomocnika dla tej metody i przekazuje pełnomocnika do źródła zdarzenia. Źródło wywołuje delegata, gdy wystąpi zdarzenie. Pełnomocnik następnie wywołuje metodę obsługi zdarzeń na adresata, dostarczając dane zdarzenia. Typ delegata dla danego zdarzenia jest zdefiniowany przez źródło zdarzenia. Aby uzyskać więcej informacji, zobacz [Wydarzenia](../events/index.md).

Porównanie delegatów dwóch różnych typów przypisanych w czasie kompilacji spowoduje błąd kompilacji. Jeśli wystąpienia delegata są statycznie typu, `System.Delegate`porównanie jest dozwolone, ale zwróci false w czasie wykonywania. Przykład:

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Delegaty](./index.md)
- [Korzystanie z wariancji w delegatach](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Wariancje w delegatach](../concepts/covariance-contravariance/variance-in-delegates.md)
- [Korzystanie z wariancji dla delegatów ogólnych Func i Action](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Zdarzenia](../events/index.md)
