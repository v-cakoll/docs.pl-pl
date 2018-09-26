---
title: Delegaty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 96de5601c60dd309fe5467414affd20b8bc93d87
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087479"
---
# <a name="delegates-c-programming-guide"></a>Delegaty (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) to typ, który reprezentuje odwołania do metod z określoną listą parametrów i typ zwracany. Podczas tworzenia wystąpienia delegata można skojarzyć jego wystąpienie z dowolną metodą mającą zgodny podpis i zwracany typ. Za pośrednictwem wystąpienia delegata można wywołać metodę.  
  
 Delegaty służą do przekazywania metod jako argumentów do innych metod. Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Użytkownik tworzy metodę niestandardową, a klasa, taka jak formant systemu Windows, może wywołać tę metodę, gdy wystąpi określone zdarzenie. W poniższym przykładzie pokazano deklarację delegata:  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 Do delegata można przypisać każdą metodę z dowolnej dostępnej klasy lub struktury, która pasuje do typu delegata. Może to być metoda statyczna lub metoda wystąpienia. Umożliwia to programowe zmienianie wywołań metod, a także podłączanie nowego kodu do istniejących klas.  
  
> [!NOTE]
>  W kontekście przeciążania metod podpis metody nie zawiera wartości zwracanej. Jednak w kontekście delegatów podpis zawiera wartość zwracaną. Innymi słowy metoda musi mieć taki sam zwracany typ jak delegat.  
  
 Ta możliwość odwoływania się do metody jak do parametru sprawia, że delegaty idealnie nadają się do definiowania metod wywoływania zwrotnego. Na przykład odwołanie do metody, która porównuje dwa obiekty można przekazać jako argument do algorytmu sortowania. Kod porównania znajduje się w osobnej procedurze, więc algorytm sortowania można napisać w bardziej ogólny sposób.  
  
## <a name="delegates-overview"></a>Omówienie delegatów  
 Delegaty mają następujące właściwości:  
  
-   Delegaty są podobne do wskaźników funkcji języka C++, ale obiekty delegowane są w pełni zorientowane obiektowo, a w przeciwieństwie do języka C++ wskaźników do składowych, delegatów hermetyzacji zarówno w przypadku wystąpienia obiektu, jak i metody.
  
-   Delegaty zezwalają na przekazywanie metod jako parametrów.  
  
-   Delegatów można używać do definiowania metod wywoływania zwrotnego.  
  
-   Delegaty można łączyć w łańcuch; na przykład w jednym zdarzeniu można wywołać wiele metod.  
  
-   Metody nie muszą dokładnie pasować do typu delegata. Aby uzyskać więcej informacji, zobacz [przy użyciu wariancje w Delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
-   C# w wersji 2.0 wprowadzono koncepcję [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), które umożliwiają bloków kodu, które zostaną przekazane jako parametry, zamiast oddzielnie definiowanej metody. W języku C# 3.0 wprowadzono wyrażenia lambda, które stanową wygodniejszy sposób pisania bloków kodu w tekście. Zarówno metody anonimowe, jak i wyrażenia lambda (w pewnych kontekstach) są kompilowane na typy delegatów. Te funkcje są obecnie nazywane łącznie funkcjami anonimowymi. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Używanie delegatów](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [Kiedy należy używać obiektów delegowanych zamiast interfejsów (C# Programming Guide)](https://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [Delegaci z metodami nazwanymi lub anonimowymi](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Korzystanie z wariancji w delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Instrukcje: deklarowanie, tworzenie wystąpień i użycie delegowania](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegatów, zdarzeń i wyrażenia Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) w [C# 3.0 Cookbook, wydanie trzecie: ponad 250 rozwiązań dla programistów C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegaci i zdarzenia](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) w [Nauka języka C# 3.0: Opanuj podstawy języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
