---
title: Delegaci — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: c0f28716926d4c9d74cde58fd00e27d1fdfa7ce1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75705369"
---
# <a name="delegates-c-programming-guide"></a>Delegaty (Przewodnik programowania w języku C#)
[Delegat](../../language-reference/builtin-types/reference-types.md) jest typem, który reprezentuje odwołania do metod z określoną listą parametrów i typem zwracanym. Podczas tworzenia wystąpienia delegata można skojarzyć jego wystąpienie z dowolną metodą mającą zgodny podpis i zwracany typ. Za pośrednictwem wystąpienia delegata można wywołać metodę.  
  
 Delegaty służą do przekazywania metod jako argumentów do innych metod. Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Użytkownik tworzy metodę niestandardową, a klasa, taka jak formant systemu Windows, może wywołać tę metodę, gdy wystąpi określone zdarzenie. W poniższym przykładzie pokazano deklarację delegata:  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Do delegata można przypisać każdą metodę z dowolnej dostępnej klasy lub struktury, która pasuje do typu delegata. Może to być metoda statyczna lub metoda wystąpienia. Umożliwia to programowe zmienianie wywołań metod, a także podłączanie nowego kodu do istniejących klas.  
  
> [!NOTE]
> W kontekście przeciążania metod podpis metody nie zawiera wartości zwracanej. Jednak w kontekście delegatów podpis zawiera wartość zwracaną. Innymi słowy metoda musi mieć taki sam zwracany typ jak delegat.  
  
 Ta możliwość odwoływania się do metody jak do parametru sprawia, że delegaty idealnie nadają się do definiowania metod wywoływania zwrotnego. Na przykład odwołanie do metody, która porównuje dwa obiekty można przekazać jako argument do algorytmu sortowania. Kod porównania znajduje się w osobnej procedurze, więc algorytm sortowania można napisać w bardziej ogólny sposób.  
  
## <a name="delegates-overview"></a>Omówienie delegatów  
 Delegaty mają następujące właściwości:  
  
- Delegatów są podobne do wskaźników funkcji C++, ale delegatów są w pełni zorientowane obiektowo i w przeciwieństwie do wskaźników C++ do funkcji elementów członkowskich, delegatów hermetyzować zarówno wystąpienie obiektu i metody.
  
- Delegaty zezwalają na przekazywanie metod jako parametrów.  
  
- Delegatów można używać do definiowania metod wywoływania zwrotnego.  
  
- Delegaty można łączyć w łańcuch; na przykład w jednym zdarzeniu można wywołać wiele metod.  
  
- Metody nie muszą dokładnie pasować do typu delegata. Aby uzyskać więcej informacji, zobacz [Korzystanie z wariancji w delegatów](../concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C# wersja 2.0 wprowadzono pojęcie [metod anonimowych](../../language-reference/operators/delegate-operator.md), które umożliwiają bloki kodu, które mają być przekazywane jako parametry w miejsce oddzielnie zdefiniowanej metody. W języku C# 3.0 wprowadzono wyrażenia lambda, które stanową wygodniejszy sposób pisania bloków kodu w tekście. Zarówno metody anonimowe, jak i wyrażenia lambda (w pewnych kontekstach) są kompilowane na typy delegatów. Te funkcje są obecnie nazywane łącznie funkcjami anonimowymi. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Używanie delegatów](./using-delegates.md)  
  
- [Kiedy używać delegatów zamiast interfejsów (Przewodnik programowania C#)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Delegaty z metodami nazwanymi lub anonimowymi](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Korzystanie z wariancji w delegatach](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Jak połączyć delegatów (delegatów multiemisji)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Deklarowanie, tworzenie wystąpień i użycie delegowania](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Delegatów](~/_csharplang/spec/delegates.md) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegaci, zdarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów Języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaci i wydarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [nauce C# 3.0: Opanuj podstawy języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>
- [Przewodnik programowania języka C#](../index.md)
- [Zdarzenia](../events/index.md)
