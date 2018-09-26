---
title: Metody rozszerzeń (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 7ebd04665d91f599edcb4a5c07680216dfb8925a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080256"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozszerzeń (Przewodnik programowania w języku C#)
Metody rozszerzenia umożliwiają „dodawanie” metod do istniejących typów bez konieczności tworzenia nowego typu pochodnego, ponownej kompilacji lub modyfikowania oryginalnego typu w inny sposób. Metody rozszerzenia stanowią specjalny rodzaj metod statycznych, ale są wywoływane tak, jakby były metodami wystąpień w typie rozszerzonym. Dla kodu klienta napisanego w języku C#, F # i Visual Basic nie istnieje żadna widoczna różnica między wywołaniem metody rozszerzenia i metod, które faktycznie są zdefiniowane w typie.  
  
 Najczęściej stosowanymi metodami rozszerzenia są [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowych operatorów zapytań, które dodają funkcje zapytań do istniejących <xref:System.Collections.IEnumerable?displayProperty=nameWithType> i <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typów. Aby użyć standardowych operatorów zapytań, najpierw Doprowadź je do zakresu za pomocą `using System.Linq` dyrektywy. Następnie dowolny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601> wydaje się mieć metody wystąpień, takie jak <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>i tak dalej. Możesz zobaczyć te dodatkowe metody w instrukcji IntelliSense po wpisaniu "dot" po wystąpieniu typu <xref:System.Collections.Generic.IEnumerable%601> wpisz na przykład <xref:System.Collections.Generic.List%601> lub <xref:System.Array>.  
  
 Poniższy przykład pokazuje sposób wywoływania standardowego operatora zapytania `OrderBy` metody w tablicy liczb całkowitych. Wyrażenie w nawiasach to wyrażenie lambda. Wiele standardowych operatorów zapytań przyjmuje wyrażenia lambda jako parametry, ale nie jest to wymagane dla metod rozszerzenia. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 Metody rozszerzenia są zdefiniowane jako metody statyczne, ale są wywoływane przy użyciu składni metod wystąpienia. Ich pierwszy parametr określa, jakiego typu metoda działa, i ten parametr jest poprzedzony przez [to](../../../csharp/language-reference/keywords/this.md) modyfikator. Metody rozszerzające są w zakresie wyłącznie wtedy, gdy jawnie importujesz przestrzeń nazw do kodu źródłowego za pomocą `using` dyrektywy.  
  
 W poniższym przykładzie pokazano metodę rozszerzenia zdefiniowaną dla <xref:System.String?displayProperty=nameWithType> klasy. Należy zauważyć, że zdefiniowano ją wewnątrz niezagnieżdżonej nieogólnej klasy statycznej:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 `WordCount` — Metoda rozszerzenia może być wprowadzana do zakresu za pomocą `using` dyrektywy:  
  
```csharp  
using ExtensionMethods;  
```  
  
 A za pomocą poniższej składni można ją wywołać z aplikacji:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 W kodzie metoda rozszerzenia jest wywoływana za pomocą składni metody wystąpienia. Jednak język pośredni (IL) generowany przez kompilator dokonuje translacji kodu na wywołanie metody statycznej. W związku z tym zasada hermetyzacji tak naprawdę nie jest naruszana. W rzeczywistości metody rozszerzenia nie mają dostępu do zmiennych prywatnych w typie, który rozszerzają.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Implementowanie i wywołanie metody rozszerzenia niestandardowe](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Ogólnie rzecz biorąc, liczba wywołań metod rozszerzenia zazwyczaj jest o wiele większa niż liczba implementacji własnych metod. Metody rozszerzenia są wywoływane przy użyciu składni metody wystąpienia, więc nie jest potrzebna specjalistyczna wiedza, aby móc używać ich z poziomu kodu klienta. Aby włączyć metody rozszerzające dla określonego typu, wystarczy dodać atrybut `using` dyrektywy dla przestrzeni nazw, w którym są zdefiniowane te metody. Na przykład, aby użyć standardowych operatorów zapytań, dodaj to `using` dyrektywę w kodzie:  
  
```csharp  
using System.Linq;  
```  
  
 (Może być też koniecznie dodanie odwołania do biblioteki System.Core.dll). Zauważysz, że standardowe operatory zapytań pojawiają się w IntelliSense jako dodatkowe metody dostępne dla większości <xref:System.Collections.Generic.IEnumerable%601> typów.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Metody rozszerzające w czasie kompilacji  
 Można stosować metody rozszerzenia, aby rozszerzyć klasę lub interfejs, ale nie w celu pominięcia go. Metoda rozszerzenia mająca taką samą nazwę i podpis jak interfejs lub metoda klasy nigdy nie zostanie wywołana. W czasie kompilacji metody rozszerzenia zawsze mają niższy priorytet niż zdefiniowane w typie metody wystąpienia. Innymi słowy, jeśli typ ma metodę o nazwie `Process(int i)`i masz metodę rozszerzającą o tym samym podpisie, kompilator zawsze utworzy wiązanie z metodą wystąpienia. Gdy kompilator napotyka wywołanie metody, najpierw szuka dopasowania w metodach wystąpienia danego typu. Jeżeli nie znajdzie dopasowania, wyszuka metody rozszerzenia, które są zdefiniowane dla danego typu, i utworzy powiązanie z pierwszą metodą rozszerzenia, którą znajdzie. W poniższym przykładzie pokazano, w jaki sposób kompilator określa metodę rozszerzenia lub metodę wystąpienia, z którą ma utworzyć powiązanie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono reguły, zgodnie z którymi kompilator języka C# określa, czy należy powiązać wywołanie metody z metodą wystąpienia typu, czy z metodą rozszerzenia. Klasa statyczna `Extensions` zawiera metody rozszerzenia zdefiniowane dla dowolnego typu, który implementuje `IMyInterface`. Klasy `A`, `B`, i `C` implementują interfejs.  
  
 `MethodB` — Metoda rozszerzenia nigdy nie jest wywoływana, ponieważ jego nazwa i podpis dokładnie pasują do metod już zaimplementowanych przez klasy.  
  
 Gdy kompilator nie może odnaleźć metody wystąpienia mającej pasujący podpis, tworzy powiązanie z pasującą metodą rozszerzenia, jeśli taka istnieje.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Ogólnie zalecane jest, aby implementować metody rozszerzenia oszczędnie i tylko wtedy, gdy jest to konieczne. Jeśli to możliwe, kod klienta, który musi rozszerzyć istniejący typ, powinien to zrobić przez utworzenie nowego typu, który będzie typem pochodnym istniejącego typu. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 W przypadku korzystania z metody rozszerzenia w celu rozszerzania typu, którego kodu źródłowego nie można zmienić, istnieje ryzyko, że zmiana w implementacji typu spowoduje przerwanie działania metody rozszerzenia.  
  
 W przypadku zastosowania metody rozszerzenia dla danego typu, należy pamiętać o następujące kwestie:  
  
-   Metoda rozszerzenia nigdy nie zostanie wywołana, jeśli ma taki sam podpis, jak metoda zdefiniowana w typie.  
  
-   Metody rozszerzenia są włączane do zakresu na poziomie przestrzeni nazw. Na przykład, jeśli masz wiele klas statycznych, które zawierają metody rozszerzające w pojedynczej przestrzeni nazw o nazwie `Extensions`, ich zostaną wszystkie włączone do zakresu `using Extensions;` dyrektywy.  
  
 Dla zaimplementowanej biblioteki klas nie należy używać metod rozszerzenia, aby uniknąć zwiększenia numeru wersji zestawu. W przypadku dodawania znaczącej funkcjonalności do biblioteki, której kod źródłowy jest własnością użytkownika, należy przestrzegać standardowych wytycznych programu .NET Framework dotyczących wersji zestawów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../docs/framework/app-domains/assembly-versioning.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Równoległe przykłady programowania (zawierają wiele przykładów metod rozszerzenia)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)  
- [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Standardowe operatory zapytań — przegląd](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Reguły konwersji dla wystąpienia parametrów i ich wpływ](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)  
- [Międzyoperacyjność metod rozszerzających między językami](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)  
- [Metody rozszerzające i przenoszeni delegaci](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)  
- [Metoda rozszerzenia powiązań i raportowanie błędów](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
