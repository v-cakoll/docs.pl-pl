---
title: "Metody rozszerzeń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
caps.latest.revision: "35"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 30058a461dddb872e76bef574273c62910e8b2c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozszerzeń (Przewodnik programowania w języku C#)
Metody rozszerzenia umożliwiają „dodawanie” metod do istniejących typów bez konieczności tworzenia nowego typu pochodnego, ponownej kompilacji lub modyfikowania oryginalnego typu w inny sposób. Metody rozszerzenia stanowią specjalny rodzaj metod statycznych, ale są wywoływane tak, jakby były metodami wystąpień w typie rozszerzonym. Dla klienta kod napisany w języku C#, F # i Visual Basic istnieje widocznej różnicy wywoływanie metody rozszerzenia i metody, które faktycznie są zdefiniowane w typie.  
  
 Najbardziej typowe metody rozszerzenia są [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardowych operatorów zapytań zwiększających funkcjonalność zapytania do istniejącej <xref:System.Collections.IEnumerable?displayProperty=nameWithType> i <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typów. Aby użyć standardowych operatorów zapytań, najpierw dostosować je do zakresu o `using System.Linq` dyrektywy. Następnie dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> ma metody wystąpienia, takich jak <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>i tak dalej. Można wyświetlić te dodatkowe metody w instrukcji IntelliSense po wpisaniu "kropka" po wystąpieniu <xref:System.Collections.Generic.IEnumerable%601> wpisz na przykład <xref:System.Collections.Generic.List%601> lub <xref:System.Array>.  
  
 Poniższy przykład przedstawia sposób wywołania operator zapytania standardowe `OrderBy` metody w tablicy liczb całkowitych. Wyrażenie w nawiasach to wyrażenie lambda. Wiele standardowych operatorów zapytań przyjmuje wyrażenia lambda jako parametry, ale nie jest to wymagane dla metod rozszerzenia. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]  
  
 Metody rozszerzenia są zdefiniowane jako metody statyczne, ale są wywoływane przy użyciu składni metod wystąpienia. Ich pierwszy parametr określa typ metoda działa na i parametru jest poprzedzony [to](../../../csharp/language-reference/keywords/this.md) modyfikator. Metody rozszerzenia są tylko w zakresie po zaimportowaniu jawnie przestrzeni nazw do kodu źródłowego za pomocą `using` dyrektywy.  
  
 W poniższym przykładzie przedstawiono metodę rozszerzenia zdefiniowane dla <xref:System.String?displayProperty=nameWithType> klasy. Należy zauważyć, że zdefiniowano ją wewnątrz niezagnieżdżonej nieogólnej klasy statycznej:  
  
 [!code-csharp[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]  
  
 `WordCount` — Metoda rozszerzenia mogą być wprowadzane do zakresu z tym `using` dyrektywy:  
  
```  
using ExtensionMethods;  
```  
  
 A za pomocą poniższej składni można ją wywołać z aplikacji:  
  
```  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 W kodzie metoda rozszerzenia jest wywoływana za pomocą składni metody wystąpienia. Jednak język pośredni (IL) generowany przez kompilator dokonuje translacji kodu na wywołanie metody statycznej. W związku z tym zasada hermetyzacji tak naprawdę nie jest naruszana. W rzeczywistości metody rozszerzenia nie mają dostępu do zmiennych prywatnych w typie, który rozszerzają.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Implementowanie i wywołanie niestandardowej metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Ogólnie rzecz biorąc, liczba wywołań metod rozszerzenia zazwyczaj jest o wiele większa niż liczba implementacji własnych metod. Metody rozszerzenia są wywoływane przy użyciu składni metody wystąpienia, więc nie jest potrzebna specjalistyczna wiedza, aby móc używać ich z poziomu kodu klienta. Aby włączyć metody rozszerzenia dla określonego typu, po prostu Dodaj `using` dyrektywy dla przestrzeni nazw, w którym zdefiniowano metody. Na przykład, aby używać standardowych operatorów zapytań, dodaj to `using` dyrektywy w kodzie:  
  
```  
using System.Linq;  
```  
  
 (Może być też koniecznie dodanie odwołania do biblioteki System.Core.dll). Można zauważyć, że standardowych operatorów zapytań są teraz wyświetlane w IntelliSense jako dodatkowe metody dostępne dla większości <xref:System.Collections.Generic.IEnumerable%601> typów.  
  
> [!NOTE]
>  Mimo że nie występują w technologii IntelliSense dla standardowych operatorów zapytań <xref:System.String>, będą nadal dostępne.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Metody rozszerzające w czasie kompilacji  
 Można stosować metody rozszerzenia, aby rozszerzyć klasę lub interfejs, ale nie w celu pominięcia go. Metoda rozszerzenia mająca taką samą nazwę i podpis jak interfejs lub metoda klasy nigdy nie zostanie wywołana. W czasie kompilacji metody rozszerzenia zawsze mają niższy priorytet niż zdefiniowane w typie metody wystąpienia. Innymi słowy, jeśli typ ma metodę o nazwie `Process(int i)`i ma metodę rozszerzenia o tej samej sygnaturze, kompilator zawsze wiążą się metody wystąpienia. Gdy kompilator napotyka wywołanie metody, najpierw szuka dopasowania w metodach wystąpienia danego typu. Jeżeli nie znajdzie dopasowania, wyszuka metody rozszerzenia, które są zdefiniowane dla danego typu, i utworzy powiązanie z pierwszą metodą rozszerzenia, którą znajdzie. W poniższym przykładzie pokazano, w jaki sposób kompilator określa metodę rozszerzenia lub metodę wystąpienia, z którą ma utworzyć powiązanie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono reguły, zgodnie z którymi kompilator języka C# określa, czy należy powiązać wywołanie metody z metodą wystąpienia typu, czy z metodą rozszerzenia. Klasa statyczna `Extensions` zawiera metody rozszerzenia zdefiniowane dla dowolnego typu, który implementuje `IMyInterface`. Klasy `A`, `B`, i `C` wszystkie implementować interfejs.  
  
 `MethodB` Nigdy nie jest wywołać metody rozszerzenia, ponieważ jego nazwę i sygnaturę dokładnie odpowiadać metod już zaimplementowany przez klasy.  
  
 Gdy kompilator nie może odnaleźć metody wystąpienia mającej pasujący podpis, tworzy powiązanie z pasującą metodą rozszerzenia, jeśli taka istnieje.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Ogólnie zalecane jest, aby implementować metody rozszerzenia oszczędnie i tylko wtedy, gdy jest to konieczne. Jeśli to możliwe, kod klienta, który musi rozszerzyć istniejący typ, powinien to zrobić przez utworzenie nowego typu, który będzie typem pochodnym istniejącego typu. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 W przypadku korzystania z metody rozszerzenia w celu rozszerzania typu, którego kodu źródłowego nie można zmienić, istnieje ryzyko, że zmiana w implementacji typu spowoduje przerwanie działania metody rozszerzenia.  
  
 W przypadku zastosowania metody rozszerzenia dla danego typu, należy pamiętać o następujące kwestie:  
  
-   Metoda rozszerzenia nigdy nie zostanie wywołana, jeśli ma taki sam podpis, jak metoda zdefiniowana w typie.  
  
-   Metody rozszerzenia są włączane do zakresu na poziomie przestrzeni nazw. Na przykład, jeśli masz wiele klas statycznych, zawierające metody rozszerzenia w jednym obszarze nazw o nazwie `Extensions`, użytkownik zostanie wszystkie przeniesiony do zakresu `using Extensions;` dyrektywy.  
  
 Dla zaimplementowanej biblioteki klas nie należy używać metod rozszerzenia, aby uniknąć zwiększenia numeru wersji zestawu. W przypadku dodawania znaczącej funkcjonalności do biblioteki, której kod źródłowy jest własnością użytkownika, należy przestrzegać standardowych wytycznych programu .NET Framework dotyczących wersji zestawów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](https://msdn.microsoft.com/library/51ket42z).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Równoległe przykłady programowania (dotyczy to wiele metod rozszerzenia przykład)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)  
 [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Operatory standardowe zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 [Konwersja na przykład zasady parametrów i ich wpływ](http://go.microsoft.com/fwlink/?LinkId=112385)  
 [Metody rozszerzenia współdziałanie między językami](http://go.microsoft.com/fwlink/?LinkId=112386)  
 [Metody rozszerzenia i delegatów typu Curried.](http://go.microsoft.com/fwlink/?LinkId=112387)  
 [Metody rozszerzenia powiązania oraz raportowania błędów](http://go.microsoft.com/fwlink/?LinkId=112388)
