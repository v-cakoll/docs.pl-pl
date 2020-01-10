---
title: Delegaty C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: c0f28716926d4c9d74cde58fd00e27d1fdfa7ce1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705369"
---
# <a name="delegates-c-programming-guide"></a>Delegaty (Przewodnik programowania w języku C#)
[Delegat](../../language-reference/builtin-types/reference-types.md) jest typem, który reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Podczas tworzenia wystąpienia delegata można skojarzyć jego wystąpienie z dowolną metodą mającą zgodny podpis i zwracany typ. Za pośrednictwem wystąpienia delegata można wywołać metodę.  
  
 Delegaty służą do przekazywania metod jako argumentów do innych metod. Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Użytkownik tworzy metodę niestandardową, a klasa, taka jak formant systemu Windows, może wywołać tę metodę, gdy wystąpi określone zdarzenie. W poniższym przykładzie pokazano deklarację delegata:  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Do delegata można przypisać każdą metodę z dowolnej dostępnej klasy lub struktury, która pasuje do typu delegata. Może to być metoda statyczna lub metoda wystąpienia. Umożliwia to programowe zmienianie wywołań metod, a także podłączanie nowego kodu do istniejących klas.  
  
> [!NOTE]
> W kontekście przeciążania metod podpis metody nie zawiera wartości zwracanej. Jednak w kontekście delegatów podpis zawiera wartość zwracaną. Innymi słowy metoda musi mieć taki sam zwracany typ jak delegat.  
  
 Ta możliwość odwoływania się do metody jak do parametru sprawia, że delegaty idealnie nadają się do definiowania metod wywoływania zwrotnego. Na przykład odwołanie do metody, która porównuje dwa obiekty można przekazać jako argument do algorytmu sortowania. Kod porównania znajduje się w osobnej procedurze, więc algorytm sortowania można napisać w bardziej ogólny sposób.  
  
## <a name="delegates-overview"></a>Omówienie delegatów  
 Delegaty mają następujące właściwości:  
  
- Delegaty są podobne C++ do wskaźników funkcji, ale Delegaty są w pełni zorientowane obiektowo i C++ w przeciwieństwie do wskaźników do funkcji składowych, Delegaty hermetyzują zarówno wystąpienie obiektu, jak i metodę.
  
- Delegaty zezwalają na przekazywanie metod jako parametrów.  
  
- Delegatów można używać do definiowania metod wywoływania zwrotnego.  
  
- Delegaty można łączyć w łańcuch; na przykład w jednym zdarzeniu można wywołać wiele metod.  
  
- Metody nie muszą dokładnie pasować do typu delegata. Aby uzyskać więcej informacji, zobacz [Korzystanie z wariancji w delegatach](../concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C#w wersji 2,0 wprowadzono koncepcję [metod anonimowych](../../language-reference/operators/delegate-operator.md), która umożliwia przekazywanie bloków kodu jako parametrów zamiast oddzielnie zdefiniowanej metody. W języku C# 3.0 wprowadzono wyrażenia lambda, które stanową wygodniejszy sposób pisania bloków kodu w tekście. Zarówno metody anonimowe, jak i wyrażenia lambda (w pewnych kontekstach) są kompilowane na typy delegatów. Te funkcje są obecnie nazywane łącznie funkcjami anonimowymi. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../statements-expressions-operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Używanie delegatów](./using-delegates.md)  
  
- [Kiedy używać delegatów zamiast interfejsów (C# Przewodnik programowania)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Delegaty z metodami nazwanymi i anonimowymi](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Korzystanie z wariancji w delegatach](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Jak łączyć delegatów (delegatów multiemisji)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Jak zadeklarować delegata, utworzyć jego wystąpienie i użyć go](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, [Delegaci](~/_csharplang/spec/delegates.md) zobacz Delegaty w [C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3,0 Cookbook, wydanie trzecie: więcej niż 250 rozwiązań dla C# 3,0 programistów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaty i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczeniu C# 3,0: główne podstawy C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](../events/index.md)
