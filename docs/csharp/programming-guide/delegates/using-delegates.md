---
title: Używanie delegatów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: eb5721d1c04ad761821bcdae03159f290a802ec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711164"
---
# <a name="using-delegates-c-programming-guide"></a>Używanie delegatów (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) to typ, który hermetyzuje bezpiecznie metody, podobne do wskaźnika funkcji w C i C++. W przeciwieństwie do wskaźników funkcji języka C obiekty delegowane są zorientowane obiektowo, typu, bezpieczeństwa i bezpieczne. Typ obiektu delegowanego jest definiowany przez nazwę obiektu delegowanego. Poniższy przykład deklaruje delegat o nazwie `Del` który umożliwiająca Hermetyzowanie metody, która przyjmuje [ciąg](../../../csharp/language-reference/keywords/string.md) jako argument i zwraca [void](../../../csharp/language-reference/keywords/void.md):  
  
 [!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]  
  
 Obiektu delegowanego jest zwykle tworzony przez realizacji nazwę metody delegata będzie zawijany lub za pomocą [metody anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Po utworzeniu delegata wywołania metody delegata zostaną przekazane przez delegata do tej metody. Parametry przekazane do obiektu delegowanego przez obiekt wywołujący jest przekazywany do metody i zwracanej wartości, z metody jest zwracany do obiektu wywołującego przez delegata. Jest to nazywane wywoływania delegata. Może być wywoływany delegat wystąpień, tak jakby opakowana sama metoda. Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  
  
 [!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]  
  
 Typy delegatów są uzyskiwane z <xref:System.Delegate> klasy w .NET Framework. Typy delegatów są [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md)— nie mogą pochodzić z — i nie jest możliwe określenie niestandardowych klas z <xref:System.Delegate>. Ponieważ wystąpień delegata jest obiektem, jego mogą być przekazany jako parametr lub przypisane do właściwości. Dzięki temu metodę, aby zaakceptować delegata jako parametr, a następnie wywołaj delegat w późniejszym czasie. Jest znany jako asynchroniczne wywołanie zwrotne, a metoda jest często powiadamiania obiekt wywołujący, po ukończeniu procesu długie. Gdy obiekt delegowany jest używany w ten sposób, kod przy użyciu delegat nie musi żadnej wiedzy implementacji metody używane. Funkcje są podobne do hermetyzacji, podane przez interfejsy.  
  
 Innym typowym zastosowaniem wywołań zwrotnych jest definiowanie metody porównania niestandardowego i przekazanie delegata do metody sortowania. Umożliwia ona wywołującego kod, aby stać się częścią algorytmu sortowania. Poniższy przykład metody używa `Del` typu jako parametru:  
  
 [!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]  
  
 Możesz następnie przekazać delegata utworzone powyżej do tej metody:  
  
 [!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]  
  
 i pojawić się następujące dane wyjściowe do konsoli:  
  
 `The number is: 3`  
  
 Używanie delegata jako klasą abstrakcyjną `MethodWithCallback` nie trzeba wywoływać bezpośrednio z konsoli — nie musi być zaprojektowane tak, za pomocą konsoli, należy pamiętać. Co `MethodWithCallback` jest to po prostu przygotowanie ciągu i przekaż parametry do innej metody. Jest to szczególnie wydajne, ponieważ metoda delegowanego można użyć dowolnej liczbie parametrów.  
  
 Gdy obiekt delegowany jest konstruowany opakowywać metodą wystąpienia, delegat odwołuje się do wystąpienia i metody. Delegat nie zna typu wystąpienia jako uzupełnienie metody, który otacza, więc tak długo, jak dla tego obiektu, który jest zgodny podpis delegata ma metodę delegata może odwoływać się do dowolnego typu obiektu. Gdy obiekt delegowany jest konstruowany opakowywać metodę statyczną, tylko odwołania metody. Rozważ następujące deklaracje:  
  
 [!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]  
  
 Wraz ze statycznej `DelegateMethod` przedstawionego wcześniej, mamy trzy metody, które może zostać zawinięty przy `Del` wystąpienia.  
  
 Delegata można wywołać więcej niż jednej metody po wywołaniu. Jest to określane jako multiemisji. Aby dodać dodatkową metodę do listy pełnomocnika metod — listy wywołań — po prostu wymaga dodania dwóch delegatów za pomocą dodawania lub operatorów przypisania dodawania ("+" lub "+="). Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]  
  
 W tym momencie `allMethodsDelegate` zawiera trzy metody na liście wywołania —`Method1`, `Method2`, i `DelegateMethod`. Oryginalny trzech obiektów delegowanych `d1`, `d2`, i `d3`, pozostają niezmienione. Gdy `allMethodsDelegate` jest wywołana, wszystkie trzy metody są wywoływane w kolejności. Jeśli delegat używa parametrów w formie odwołań, odwołanie jest przekazywany sekwencyjnie do każdego z trzech metod z kolei, a wszelkie zmiany według jedną z metod są widoczne dla następnej metody. Gdy dowolnej z metod zgłasza wyjątek, który nie jest wyłapywany wewnątrz metody, że wyjątek jest przekazywany do obiektu wywołującego delegat i żadne kolejne metody na liście wywołania są wywoływane. Jeśli pełnomocnik ma wartość zwracaną i/lub parametrów out, zwraca wartość zwracaną i parametry ostatniego metody wywoływane. Aby usunąć metodę liście wywołania, należy użyć dekrementacji lub dekrementacja, operator przypisania ("-" lub "-="). Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]  
  
 Ponieważ typy delegatów są uzyskiwane z `System.Delegate`, można wywołać metody i właściwości zdefiniowane przez tę klasę w delegacie. Na przykład aby znaleźć wiele metod w listy wywołań obiektu delegowanego, użytkownik może zapisać:  
  
 [!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]  
  
 Delegaty z więcej niż jednej metody na liście wywołań pochodzi od <xref:System.MulticastDelegate>, który jest podklasą `System.Delegate`. Powyższy kod działa w obu przypadkach, ponieważ obsługuje obie klasy `GetInvocationList`.  
  
 Obiekty delegowane multiemisji są często używane w obsłudze zdarzeń. Obiekty źródła zdarzeń Wysyłaj powiadomienia o zdarzeniach do adresatów obiektów, które zostały zarejestrowane do otrzymywania tego zdarzenia. Zarejestrować zdarzenie, odbiorca tworzy metodę z myślą o obsłudze zdarzeń, a następnie tworzy delegata dla tej metody i przekazuje delegata do źródła zdarzenia. Po wystąpieniu zdarzenia, źródło wywołuje delegata. Delegat następnie wywołuje metodę na odbiorca, dostarczanie danych zdarzenia do obsługi zdarzeń. Typ delegata dla danego zdarzenia jest definiowany przez źródło zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../csharp/programming-guide/events/index.md).  
  
 Porównywanie delegatów dwa różne typy przypisane w czasie kompilacji spowoduje błąd kompilacji. W przypadku wystąpień delegata statycznie typu `System.Delegate`, następnie wynik porównania jest dozwolone, ale będzie uruchamiany zwróci wartość false w czasie. Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
- [Korzystanie z wariancji w delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Wariancje w delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Korzystanie z wariancji dla delegatów ogólnych Func i Action](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
