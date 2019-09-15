---
title: Metody rozszerzające C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: e37fc792f79044345d52b2bc463813c0bde22f5b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970907"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozszerzeń (Przewodnik programowania w języku C#)
Metody rozszerzenia umożliwiają „dodawanie” metod do istniejących typów bez konieczności tworzenia nowego typu pochodnego, ponownej kompilacji lub modyfikowania oryginalnego typu w inny sposób. Metody rozszerzenia stanowią specjalny rodzaj metod statycznych, ale są wywoływane tak, jakby były metodami wystąpień w typie rozszerzonym. W przypadku kodu klienta pisanego C#w F# i Visual Basic nie ma żadnej widocznej różnicy między wywołaniem metody rozszerzającej a metodami, które są faktycznie zdefiniowane w typie.  
  
 Najbardziej typowymi metodami rozszerzenia są [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowe operatory zapytań, które dodają funkcję zapytania do <xref:System.Collections.IEnumerable?displayProperty=nameWithType> istniejących <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> i typów. Aby użyć standardowych operatorów zapytań, najpierw Przenieś je do zakresu za pomocą `using System.Linq` dyrektywy. Następnie dowolny typ, który <xref:System.Collections.Generic.IEnumerable%601> implementuje wydaje się mieć metody instancji, <xref:System.Linq.Enumerable.GroupBy%2A>takie <xref:System.Linq.Enumerable.OrderBy%2A>jak <xref:System.Linq.Enumerable.Average%2A>,,, i tak dalej. Te dodatkowe metody można zobaczyć w uzupełnianiu instrukcji IntelliSense po wpisaniu "kropki" po wystąpieniu <xref:System.Collections.Generic.IEnumerable%601> typu, takim jak <xref:System.Collections.Generic.List%601> lub <xref:System.Array>.  
  
 Poniższy przykład pokazuje, jak wywołać metodę standardowego operatora `OrderBy` zapytania w tablicy liczb całkowitych. Wyrażenie w nawiasach to wyrażenie lambda. Wiele standardowych operatorów zapytań przyjmuje wyrażenia lambda jako parametry, ale nie jest to wymagane dla metod rozszerzenia. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Metody rozszerzenia są zdefiniowane jako metody statyczne, ale są wywoływane przy użyciu składni metod wystąpienia. Pierwszy parametr określa, który typ metody operuje, a parametr jest poprzedzony przez [ten](../../language-reference/keywords/this.md) modyfikator. Metody rozszerzające są tylko w zakresie, gdy jawnie zaimportowano przestrzeń nazw do kodu źródłowego `using` za pomocą dyrektywy.  
  
 Poniższy przykład przedstawia metodę rozszerzenia zdefiniowaną dla <xref:System.String?displayProperty=nameWithType> klasy. Należy zauważyć, że zdefiniowano ją wewnątrz niezagnieżdżonej nieogólnej klasy statycznej:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 Metodę rozszerzenia można wprowadzić do zakresu przy użyciu tej `using` dyrektywy: `WordCount`  
  
```csharp  
using ExtensionMethods;  
```  
  
 A za pomocą poniższej składni można ją wywołać z aplikacji:  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 W kodzie metoda rozszerzenia jest wywoływana za pomocą składni metody wystąpienia. Jednak język pośredni (IL) generowany przez kompilator dokonuje translacji kodu na wywołanie metody statycznej. W związku z tym zasada hermetyzacji tak naprawdę nie jest naruszana. W rzeczywistości metody rozszerzenia nie mają dostępu do zmiennych prywatnych w typie, który rozszerzają.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Implementowanie i wywoływanie niestandardowej metody](./how-to-implement-and-call-a-custom-extension-method.md)rozszerzenia.  
  
 Ogólnie rzecz biorąc, liczba wywołań metod rozszerzenia zazwyczaj jest o wiele większa niż liczba implementacji własnych metod. Metody rozszerzenia są wywoływane przy użyciu składni metody wystąpienia, więc nie jest potrzebna specjalistyczna wiedza, aby móc używać ich z poziomu kodu klienta. Aby włączyć metody rozszerzające dla określonego typu, po prostu Dodaj `using` dyrektywę dla przestrzeni nazw, w której są zdefiniowane metody. Na przykład aby użyć standardowych operatorów zapytań, należy dodać tę `using` dyrektywę do kodu:  
  
```csharp  
using System.Linq;  
```  
  
 (Może być też koniecznie dodanie odwołania do biblioteki System.Core.dll). Można zauważyć, że standardowe operatory zapytań są teraz wyświetlane w technologii IntelliSense jako dodatkowe metody dostępne dla <xref:System.Collections.Generic.IEnumerable%601> większości typów.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Metody rozszerzające w czasie kompilacji  
 Można stosować metody rozszerzenia, aby rozszerzyć klasę lub interfejs, ale nie w celu pominięcia go. Metoda rozszerzenia mająca taką samą nazwę i podpis jak interfejs lub metoda klasy nigdy nie zostanie wywołana. W czasie kompilacji metody rozszerzenia zawsze mają niższy priorytet niż zdefiniowane w typie metody wystąpienia. Innymi słowy, jeśli typ ma metodę o nazwie `Process(int i)`i istnieje metoda rozszerzająca o tym samym podpisie, kompilator zawsze utworzy powiązanie z metodą wystąpienia. Gdy kompilator napotyka wywołanie metody, najpierw szuka dopasowania w metodach wystąpienia danego typu. Jeżeli nie znajdzie dopasowania, wyszuka metody rozszerzenia, które są zdefiniowane dla danego typu, i utworzy powiązanie z pierwszą metodą rozszerzenia, którą znajdzie. W poniższym przykładzie pokazano, w jaki sposób kompilator określa metodę rozszerzenia lub metodę wystąpienia, z którą ma utworzyć powiązanie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono reguły, zgodnie z którymi kompilator języka C# określa, czy należy powiązać wywołanie metody z metodą wystąpienia typu, czy z metodą rozszerzenia. Klasa `Extensions` statyczna zawiera metody rozszerzenia zdefiniowane dla dowolnego typu, który `IMyInterface`implementuje. Klasy `A`, `B` i`C` wszystkie implementują interfejs.  
  
 Metoda `MethodB` rozszerzenia nigdy nie jest wywoływana, ponieważ jej nazwa i podpis są dokładnie zgodne z metodami już zaimplementowanymi przez klasy.  
  
 Gdy kompilator nie może odnaleźć metody wystąpienia mającej pasujący podpis, tworzy powiązanie z pasującą metodą rozszerzenia, jeśli taka istnieje.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Ogólnie zalecane jest, aby implementować metody rozszerzenia oszczędnie i tylko wtedy, gdy jest to konieczne. Jeśli to możliwe, kod klienta, który musi rozszerzyć istniejący typ, powinien to zrobić przez utworzenie nowego typu, który będzie typem pochodnym istniejącego typu. Aby uzyskać więcej informacji, zobacz [dziedziczenie](./inheritance.md).  
  
 W przypadku korzystania z metody rozszerzenia w celu rozszerzania typu, którego kodu źródłowego nie można zmienić, istnieje ryzyko, że zmiana w implementacji typu spowoduje przerwanie działania metody rozszerzenia.  
  
 W przypadku implementowania metod rozszerzających dla danego typu należy pamiętać o następujących kwestiach:  
  
- Metoda rozszerzenia nigdy nie zostanie wywołana, jeśli ma taki sam podpis, jak metoda zdefiniowana w typie.  
  
- Metody rozszerzenia są włączane do zakresu na poziomie przestrzeni nazw. Na przykład jeśli masz wiele klas statycznych, które zawierają metody rozszerzające w pojedynczej przestrzeni nazw `Extensions`o nazwie, wszystkie te elementy zostaną wprowadzone do zakresu `using Extensions;` przez dyrektywę.  
  
 Dla zaimplementowanej biblioteki klas nie należy używać metod rozszerzenia, aby uniknąć zwiększenia numeru wersji zestawu. W przypadku dodawania znaczącej funkcjonalności do biblioteki, której kod źródłowy jest własnością użytkownika, należy przestrzegać standardowych wytycznych programu .NET Framework dotyczących wersji zestawów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../standard/assembly/versioning.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Równoległe przykłady programowania (zawierają wiele przykładowych metod rozszerzających)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md)
- [Standardowe operatory zapytań — przegląd](../concepts/linq/standard-query-operators-overview.md)
- [Reguły konwersji dla parametrów wystąpienia i ich wpływu](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)
- [Metody rozszerzające współdziałanie między językami](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)
- [Metody rozszerzające i Delegaty rozwinięte](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)
- [Powiązanie metody rozszerzenia i raportowanie błędów](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
