---
title: Metody rozszerzenia — przewodnik po programowaniu języka C#
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0b35ad523fc7f0949cb5243edbdc50cd3e927999
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249223"
---
# <a name="extension-methods-c-programming-guide"></a>Metody rozszerzeń (Przewodnik programowania w języku C#)

Metody rozszerzenia umożliwiają „dodawanie” metod do istniejących typów bez konieczności tworzenia nowego typu pochodnego, ponownej kompilacji lub modyfikowania oryginalnego typu w inny sposób. Metody rozszerzenia są metody statyczne, ale są one wywoływane tak, jakby były metody wystąpienia na typ rozszerzony. Dla kodu klienta napisanego w językach C#, F# i Visual Basic nie ma widocznej różnicy między wywołaniem metody rozszerzenia a metodami zdefiniowanymi w typie.

Najbardziej typowe metody rozszerzenia są LINQ standardowych operatorów zapytań, które dodają funkcje kwerendy do istniejących <xref:System.Collections.IEnumerable?displayProperty=nameWithType> i <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typów. Aby użyć standardowych operatorów zapytań, najpierw `using System.Linq` przenieś je do zakresu za pomocą dyrektywy. Następnie każdy typ, <xref:System.Collections.Generic.IEnumerable%601> który implementuje wydaje <xref:System.Linq.Enumerable.GroupBy%2A> <xref:System.Linq.Enumerable.OrderBy%2A>się <xref:System.Linq.Enumerable.Average%2A>mieć metody wystąpienia, takie jak , , i tak dalej. Te dodatkowe metody można zobaczyć w uzupełnieniu instrukcji IntelliSense po wpisaniu "kropka" po wystąpieniu <xref:System.Collections.Generic.IEnumerable%601> typu, takiego jak <xref:System.Collections.Generic.List%601> lub <xref:System.Array>.

### <a name="orderby-example"></a>Przykład OrderBy

W poniższym przykładzie pokazano, `OrderBy` jak wywołać standardową metodę operatora kwerendy na tablicy liczby całkowitej. Wyrażenie w nawiasach to wyrażenie lambda. Wiele standardowych operatorów zapytań przyjmuje wyrażenia lambda jako parametry, ale nie jest to wymagane dla metod rozszerzenia. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Metody rozszerzenia są zdefiniowane jako metody statyczne, ale są wywoływane przy użyciu składni metod wystąpienia. Ich pierwszy parametr określa, na którym typ działa metoda. Parametr jest poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem. Metody rozszerzenia są tylko w zakresie, gdy jawnie zaimportować obszar nazw do kodu źródłowego z dyrektywą. `using`

Poniższy przykład przedstawia metodę rozszerzenia <xref:System.String?displayProperty=nameWithType> zdefiniowaną dla klasy. Jest zdefiniowany wewnątrz niezagnieżdżonej, niegenerycznej klasy statycznej:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

Metoda `WordCount` rozszerzenia może zostać wprowadzona `using` w zakres tej dyrektywy:

```csharp
using ExtensionMethods;
```

A za pomocą poniższej składni można ją wywołać z aplikacji:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Wywołać metodę rozszerzenia w kodzie ze składnią metody wystąpienia. Język pośredni (IL) generowany przez kompilator tłumaczy kod na wywołanie metody statycznej. Zasada hermetyzacji nie jest tak naprawdę naruszana. Metody rozszerzenia nie mogą uzyskać dostępu do zmiennych prywatnych w typie, który rozszerzają.

Aby uzyskać więcej informacji, zobacz [Jak zaimplementować i wywołać niestandardową metodę rozszerzenia](./how-to-implement-and-call-a-custom-extension-method.md).

Ogólnie rzecz biorąc prawdopodobnie będziesz wywoływać metody rozszerzenia znacznie częściej niż implementowanie własnych. Metody rozszerzenia są wywoływane przy użyciu składni metody wystąpienia, więc nie jest potrzebna specjalistyczna wiedza, aby móc używać ich z poziomu kodu klienta. Aby włączyć metody rozszerzenia dla określonego `using` typu, wystarczy dodać dyrektywę dla obszaru nazw, w którym metody są zdefiniowane. Na przykład, aby użyć standardowych operatorów zapytań, dodaj tę `using` dyrektywę do kodu:

```csharp
using System.Linq;
```

(Może być również trzeba dodać odwołanie do Pliku System.Core.dll. Można zauważyć, że standardowe operatory zapytań są teraz wyświetlane w <xref:System.Collections.Generic.IEnumerable%601> IntelliSense jako dodatkowe metody dostępne dla większości typów.

## <a name="binding-extension-methods-at-compile-time"></a>Metody rozszerzające w czasie kompilacji

Można stosować metody rozszerzenia, aby rozszerzyć klasę lub interfejs, ale nie w celu pominięcia go. Metoda rozszerzenia mająca taką samą nazwę i podpis jak interfejs lub metoda klasy nigdy nie zostanie wywołana. W czasie kompilacji metody rozszerzenia zawsze mają niższy priorytet niż zdefiniowane w typie metody wystąpienia. Innymi słowy, jeśli typ ma `Process(int i)`metodę o nazwie , a masz metodę rozszerzenia z tym samym podpisem, kompilator zawsze będzie powiązany z metodą wystąpienia. Gdy kompilator napotyka wywołanie metody, najpierw szuka dopasowania w metodach wystąpienia danego typu. Jeżeli nie znajdzie dopasowania, wyszuka metody rozszerzenia, które są zdefiniowane dla danego typu, i utworzy powiązanie z pierwszą metodą rozszerzenia, którą znajdzie. W poniższym przykładzie pokazano, w jaki sposób kompilator określa metodę rozszerzenia lub metodę wystąpienia, z którą ma utworzyć powiązanie.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono reguły, zgodnie z którymi kompilator języka C# określa, czy należy powiązać wywołanie metody z metodą wystąpienia typu, czy z metodą rozszerzenia. Klasa statyczna `Extensions` zawiera metody rozszerzenia zdefiniowane `IMyInterface`dla każdego typu implementuujego . Klasy `A` `B`, `C` i wszystkie implementują interfejs.

Metoda `MethodB` rozszerzenia nigdy nie jest wywoływana, ponieważ jej nazwa i podpis dokładnie pasują do metod już zaimplementowanych przez klasy.

Gdy kompilator nie może znaleźć metody wystąpienia z podpisem dopasowania, będzie powiązana z pasujące metody rozszerzenia, jeśli istnieje.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Typowe wzorce użycia

### <a name="collection-functionality"></a>Funkcja zbierania

W przeszłości było wspólne do tworzenia "Klas kolekcji", który implementował <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs dla danego typu i zawarte funkcje, które działały na kolekcje tego typu. Chociaż nie ma nic złego w tworzeniu tego typu obiektu kolekcji, tę samą <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>funkcjonalność można osiągnąć za pomocą rozszerzenia na . Rozszerzenia mają tę zaletę, że funkcja ma być wywoływana z dowolnej kolekcji, <xref:System.Array?displayProperty=nameWithType> takiej jak lub <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> w tym typie. Przykład tego przy użyciu tablicy Int32 można znaleźć [wcześniej w tym artykule](#orderby-example).

### <a name="layer-specific-functionality"></a>Funkcje specyficzne dla warstwy

Podczas korzystania z architektury cebuli lub innych warstwowych projektu aplikacji, jest często zestaw jednostek domeny lub obiektów transferu danych, które mogą służyć do komunikowania się między granicami aplikacji. Obiekty te zazwyczaj nie zawierają żadnych funkcji lub tylko minimalne funkcje, które ma zastosowanie do wszystkich warstw aplikacji. Metody rozszerzenia mogą służyć do dodawania funkcji, które są specyficzne dla każdej warstwy aplikacji bez ładowania obiektu w dół z metod nie jest potrzebne lub pożądane w innych warstwach.

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

Zamiast tworzyć nowe obiekty, gdy należy utworzyć funkcje wielokrotnego użytku, często możemy rozszerzyć istniejący typ, taki jak .NET Framework lub CLR. Na przykład jeśli nie używamy metod rozszerzenia, możemy `Engine` utworzyć `Query` lub klasy do wykonywania kwerendy na serwerze SQL, które mogą być wywoływane z wielu miejsc w naszym kodzie. Jednak zamiast tego możemy <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> rozszerzyć klasę przy użyciu metod rozszerzenia, aby wykonać tę kwerendę z dowolnego miejsca, z których mamy połączenie z programem SQL Server. Inne przykłady mogą być dodać typowe <xref:System.String?displayProperty=nameWithType> funkcje do klasy, rozszerzyć <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> możliwości przetwarzania <xref:System.Exception?displayProperty=nameWithType> danych i obiektów i obiektów dla określonych funkcji obsługi błędów. Tego typu przypadki użycia są ograniczone tylko przez wyobraźnię i zdrowy rozsądek.

Rozszerzanie wstępnie zdefiniowanych typów może `struct` być trudne w przypadku typów, ponieważ są one przekazywane przez wartość do metod. Oznacza to, że wszelkie zmiany w strukturze są wprowadzane do kopii struktury. Te zmiany nie są widoczne po zamknięciu metody rozszerzenia. Począwszy od języka C# 7.2, można dodać `ref` modyfikator do pierwszego argumentu metody rozszerzenia. Dodanie `ref` modyfikatora oznacza, że pierwszy argument jest przekazywany przez odwołanie. Dzięki temu można napisać metody rozszerzenia, które zmieniają stan struktury jest rozszerzony.

## <a name="general-guidelines"></a>Ogólne wskazówki

Chociaż nadal uważa się za preferowane, aby dodać funkcjonalność, modyfikując kod obiektu lub wyprowadzając nowy typ, gdy jest to uzasadnione i możliwe, metody rozszerzenia stały się kluczową opcją do tworzenia funkcji wielokrotnego użytku w całej .NET Ekosystemu. W tych przypadkach, gdy oryginalne źródło nie jest pod kontrolą, gdy obiekt pochodny jest nieodpowiedni lub niemożliwe lub gdy funkcja nie powinna być narażona poza jego odpowiedni zakres, Metody rozszerzenia są doskonałym wyborem.

Aby uzyskać więcej informacji na temat typów pochodnych, zobacz [Dziedziczenie](./inheritance.md).

Podczas korzystania z metody rozszerzenia, aby rozszerzyć typ, którego kod źródłowy nie są pod kontrolą, istnieje ryzyko, że zmiana w implementacji typu spowoduje, że metoda rozszerzenia do przerwania.

Jeśli zaimplementujesz metody rozszerzenia dla danego typu, należy pamiętać o następujących punktach:

- Metoda rozszerzenia nigdy nie zostanie wywołana, jeśli ma taki sam podpis, jak metoda zdefiniowana w typie.
- Metody rozszerzenia są włączane do zakresu na poziomie przestrzeni nazw. Na przykład jeśli masz wiele klas statycznych, które zawierają `Extensions`metody rozszerzenia w jednej przestrzeni nazw `using Extensions;` o nazwie , wszystkie one zostaną wprowadzone do zakresu przez dyrektywę.

Dla zaimplementowanej biblioteki klas nie należy używać metod rozszerzenia, aby uniknąć zwiększenia numeru wersji zestawu. W przypadku dodawania znaczącej funkcjonalności do biblioteki, której kod źródłowy jest własnością użytkownika, należy przestrzegać standardowych wytycznych programu .NET Framework dotyczących wersji zestawów. Aby uzyskać więcej informacji, zobacz [Versioning zestawu](../../../standard/assembly/versioning.md).

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Przykłady programowania równoległego (obejmują one wiele przykładowych metod rozszerzenia)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md)
- [Standardowe operatory zapytań — przegląd](../concepts/linq/standard-query-operators-overview.md)
- [Reguły konwersji dla parametrów instancji i ich wpływu](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Metody rozszerzenia Interoperacyjność między językami](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Metody rozszerzenia i curried delegatów](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Powiązanie metody rozszerzenia i raportowanie błędów](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
