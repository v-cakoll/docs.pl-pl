---
title: Używanie delegatów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: b27c94570fdf76808e8a7df67b34466bde20de7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-delegates-c-programming-guide"></a>Używanie delegatów (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) jest typem, który hermetyzuje bezpieczne metody podobne do wskaźnika funkcji w C i C++. W przeciwieństwie do wskaźników funkcji C delegatów zorientowane obiektowo, wpisz bezpieczne i bezpieczne. Typ delegata jest zdefiniowany przez nazwę obiektu delegowanego. Poniższy przykład deklaruje delegata o nazwie `Del` które hermetyzują metody pobierającej [ciąg](../../../csharp/language-reference/keywords/string.md) jako argument i zwraca [void](../../../csharp/language-reference/keywords/void.md):  
  
 [!code-csharp[csProgGuideDelegates#21](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_1.cs)]  
  
 Obiektu delegowanego jest zwykle tworzony przez zapewniające nazwę metody obiektu delegowanego będzie zawijany, lub z [metody anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Po utworzeniu delegata wywołania metody delegata zostaną przekazane przez delegata do tej metody. Parametry przekazane do delegata przez obiekt wywołujący są przekazywane do metody i zwracanej wartości, jeśli z metody jest zwracany do obiektu wywołującego przez obiekt delegowany. Jest to nazywane wywoływania obiektu delegowanego. Tak, jakby była metody opakowana można wywołać delegata wystąpień. Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#22](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_2.cs)]  
  
 [!code-csharp[csProgGuideDelegates#23](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_3.cs)]  
  
 Typy delegatów są pochodnymi <xref:System.Delegate> klasa w programie .NET Framework. Typy delegatów są [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md)— nie może pochodzić od — i nie jest możliwe określenie klas niestandardowych z <xref:System.Delegate>. Ponieważ wystąpień obiektu delegowanego jest obiektem, możesz można przekazać jako parametru lub przypisane do właściwości. Zapewnia metody zaakceptować delegata jako parametr i wywołać delegata w późniejszym czasie. To jest znany jako asynchroniczne wywołanie zwrotne i jest powszechnie używaną metodą powiadamianie obiekt wywołujący, które długie proces został zakończony. W przypadku delegata w ten sposób kodu za pomocą obiektu delegowanego nie musi znać implementacji metody używane. Funkcjonalność jest podobny do hermetyzacja zapewniają interfejsów.  
  
 Inne typowe zastosowanie wywołań zwrotnych jest definiowanie metody niestandardowe porównania i przekazywanie tego delegata do metody sortowania. Umożliwia on kodu wywołującego stać się częścią algorytm sortowania. Następujący przykład metody używa `Del` typu jako parametr:  
  
 [!code-csharp[csProgGuideDelegates#24](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_4.cs)]  
  
 Można następnie przekazać delegata utworzone powyżej do tej metody:  
  
 [!code-csharp[csProgGuideDelegates#25](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_5.cs)]  
  
 uprawnia do następujących danych wyjściowych do konsoli:  
  
 `The number is: 3`  
  
 Używanie delegata jako abstrakcji `MethodWithCallback` nie trzeba wywoływać bezpośrednio z konsoli — nie musi zostać zaprojektowana z konsolą pamiętać. Co `MethodWithCallback` jest to po prostu przygotowanie ciągu i przekazać ciąg do innej metody. Jest to szczególnie wydajne, ponieważ delegowanego metoda może używać dowolnej liczby parametrów.  
  
 Gdy delegata jest utworzony opakowywać metody wystąpienia, delegat odwołuje się zarówno wystąpienie, jak i metody. Delegat nie zna typu wystąpienia jako uzupełnienie metodę, która jest zawijany, tak jak brak metody dla tego obiektu, który pasującego do podpisu delegata delegata mogą odwoływać się do dowolnego typu obiektu. Gdy delegata jest utworzony opakowywać metodą statyczną, odwołuje się tylko metody. Rozważ następujące deklaracje:  
  
 [!code-csharp[csProgGuideDelegates#26](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_6.cs)]  
  
 Wraz ze statycznego `DelegateMethod` pokazano wcześniej, teraz mamy trzy metody, które można zawijać za `Del` wystąpienia.  
  
 Delegat można wywołać więcej niż jedną metodę, gdy została wywołana. Jest to określane jako multiemisji. Aby dodać dodatkową metodę do listy metod delegata — listy wywołania — wystarczy dodanie dwóch obiektów delegowanych za pomocą dodawania lub dodanie operatory przypisania ("+" lub "+="). Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#27](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_7.cs)]  
  
 W tym momencie `allMethodsDelegate` zawiera trzy metody na swojej liście wywołania —`Method1`, `Method2`, i `DelegateMethod`. Oryginalny trzech delegatów, `d1`, `d2`, i `d3`, pozostają niezmienione. Gdy `allMethodsDelegate` jest wywołane, wszystkie trzy metody są wywoływane w kolejności. Jeśli delegat używa parametrów odwołania, odwołanie jest przekazywany sekwencyjnie do każdego z trzech metod z kolei, a wszelkie zmiany wprowadzone przez jedną metodę będą widoczne dla next — metoda. Po dowolnej z metod zgłasza wyjątek, który nie jest zgłoszony w metodzie, czy wyjątek jest przekazywany do wywołującego delegata i żadne kolejne metody na liście wywołania są nazywane. Jeśli delegat ma wartość zwracaną i/lub parametrów out, zwraca wartość zwracaną i parametry ostatniego metody wywoływane. Aby usunąć metodę z listy wywołania, użyj zmniejszyć lub zmniejszenie operator przypisania ("-" lub "-="). Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#28](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_8.cs)]  
  
 Ponieważ typy delegatów są pochodnymi `System.Delegate`, można wywołać metody i właściwości zdefiniowane przez tę klasę w delegacie. Na przykład aby znaleźć wiele metod delegata wywołania liście, można wpisywać:  
  
 [!code-csharp[csProgGuideDelegates#29](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_9.cs)]  
  
 Delegatów o więcej niż jednej metody na liście wywołania pochodzi od <xref:System.MulticastDelegate>, która jest podklasą klasy `System.Delegate`. Powyższy kod działa w obu przypadkach, ponieważ obsługuje zarówno klasy `GetInvocationList`.  
  
 Obiekty delegowane multiemisji są często używane w obsłudze zdarzeń. Obiekty źródła zdarzeń Wysyłaj powiadomienia o zdarzeniach do adresatów obiektów, które zostały zarejestrowane do otrzymania tego zdarzenia. Aby zarejestrować dla zdarzenia, odbiorca tworzy metodę przeznaczone do obsługi zdarzeń, a następnie tworzy delegowanego dla tej metody i przekazuje delegat źródło zdarzenia. Źródło wywołuje delegata po wystąpieniu zdarzenia. Delegat wywołuje zdarzenie obsługi metody na odbiorcy, dostarczając danych zdarzenia. Typ obiektu delegowanego dla danego zdarzenia jest zdefiniowana przez źródło zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../csharp/programming-guide/events/index.md).  
  
 Porównywanie delegatów dwa różne typy przypisane w czasie kompilacji spowoduje błąd kompilacji. W przypadku wystąpienia delegata statycznie typu `System.Delegate`, następnie porównania jest dozwolone, ale będą wykonywać zwróci wartość false w czasie. Na przykład:  
  
 [!code-csharp[csProgGuideDelegates#30](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_10.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
 [Korzystanie z wariancji w delegatach](http://msdn.microsoft.com/library/e6acad03-93e0-4efb-a158-8696d5eb4ecf)  
 [Wariancje w delegatach](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)  
 [Korzystanie z wariancji dla delegatów ogólnych Func i Action](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)
