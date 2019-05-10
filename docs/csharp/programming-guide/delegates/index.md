---
title: Delegaty - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: faab42a7a2f7dda12f32a65890b795abfe0d11ca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608718"
---
# <a name="delegates-c-programming-guide"></a>Delegaty (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) to typ, który reprezentuje odwołania do metod z określoną listą parametrów i typ zwracany. Podczas tworzenia wystąpienia delegata można skojarzyć jego wystąpienie z dowolną metodą mającą zgodny podpis i zwracany typ. Za pośrednictwem wystąpienia delegata można wywołać metodę.  
  
 Delegaty służą do przekazywania metod jako argumentów do innych metod. Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Użytkownik tworzy metodę niestandardową, a klasa, taka jak formant systemu Windows, może wywołać tę metodę, gdy wystąpi określone zdarzenie. W poniższym przykładzie pokazano deklarację delegata:  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Do delegata można przypisać każdą metodę z dowolnej dostępnej klasy lub struktury, która pasuje do typu delegata. Może to być metoda statyczna lub metoda wystąpienia. Umożliwia to programowe zmienianie wywołań metod, a także podłączanie nowego kodu do istniejących klas.  
  
> [!NOTE]
>  W kontekście przeciążania metod podpis metody nie zawiera wartości zwracanej. Jednak w kontekście delegatów podpis zawiera wartość zwracaną. Innymi słowy metoda musi mieć taki sam zwracany typ jak delegat.  
  
 Ta możliwość odwoływania się do metody jak do parametru sprawia, że delegaty idealnie nadają się do definiowania metod wywoływania zwrotnego. Na przykład odwołanie do metody, która porównuje dwa obiekty można przekazać jako argument do algorytmu sortowania. Kod porównania znajduje się w osobnej procedurze, więc algorytm sortowania można napisać w bardziej ogólny sposób.  
  
## <a name="delegates-overview"></a>Omówienie delegatów  
 Delegaty mają następujące właściwości:  
  
- Delegaty są podobne do wskaźników funkcji języka C++, ale obiekty delegowane są w pełni zorientowane obiektowo, a w przeciwieństwie do języka C++ wskaźników do składowych, delegatów hermetyzacji zarówno w przypadku wystąpienia obiektu, jak i metody.
  
- Delegaty zezwalają na przekazywanie metod jako parametrów.  
  
- Delegatów można używać do definiowania metod wywoływania zwrotnego.  
  
- Delegaty można łączyć w łańcuch; na przykład w jednym zdarzeniu można wywołać wiele metod.  
  
- Metody nie muszą dokładnie pasować do typu delegata. Aby uzyskać więcej informacji, zobacz [przy użyciu wariancje w Delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C# w wersji 2.0 wprowadzono koncepcję [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), które umożliwiają bloków kodu, które zostaną przekazane jako parametry, zamiast oddzielnie definiowanej metody. W języku C# 3.0 wprowadzono wyrażenia lambda, które stanową wygodniejszy sposób pisania bloków kodu w tekście. Zarówno metody anonimowe, jak i wyrażenia lambda (w pewnych kontekstach) są kompilowane na typy delegatów. Te funkcje są obecnie nazywane łącznie funkcjami anonimowymi. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Używanie delegatów](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
- [Kiedy należy używać obiektów delegowanych zamiast interfejsów (C# Programming Guide)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Delegaci z metodami nazwanymi lub anonimowymi](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
- [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
- [Korzystanie z wariancji w delegatach](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
- [Instrukcje: Deklarowanie, tworzenie wystąpień i użycie delegowania](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  

## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [delegatów](~/_csharplang/spec/delegates.md) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegatów, zdarzeń i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3.0 Cookbook, Third Edition: Ponad 250 rozwiązań dla C# ekspertów w programowaniu w wersji 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaci i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczenia C# 3.0: Opanowanie podstaw C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
