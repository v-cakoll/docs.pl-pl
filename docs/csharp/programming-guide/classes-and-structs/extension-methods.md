---
title: Metody rozszerzenia — Przewodnik programowania w języku C#
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: fc816123134995b753beda0a6f281133d6ddd691
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506821"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozszerzeń (Przewodnik programowania w języku C#)

Metody rozszerzenia umożliwiają „dodawanie” metod do istniejących typów bez konieczności tworzenia nowego typu pochodnego, ponownej kompilacji lub modyfikowania oryginalnego typu w inny sposób. Metody rozszerzające są metodami statycznymi, ale są wywoływane tak, jakby były metodami wystąpień w typie rozszerzonym. W przypadku kodu klienta pisanego w językach C#, F # i Visual Basic nie ma żadnej widocznej różnicy między wywołaniem metody rozszerzającej i metodami zdefiniowanymi w typie.

Najbardziej typowymi metodami rozszerzenia są operatory standardowych zapytań LINQ, które dodają funkcję zapytania do <xref:System.Collections.IEnumerable?displayProperty=nameWithType> istniejących <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typów i. Aby użyć standardowych operatorów zapytań, najpierw Przenieś je do zakresu za pomocą `using System.Linq` dyrektywy. Następnie dowolny typ, który <xref:System.Collections.Generic.IEnumerable%601> implementuje wydaje się mieć metody instancji, <xref:System.Linq.Enumerable.GroupBy%2A>takie <xref:System.Linq.Enumerable.OrderBy%2A>jak <xref:System.Linq.Enumerable.Average%2A>,,, i tak dalej. Te dodatkowe metody można zobaczyć w uzupełnianiu instrukcji IntelliSense po wpisaniu "kropki" po wystąpieniu <xref:System.Collections.Generic.IEnumerable%601> typu, takim jak <xref:System.Collections.Generic.List%601> lub. <xref:System.Array>

### <a name="orderby-example"></a>Przykład OrderBy

Poniższy przykład pokazuje, jak wywołać metodę standardowego operatora `OrderBy` zapytania w tablicy liczb całkowitych. Wyrażenie w nawiasach to wyrażenie lambda. Wiele standardowych operatorów zapytań przyjmuje wyrażenia lambda jako parametry, ale nie jest to wymagane dla metod rozszerzających. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Metody rozszerzenia są zdefiniowane jako metody statyczne, ale są wywoływane przy użyciu składni metod wystąpienia. Ich pierwszy parametr określa typ, na którym działa Metoda. Parametr jest poprzedzony przez [ten](../../language-reference/keywords/this.md) modyfikator. Metody rozszerzające są tylko w zakresie, gdy jawnie zaimportowano przestrzeń nazw do kodu źródłowego `using` za pomocą dyrektywy.

Poniższy przykład przedstawia metodę rozszerzenia zdefiniowaną dla <xref:System.String?displayProperty=nameWithType> klasy. Jest on zdefiniowany w niezagnieżdżonej nieogólnej klasie statycznej:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

Metodę `WordCount` rozszerzenia można wprowadzić do zakresu przy użyciu tej `using` dyrektywy:

```csharp
using ExtensionMethods;
```

A za pomocą poniższej składni można ją wywołać z aplikacji:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Wywoływanie metody rozszerzenia w kodzie za pomocą składni metody wystąpienia. Język pośredni (IL) generowany przez kompilator tłumaczy kod na wywołanie metody statycznej. Zasada hermetyzacji nie jest naprawdę naruszana. Metody rozszerzające nie mogą uzyskać dostępu do zmiennych prywatnych w typie, który rozszerza.

Aby uzyskać więcej informacji, zobacz [jak zaimplementować i wywołać niestandardową metodę rozszerzenia](./how-to-implement-and-call-a-custom-extension-method.md).

Ogólnie rzecz biorąc, prawdopodobnie będą wywoływane metody rozszerzające znacznie częściej niż implementowanie własnych. Metody rozszerzenia są wywoływane przy użyciu składni metody wystąpienia, więc nie jest potrzebna specjalistyczna wiedza, aby móc używać ich z poziomu kodu klienta. Aby włączyć metody rozszerzające dla określonego typu, po prostu Dodaj `using` dyrektywę dla przestrzeni nazw, w której są zdefiniowane metody. Na przykład aby użyć standardowych operatorów zapytań, należy dodać tę `using` dyrektywę do kodu:

```csharp
using System.Linq;
```

(Może być również konieczne dodanie odwołania do System. Core. dll). Można zauważyć, że standardowe operatory zapytań są teraz wyświetlane w technologii IntelliSense jako dodatkowe metody dostępne dla <xref:System.Collections.Generic.IEnumerable%601> większości typów.

## <a name="binding-extension-methods-at-compile-time"></a>Metody rozszerzające w czasie kompilacji

Można stosować metody rozszerzenia, aby rozszerzyć klasę lub interfejs, ale nie w celu pominięcia go. Metoda rozszerzenia mająca taką samą nazwę i podpis jak interfejs lub metoda klasy nigdy nie zostanie wywołana. W czasie kompilacji metody rozszerzenia zawsze mają niższy priorytet niż zdefiniowane w typie metody wystąpienia. Innymi słowy, jeśli typ ma metodę o nazwie `Process(int i)`i istnieje metoda rozszerzająca o tym samym podpisie, kompilator zawsze utworzy powiązanie z metodą wystąpienia. Gdy kompilator napotyka wywołanie metody, najpierw szuka dopasowania w metodach wystąpienia danego typu. Jeżeli nie znajdzie dopasowania, wyszuka metody rozszerzenia, które są zdefiniowane dla danego typu, i utworzy powiązanie z pierwszą metodą rozszerzenia, którą znajdzie. W poniższym przykładzie pokazano, w jaki sposób kompilator określa metodę rozszerzenia lub metodę wystąpienia, z którą ma utworzyć powiązanie.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono reguły, zgodnie z którymi kompilator języka C# określa, czy należy powiązać wywołanie metody z metodą wystąpienia typu, czy z metodą rozszerzenia. Klasa `Extensions` statyczna zawiera metody rozszerzenia zdefiniowane dla dowolnego typu, który `IMyInterface`implementuje. Klasy `A`, `B`i `C` wszystkie implementują interfejs.

Metoda `MethodB` rozszerzenia nigdy nie jest wywoływana, ponieważ jej nazwa i podpis są dokładnie zgodne z metodami już zaimplementowanymi przez klasy.

Gdy kompilator nie może odnaleźć metody wystąpienia o pasującym podpisie, zostanie on powiązany z pasującą metodą rozszerzenia, jeśli taka istnieje.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Typowe wzorce użycia

### <a name="collection-functionality"></a>Funkcje kolekcji

W przeszłości często utworzono "klasy kolekcji", które implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs dla danego typu i zawiera funkcje, które działały na kolekcjach tego typu. Mimo że nie ma żadnych problemów z tworzeniem tego typu obiektu kolekcji, można osiągnąć te same funkcje przy użyciu rozszerzenia w <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Rozszerzenia mają zalety zezwalające na wywoływanie funkcji z dowolnej kolekcji, takiej jak <xref:System.Array?displayProperty=nameWithType> lub <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , która jest implementowana <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> dla tego typu. Przykładem użycia tablicy Int32 można znaleźć [we wcześniejszej części tego artykułu](#orderby-example).

### <a name="layer-specific-functionality"></a>Funkcje specyficzne dla warstwy

W przypadku używania architektury o architekturze ujęć lub innego projektu aplikacji warstwowych często istnieje zestaw jednostek domeny lub Transfer danych obiektów, które mogą być używane do komunikacji między granicami aplikacji. Te obiekty zwykle nie zawierają funkcji ani tylko minimalnej funkcjonalności, która ma zastosowanie do wszystkich warstw aplikacji. Metody rozszerzające mogą służyć do dodawania funkcji, które są specyficzne dla każdej warstwy aplikacji bez ładowania obiektu w dół z niezbędnymi metodami lub w innych warstwach.

```aspx-csharp
public class DomainEntity
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

static class DomainEntityExtensions
{
    static string FullName(this DomainEntity value)
        => $"{value.FirstName} {value.LastName}";
}
```

### <a name="extending-predefined-types"></a>Rozszerzanie wstępnie zdefiniowanych typów

Zamiast tworzyć nowe obiekty w przypadku konieczności tworzenia funkcji wielokrotnego użytku, można często rozwijać istniejący typ, taki jak .NET Framework lub typ CLR. Jeśli na przykład nie korzystamy z metod rozszerzających, możemy utworzyć klasę `Engine` lub `Query` , aby wykonać kwerendę na SQL Server, która może być wywołana z wielu miejsc w naszym kodzie. Można jednak w zamian zwiększyć <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> klasę przy użyciu metod rozszerzających, aby wykonać to zapytanie z dowolnego miejsca, w którym mamy połączenie z SQL Server. Innymi przykładami może być Dodawanie <xref:System.String?displayProperty=nameWithType> typowych funkcji do klasy, rozszerzonie możliwości przetwarzania danych <xref:System.IO.File?displayProperty=nameWithType> i <xref:System.IO.Stream?displayProperty=nameWithType> obiektów oraz <xref:System.Exception?displayProperty=nameWithType> obiektów dla określonych funkcji obsługi błędów. Te typy przypadków użycia są ograniczone tylko przez wyobraźnię i dobre znaczenie.

Rozszerzanie wstępnie zdefiniowanych typów może być `struct` trudne z typami, ponieważ są one przesyłane przez wartość do metod. Oznacza to, że wszelkie zmiany struktury są wykonywane do kopii struktury. Te zmiany nie są widoczne po zamknięciu metody rozszerzenia. Począwszy od języka C# 7,2, można dodać `ref` modyfikator do pierwszego argumentu metody rozszerzenia. Dodanie `ref` modyfikatora oznacza, że pierwszy argument jest przenoszona przez odwołanie. Dzięki temu można pisać metody rozszerzające, które zmieniają stan rozszerzanej struktury.

## <a name="general-guidelines"></a>Ogólne wskazówki

Mimo że jest to zalecane, aby dodać funkcje, modyfikując kod obiektu lub wprowadzając nowy typ, gdy jest to uzasadnione i możliwe do wykonania, metody rozszerzające stają się kluczową opcją tworzenia funkcji wielokrotnego użytku w całym ekosystemie .NET. Z tego względu, gdy oryginalne źródło nie znajduje się w kontrolce, gdy obiekt pochodny jest nieodpowiedni lub niemożliwe lub gdy funkcjonalność nie powinna być ujawniona poza odpowiednim zakresem, metody rozszerzające są doskonałym wyborem.

Aby uzyskać więcej informacji na temat typów pochodnych, zobacz [dziedziczenie](./inheritance.md).

W przypadku korzystania z metody rozszerzenia w celu rozszerzenia typu, którego kod źródłowy nie jest kontrolowany, należy uruchomić ryzyko, że zmiana w implementacji typu spowoduje, że Metoda rozszerzenia zostanie przerwana.

W przypadku implementowania metod rozszerzających dla danego typu należy pamiętać o następujących kwestiach:

- Metoda rozszerzenia nigdy nie zostanie wywołana, jeśli ma taki sam podpis, jak metoda zdefiniowana w typie.
- Metody rozszerzenia są włączane do zakresu na poziomie przestrzeni nazw. Na przykład jeśli masz wiele klas statycznych, które zawierają metody rozszerzające w pojedynczej przestrzeni nazw `Extensions`o nazwie, wszystkie te elementy zostaną wprowadzone do zakresu `using Extensions;` przez dyrektywę.

Dla zaimplementowanej biblioteki klas nie należy używać metod rozszerzenia, aby uniknąć zwiększenia numeru wersji zestawu. W przypadku dodawania znaczącej funkcjonalności do biblioteki, której kod źródłowy jest własnością użytkownika, należy przestrzegać standardowych wytycznych programu .NET Framework dotyczących wersji zestawów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../standard/assembly/versioning.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Równoległe przykłady programowania (zawierają wiele przykładowych metod rozszerzających)](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
- [Wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md)
- [Standardowe operatory zapytań — Omówienie](../concepts/linq/standard-query-operators-overview.md)
- [Reguły konwersji dla parametrów wystąpienia i ich wpływu](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Metody rozszerzające współdziałanie między językami](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Metody rozszerzające i Delegaty rozwinięte](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Powiązanie metody rozszerzenia i raportowanie błędów](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
