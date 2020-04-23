---
title: Aktualizowanie bazy kodu w celu używania typów odwołań z dopuszczalną wartością null
description: Wybierz najlepszą strategię uaktualniania bazy kodu, aby użyć typów odwołań z dopuszczalną wartością null.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: b4a10863aea5c47b47c2a017afb20786b1e67528
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103528"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizowanie bibliotek w celu używania typów odwołań z regułami zbędnymi wartościami null i przekazywanie reguł nullable wywołującym

Dodanie [typów odwołań nullable](nullable-references.md) oznacza, że `null` można zadeklarować, czy wartość jest dozwolona lub oczekiwana dla każdej zmiennej. Ponadto można zastosować liczbę atrybutów: `AllowNull` `DisallowNull`, `MaybeNull` `NotNull`, `NotNullWhen` `MaybeNullWhen`, `NotNullIfNotNull` , , i całkowicie opisać null stany argumentów i zwracanych wartości. Zapewnia to wspaniałe doświadczenie podczas pisania kodu. Otrzymasz ostrzeżenia, jeśli zmienna nienastępna null może być ustawiona na `null`. Otrzymasz ostrzeżenia, jeśli zmienna nullable nie jest zaznaczona zerem przed wyłuskaniem go. Aktualizowanie bibliotek może zająć trochę czasu, ale wypłaty są tego warte. Im więcej informacji, które podasz `null` kompilatorowi o *tym, kiedy* wartość jest dozwolona lub zabroniona, otrzymają lepsze ostrzeżenia, które otrzymają użytkownicy interfejsu API. Zacznijmy od znanego przykładu. Wyobraź sobie, że biblioteka ma następujący interfejs API do pobierania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

W poprzednim przykładzie `Try*` następuje znane wzorzec w .NET. Istnieją dwa argumenty odwołania dla `key` tego `message` interfejsu API: i parametr. Ten interfejs API ma następujące reguły odnoszące się do nieważności tych argumentów:

- Dzwoniący nie powinni `null` przechodzić `key`jako argument dla .
- Osoby dzwoniące mogą przekazać `null` zmienną, `message`której wartość jest argumentem dla .
- Jeśli `TryGetMessage` metoda `true`zwraca , `message` wartość nie jest null. Jeśli zwracana `false,` wartość jest `message` wartością (a jej stan zerowy) jest null.

Reguła `key` dla może być całkowicie wyrażona `key` przez typ zmiennej: powinien być typem odwołania nienastępnego. Parametr `message` jest bardziej złożony. Pozwala `null` jako argument, ale gwarantuje, że `out` na sukces, że argument nie jest null. W przypadku tych scenariuszy potrzebujesz bogatszego słownictwa, aby opisać oczekiwania.

Aktualizowanie biblioteki dla odwołań nullable wymaga `?` więcej niż posypywanie na niektóre zmienne i nazwy typów. W poprzednim przykładzie pokazano, że należy zbadać interfejsy API i należy wziąć pod uwagę oczekiwania dla każdego argumentu wejściowego. Należy wziąć pod uwagę gwarancje `out` dla `ref` wartości zwracanej i wszelkie lub argumenty po powrocie metody. Następnie komunikować te reguły do kompilatora, a kompilator zapewni ostrzeżenia, gdy wywołania nie są zgodne z tymi regułami.

Ta praca wymaga czasu. Zacznijmy od strategii, aby biblioteka lub aplikacja nullable-aware, przy jednoczesnym równoważeniu innych wymagań i ujednolików. Zobaczysz, jak zrównoważyć bieżące gonie, umożliwiając typy odwołań powodujących wartość null. Poznasz wyzwania dotyczące definicji typów ogólnych. Nauczysz się stosować atrybuty do opisywania warunków wstępnych i postowych w poszczególnych interfejsach API.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Wybieranie strategii dla typów odwołań z dopuszczaniem do wartości null

Pierwszym wyborem jest to, czy typy odwołań nullable powinny być domyślnie włączone lub wyłączone. Masz dwie strategie:

- Włącz typy odwołań nullable dla całego projektu i wyłącz go w kodzie, który nie jest gotowy.
- Włącz tylko typy odwołań z nullable dla kodu, który został o astowany dla typów odwołań zdatnymi do wartości null.

Pierwsza strategia działa najlepiej podczas dodawania innych funkcji do biblioteki podczas aktualizowania go dla typów odwołań, których można anulować. Wszystkie nowe rozwoju jest nullable świadomość. Podczas aktualizowania istniejącego kodu, można włączyć nullable typy odwołań w tych klasach.

Zgodnie z tą pierwszą strategią wykonaj następujące czynności:

1. Włącz typy odwołań nullable dla `<Nullable>enable</Nullable>` całego projektu, dodając element do plików *csproj.*
1. Dodaj `#nullable disable` pragmę do każdego pliku źródłowego w projekcie.
1. Podczas pracy nad każdym plikiem usuń pragmę i zaaminuj wszelkie ostrzeżenia.

Ta pierwsza strategia ma więcej pracy z góry, aby dodać pragmy do każdego pliku. Zaletą jest to, że każdy nowy plik kodu dodany do projektu będzie nullable włączone. Wszelkie nowe prace będą nieważne świadomość; tylko istniejący kod musi zostać zaktualizowany.

Druga strategia działa lepiej, jeśli biblioteka jest ogólnie stabilna, a głównym celem rozwoju jest przyjęcie typów odwołań do nullable. Typy odwołań z których można wyłączyć z wartościami null, podczas dodawać adnotacje do interfejsów API. Po zakończeniu można włączyć typy odwołań nullable dla całego projektu.

Zgodnie z tą drugą strategią wykonujesz następujące czynności:

1. Dodaj `#nullable enable` pragmę do pliku, który chcesz zgłosić do null.
1. Usuń wszelkie ostrzeżenia.
1. Kontynuuj te dwa pierwsze kroki, dopóki nie dowiesz się, że cała biblioteka jest nieuprawniona.
1. Włącz typy nullable dla całego `<Nullable>enable</Nullable>` projektu, dodając element do plików *csproj.*
1. Usuń `#nullable enable` pragmy, ponieważ nie są już potrzebne.

Ta druga strategia ma mniej pracy z góry. Kompromisem jest to, że pierwszym zadaniem podczas tworzenia nowego pliku jest dodanie pragmy i uczynienie go nullable aware. Jeśli deweloperzy w zespole zapomnieć, że nowy kod jest teraz w zaległości pracy, aby wszystkie kodu nullable świadomość.

Która z tych strategii zostanie wybrasza, zależy od tego, jak bardzo aktywny rozwój odbywa się w twoim projekcie. Im bardziej dojrzały i stabilny projekt, tym lepsza druga strategia. Im więcej funkcji jest opracowywanych, tym lepsza jest pierwsza strategia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Czy ostrzeżenia o unieważnianiu powinny powodować zmiany w przerwaniu?

Przed włączeniem typów odwołań do wartości null, zmienne są uważane za *nullable oblivious*. Po włączeniu typów odwołań zable null, wszystkie te zmienne są *niemożna null .* Kompilator wyda ostrzeżenia, jeśli te zmienne nie są inicjowane do wartości innych niż null.

Innym prawdopodobnym źródłem ostrzeżeń są zwracane wartości, gdy wartość nie została zainicjowana.

Pierwszym krokiem w adresowaniu ostrzeżeń `?` kompilatora jest użycie adnotacji na typy parametrów i zwracać, aby wskazać, kiedy argumenty lub zwraca wartości mogą być null. Gdy zmienne odwołania nie może być null, oryginalna deklaracja jest poprawna. Jak to zrobić, Twoim celem nie jest tylko naprawić ostrzeżenia. Ważniejszym celem jest, aby kompilator zrozumieć intencji dla potencjalnych wartości null. Podczas badania ostrzeżeń, można osiągnąć następną ważną decyzję dla biblioteki. Czy chcesz rozważyć zmodyfikowanie podpisów interfejsu API, aby lepiej komunikować intencje projektu? Lepszy podpis interfejsu `TryGetMessage` API dla metody badanej wcześniej może być:

```csharp
string? TryGetMessage(string key);
```

Zwracana wartość wskazuje sukces lub niepowodzenie i przenosi wartość, jeśli wartość została znaleziona. W wielu przypadkach zmiana podpisów interfejsu API może poprawić sposób przekazywania wartości null.

Jednak w przypadku bibliotek publicznych lub bibliotek z dużymi bazami użytkowników może wolisz nie wprowadzać żadnych zmian podpisu interfejsu API. W tych przypadkach i innych typowych wzorcach można zastosować atrybuty, aby jaśniej `null`zdefiniować, kiedy argument lub wartość zwracana może być . Niezależnie od tego, czy rozważasz zmianę powierzchni interfejsu API, prawdopodobnie okaże się, że `null` same adnotacje typu nie są wystarczające do opisywania wartości argumentów lub zwracanych wartości. W tych przypadkach można zastosować atrybuty, aby jaśniej opisać interfejs API.

## <a name="attributes-extend-type-annotations"></a>Atrybuty rozszerzają adnotacje typów

Dodano kilka atrybutów, aby wyrazić dodatkowe informacje o stanie null zmiennych. Cały kod, który napisałeś przed C# 8 wprowadzone nullable typy odwołań był *null oblivious*. Oznacza to, że każda zmienna typu odwołania może mieć wartość null, ale nie są wymagane kontrole wartości null. Gdy kod jest *nullable aware*, te reguły zmienić. Typy odwołań `null` nigdy nie powinny być wartością, `null` a typy odwołań do wartości null muszą być sprawdzane przed odwołaniem.

Reguły interfejsów API są prawdopodobnie bardziej skomplikowane, `TryGetValue` jak widać w scenariuszu interfejsu API. Wiele interfejsów API ma bardziej złożone reguły, gdy zmienne mogą lub nie mogą być `null`. W takich przypadkach użyjesz atrybutów do wyrażenia tych reguł. Atrybuty opisujące semantykę interfejsu API znajdują się w artykule na [atrybuty, które wpływają na analizę nullable](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Definicje ogólne i możliwość niemożności

Prawidłowe komunikowanie stanu null typów ogólnych i metod ogólnych wymaga szczególnej ostrożności. Wynika to z faktu, że typ wartości nullable i typ odwołania nullable są zasadniczo różne. An `int?` jest synonimem `Nullable<int>`, `string?` mając `string` na uwadze, że jest z atrybutem dodanym przez kompilator. Wynik jest, że kompilator nie może `T?` wygenerować poprawny kod bez wiedząc, czy `T` jest `class` lub . `struct`

Nie oznacza to, że nie można użyć typu nullable (typ wartości lub typ odwołania) jako argumentu typu dla zamkniętego typu ogólnego. Oba `List<string?>` `List<int?>` i są prawidłowe `List<T>`wystąpienia .

Oznacza to, że nie można `T?` używać w deklaracji klasy lub metody rodzajowej bez ograniczeń. Na przykład <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nie zostanie zmieniona, aby powrócić `T?`. Można przezwyciężyć to ograniczenie, `struct` dodając `class` albo ograniczenia. Z jednym z tych ograniczeń, kompilator wie, `T` jak `T?`wygenerować kod dla obu i .

Można ograniczyć typy używane dla argumentu typu ogólnego, aby były typami nienastępulnymi wartością null. Można to zrobić, `notnull` dodając ograniczenie do tego argumentu typu. Po zastosowaniu tego ograniczenia argument typu nie może być typem do null.
