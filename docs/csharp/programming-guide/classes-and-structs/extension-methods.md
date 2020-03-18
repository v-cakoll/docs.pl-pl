---
title: Metody rozszerzenia — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: ce35ef4d4286310aa6c8b6e40c3a448b0d91ea7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937524"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozszerzeń (Przewodnik programowania w języku C#)
Metody rozszerzenia umożliwiają „dodawanie” metod do istniejących typów bez konieczności tworzenia nowego typu pochodnego, ponownej kompilacji lub modyfikowania oryginalnego typu w inny sposób. Metody rozszerzenia stanowią specjalny rodzaj metod statycznych, ale są wywoływane tak, jakby były metodami wystąpień w typie rozszerzonym. Dla kodu klienta napisanego w języku C#, F# i Visual Basic nie ma widocznej różnicy między wywoływanie metody rozszerzenia i metody, które są faktycznie zdefiniowane w typie.  
  
 Najczęstsze metody rozszerzenia są linq standardowych operatorów zapytań, które <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> dodają funkcje kwerendy do istniejących i typów. Aby użyć standardowych operatorów zapytań, najpierw `using System.Linq` wprowadzić je w zakres za pomocą dyrektywy. Następnie każdy typ, <xref:System.Collections.Generic.IEnumerable%601> który implementuje wydaje <xref:System.Linq.Enumerable.GroupBy%2A>się <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Average%2A>mieć metody wystąpienia, takie jak , , , i tak dalej. Te dodatkowe metody można zobaczyć w uzupełnieniu instrukcji IntelliSense po wpisaniu "kropka" po wystąpieniu <xref:System.Collections.Generic.IEnumerable%601> typu takiego jak <xref:System.Collections.Generic.List%601> lub <xref:System.Array>.  
  
 W poniższym przykładzie pokazano, `OrderBy` jak wywołać metodę operatora kwerendy standardowej na tablicy liczb całkowitych. Wyrażenie w nawiasach to wyrażenie lambda. Wiele standardowych operatorów zapytań przyjmuje wyrażenia lambda jako parametry, ale nie jest to wymagane dla metod rozszerzenia. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Metody rozszerzenia są zdefiniowane jako metody statyczne, ale są wywoływane przy użyciu składni metod wystąpienia. Ich pierwszy parametr określa, który typ metody działa na, a parametr jest poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem. Metody rozszerzenia są tylko w zakresie, gdy jawnie zaimportować `using` obszar nazw do kodu źródłowego z dyrektywą.  
  
 W poniższym przykładzie przedstawiono metodę <xref:System.String?displayProperty=nameWithType> rozszerzenia zdefiniowaną dla klasy. Należy zauważyć, że zdefiniowano ją wewnątrz niezagnieżdżonej nieogólnej klasy statycznej:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 Metoda `WordCount` rozszerzenia może zostać wprowadzona w zakres za pomocą tej `using` dyrektywy:  
  
```csharp  
using ExtensionMethods;  
```  
  
 A za pomocą poniższej składni można ją wywołać z aplikacji:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 W kodzie metoda rozszerzenia jest wywoływana za pomocą składni metody wystąpienia. Jednak język pośredni (IL) generowany przez kompilator dokonuje translacji kodu na wywołanie metody statycznej. W związku z tym zasada hermetyzacji tak naprawdę nie jest naruszana. W rzeczywistości metody rozszerzenia nie mają dostępu do zmiennych prywatnych w typie, który rozszerzają.  
  
 Aby uzyskać więcej informacji, zobacz [Jak zaimplementować i wywołać metodę rozszerzenia niestandardowego](./how-to-implement-and-call-a-custom-extension-method.md).
  
 Ogólnie rzecz biorąc, liczba wywołań metod rozszerzenia zazwyczaj jest o wiele większa niż liczba implementacji własnych metod. Metody rozszerzenia są wywoływane przy użyciu składni metody wystąpienia, więc nie jest potrzebna specjalistyczna wiedza, aby móc używać ich z poziomu kodu klienta. Aby włączyć metody rozszerzenia dla określonego typu, wystarczy dodać dyrektywę `using` dla obszaru nazw, w którym metody są zdefiniowane. Na przykład, aby użyć standardowych operatorów `using` zapytań, dodaj tę dyrektywę do kodu:  
  
```csharp  
using System.Linq;  
```  
  
 (Może być również trzeba dodać odwołanie do System.Core.dll.) Można zauważyć, że standardowe operatory zapytań są teraz wyświetlane w <xref:System.Collections.Generic.IEnumerable%601> IntelliSense jako dodatkowe metody dostępne dla większości typów.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Metody rozszerzające w czasie kompilacji  
 Można stosować metody rozszerzenia, aby rozszerzyć klasę lub interfejs, ale nie w celu pominięcia go. Metoda rozszerzenia mająca taką samą nazwę i podpis jak interfejs lub metoda klasy nigdy nie zostanie wywołana. W czasie kompilacji metody rozszerzenia zawsze mają niższy priorytet niż zdefiniowane w typie metody wystąpienia. Innymi słowy, jeśli typ ma `Process(int i)`metodę o nazwie , i masz metodę rozszerzenia z tym samym podpisem, kompilator zawsze będzie powiązać z metodą wystąpienia. Gdy kompilator napotyka wywołanie metody, najpierw szuka dopasowania w metodach wystąpienia danego typu. Jeżeli nie znajdzie dopasowania, wyszuka metody rozszerzenia, które są zdefiniowane dla danego typu, i utworzy powiązanie z pierwszą metodą rozszerzenia, którą znajdzie. W poniższym przykładzie pokazano, w jaki sposób kompilator określa metodę rozszerzenia lub metodę wystąpienia, z którą ma utworzyć powiązanie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono reguły, zgodnie z którymi kompilator języka C# określa, czy należy powiązać wywołanie metody z metodą wystąpienia typu, czy z metodą rozszerzenia. Klasa `Extensions` statyczna zawiera metody rozszerzenia zdefiniowane dla `IMyInterface`dowolnego typu, który implementuje . Klasy `A` `B`, `C` i wszystkie implementują interfejs.  
  
 Metoda `MethodB` rozszerzenia nigdy nie jest wywoływana, ponieważ jego nazwa i podpis dokładnie odpowiadają metodom już zaimplementowanym przez klasy.  
  
 Gdy kompilator nie może odnaleźć metody wystąpienia mającej pasujący podpis, tworzy powiązanie z pasującą metodą rozszerzenia, jeśli taka istnieje.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Ogólnie zalecane jest, aby implementować metody rozszerzenia oszczędnie i tylko wtedy, gdy jest to konieczne. Jeśli to możliwe, kod klienta, który musi rozszerzyć istniejący typ, powinien to zrobić przez utworzenie nowego typu, który będzie typem pochodnym istniejącego typu. Aby uzyskać więcej informacji, zobacz [Dziedziczenie](./inheritance.md).  
  
 W przypadku korzystania z metody rozszerzenia w celu rozszerzania typu, którego kodu źródłowego nie można zmienić, istnieje ryzyko, że zmiana w implementacji typu spowoduje przerwanie działania metody rozszerzenia.  
  
 Jeśli implementujesz metody rozszerzenia dla danego typu, należy pamiętać o następujących punktach:  
  
- Metoda rozszerzenia nigdy nie zostanie wywołana, jeśli ma taki sam podpis, jak metoda zdefiniowana w typie.  
  
- Metody rozszerzenia są włączane do zakresu na poziomie przestrzeni nazw. Na przykład jeśli masz wiele klas statycznych, które zawierają `Extensions`metody rozszerzenia w jednej przestrzeni `using Extensions;` nazw o nazwie, wszystkie zostaną wprowadzone do zakresu przez dyrektywę.  
  
 Dla zaimplementowanej biblioteki klas nie należy używać metod rozszerzenia, aby uniknąć zwiększenia numeru wersji zestawu. W przypadku dodawania znaczącej funkcjonalności do biblioteki, której kod źródłowy jest własnością użytkownika, należy przestrzegać standardowych wytycznych programu .NET Framework dotyczących wersji zestawów. Aby uzyskać więcej informacji, zobacz [Przechowywanie wersji zestawu](../../../standard/assembly/versioning.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Przykłady programowania równoległego (obejmują one wiele przykładowych metod rozszerzenia)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md)
- [Standardowe operatory zapytań — przegląd](../concepts/linq/standard-query-operators-overview.md)
- [Reguły konwersji dla parametrów instancji i ich wpływu](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Metody rozszerzenia Interoperacyjność między językami](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Metody rozszerzenia i delegatów Curried](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Raportowanie powiązań i błędów metody rozszerzenia](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
