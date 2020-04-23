---
title: Typy odwołań z dopuszczalną wartością null — odwołanie do języka C#
description: Dowiedz się więcej o typach odwołań do wartości null w języku C# i o tym, jak z nich korzystać
ms.date: 04/06/2020
ms.openlocfilehash: cb61b162b06faa51faabbcdd91e55618cdeaca73
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102700"
---
# <a name="nullable-reference-types-c-reference"></a>Typy odwołań z dopuszczalną wartości null (odwołanie do języka C#)

> [!NOTE]
> W tym artykule opisano typy odwołań z dopuszczalną wartością null. Można również zadeklarować [typy wartości nullable](nullable-value-types.md).

Nullowe typy odwołań są dostępne począwszy od języka C# 8.0, w kodzie, który zdecydował się na *kontekst świadomości nullable*. Typy odwołań null, ostrzeżenia analizy statycznej null i [operator wyrozumiały o wartości null](../operators/null-forgiving.md) są opcjonalnymi funkcjami języka. Wszystkie są domyślnie wyłączone. *Kontekst z dopuszczalny do wartości null* jest kontrolowany na poziomie projektu przy użyciu ustawień kompilacji lub w kodzie przy użyciu pragmas.

 W kontekście świadomości możliwej do unieważnienia:

- Zmienna typu `T` odwołania musi być zainicjowana z wartością null i nigdy nie `null`może być przypisana do wartości, która może być .
- `T?` Zmienna typu odwołania może być `null` inicjowana lub przypisana, `null`ale `null` musi być sprawdzona przed odwołując się.
- Zmienna `m` typu `T?` jest uważana za niekwaśną po zastosowaniu `m!`operatora wyrozumiałości zerowej, jak w .

Rozróżnienia między typem `T` odwołania nienastępnego do `T?` wartości null i typu odwołania nullable są wymuszane przez interpretację kompilatora poprzednich reguł. Zmienna typu `T` i zmienna `T?` typu są reprezentowane przez ten sam typ .NET. Poniższy przykład deklaruje ciąg nienastępny do wartości null i ciąg dopuszczalny do wartości null, a następnie używa operatora zuprzejący się zerem, aby przypisać wartość do ciągu nienastępnego do wartości null:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

Zmienne `notNull` i `nullable` są reprezentowane <xref:System.String> przez typ. Ponieważ typy nienastępne i nullowe są przechowywane jako ten sam typ, istnieje kilka lokalizacji, w których użycie typu odwołania z możliwością null jest niedozwolone. Ogólnie rzecz biorąc typu odwołania nullable nie może służyć jako klasy podstawowej lub zaimplementowanego interfejsu. Typ odwołania z wartością null nie może być używany w żadnym wyrażeniu testowania obiektów lub typów. Typ odwołania z wartością null nie może być typem wyrażenia dostępu elementu członkowskiego. Poniższe przykłady przedstawiają następujące konstrukcje:

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>Nullable odwołania i analizy statycznej

Przykłady w poprzedniej sekcji ilustrują charakter nullable typów odwołań. Typy odwołań nullable nie są nowe typy klas, ale raczej adnotacje na istniejących typów odwołań. Kompilator używa tych adnotacji, aby ułatwić znajdowanie potencjalnych błędów odwołania null w kodzie. Nie ma różnicy w czasie wykonywania między typem odwołania nienastępnym wartością null a typem odwołania, którego można anulować. Kompilator nie dodaje żadnych sprawdzania środowiska uruchomieniowego dla typów odwołań niepodjętych wartości null. Korzyści są w analizie w czasie kompilacji. Kompilator generuje ostrzeżenia, które ułatwiają znajdowanie i naprawianie potencjalnych błędów null w kodzie. Deklarujesz swój zamiar, a kompilator ostrzega, gdy kod narusza tę intencję.

W kontekście włączonym nullable kompilator wykonuje analizę statyczną na zmiennych dowolnego typu odwołania, zarówno nullable i non-nullable. Kompilator śledzi stan null każdej zmiennej referencyjnej jako *nie null* lub *może null*. Domyślny stan odwołania, którego nie można unieważnić, nie jest *zerowy.* Domyślny stan odwołania do nullable jest *może null*.

Typy odwołań nienastępualnych powinny być zawsze bezpieczne do wyłudania, ponieważ ich stan zerowy nie jest *zerowy.* Aby wymusić tę regułę, kompilator wydaje ostrzeżenia, jeśli typ odwołania nie można anulować nie jest inicjowany do wartości innej niż null. Zmienne lokalne muszą być przypisane w miejscu, w którym są zadeklarowane. Każdy konstruktor musi przypisać każde pole, w jego treści, o nazwie konstruktora lub przy użyciu inicjatora pola. Kompilator wydaje ostrzeżenia, jeśli odwołanie niepodjętalne jest przypisane do odwołania, którego stan jest *może null*. Jednak ponieważ odwołanie nie można null nie jest *null,* nie ostrzeżenia są wydawane, gdy te zmienne są odwołują się.

Typy odwołań do wartości null `null`mogą być inicjowane lub przypisane do . W związku z tym analiza statyczna musi ustalić, że zmienna nie jest *null* przed jej wyłuskiwane. Jeśli odwołanie nullable jest określana *jako może być null*, nie można przypisać do zmiennej odwołania niepodjęwalne. W poniższej klasie przedstawiono przykłady tych ostrzeżeń:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

Poniższy fragment kodu pokazuje, gdzie kompilator emituje ostrzeżenia podczas korzystania z tej klasy:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

W poprzednich przykładach pokazano analizy statycznej kompilatora w celu określenia stanu null zmiennych referencyjnych. Kompilator stosuje reguły języka dla kontroli null i przypisań do informowania o swojej analizie.  Kompilator nie może tworzyć założeń dotyczących semantyki metod lub właściwości. Jeśli wywołasz metody, które wykonują kontrole null, kompilator nie może wiedzieć, te metody wpływają na stan null zmiennej. Istnieje wiele atrybutów, które można dodać do interfejsów API, aby poinformować kompilator o semantyki argumentów i zwracać wartości. Te atrybuty zostały zastosowane do wielu typowych interfejsów API w bibliotekach .NET Core. Na przykład <xref:System.String.IsNullOrEmpty%2A> został zaktualizowany, a kompilator poprawnie interpretuje tę metodę jako sprawdzenie wartości null. Aby uzyskać więcej informacji na temat atrybutów, które mają zastosowanie do analizy statycznej stanu null, zobacz artykuł o [atrybutach nullable](../attributes/nullable-analysis.md).

## <a name="setting-the-nullable-context"></a>Ustawianie kontekstu możliwego do przełowienia

Istnieją dwa sposoby kontrolowania kontekstu możliwego do anulowania. Na poziomie projektu można dodać `<Nullable>enable</Nullable>` ustawienie projektu. W jednym pliku źródłowym języka C# można dodać `#nullable enable` pragma, aby włączyć kontekst nullable. Zobacz artykuł dotyczący [ustawiania strategii możliwej do anulowania](../../nullable-migration-strategies.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące propozycje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Typy referencyjne dopuszczające wartość null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Specyfikacja typów odwołań z nieważność](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości dopuszczające wartość null](nullable-value-types.md)
