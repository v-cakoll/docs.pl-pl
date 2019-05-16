---
title: Jednostki miary
description: Dowiedz się, jak zmiennoprzecinkowych i zalogowano wartości całkowitych F# może być skojarzony jednostki miary, które są zazwyczaj używane do wskazać, długości, woluminów i urządzeń pamięci masowej.
ms.date: 05/16/2016
ms.openlocfilehash: 217ef67912625c0a4b187a7ee13a739de811cfcb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641634"
---
# <a name="units-of-measure"></a>Jednostki miary

Liczba zmiennoprzecinkowa i zalogowano wartości całkowitych F# może być skojarzony jednostki miary, które są zwykle używane w celu wskazania, długość, woluminu, urządzeń pamięci masowej i tak dalej. Za pomocą ilości z jednostkami, Włącz kompilator, aby sprawdzić, czy relacje arytmetyczne mają prawidłowe jednostki, co pomaga zapobiec błędy programowania.

## <a name="syntax"></a>Składnia

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Uwagi

Definiuje składni powyżej elementem *nazwa jednostki* jako jednostka miary. Opcjonalny składnik jest używane do definiowania nową miarę, posługując się jednostkami uprzednio zdefiniowany. Na przykład następujący wiersz definiuje środek `cm` (centymetr).

```fsharp
[<Measure>] type cm
```

Następujący wiersz określa miarę `ml` (milliliter) jako centymetr sześcienny (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

W poprzedniej składni *miary* to formuła, która obejmuje jednostki. W formułach, obejmujące jednostki, typu całkowitego uprawnień są obsługiwane (pozytywne i negatywne), spacji między jednostkami wskazują iloczyn dwóch jednostek `*` wskazuje także produktu, jednostki i `/` wskazuje iloraz jednostek. Wzajemnego jednostki, możesz użyć ujemną liczbę całkowitą potęgą lub `/` oznacza rozdzielenie licznik i mianownik formuły jednostki. Wiele jednostek w mianownik powinna być otoczona nawiasami. Jednostki rozdzielone spacjami, po `/` są interpretowane jako będące częścią mianownik, ale żadnych jednostek po `*` są interpretowane jako będące częścią licznik.

W wyrażeniach jednostki samodzielnie, aby wskazać bezwymiarowa ilość, lub wraz z innych jednostek, takich jak licznik, można użyć 1. Na przykład jednostki wskaźnik powinny być zapisane jako `1/s`, gdzie `s` wskazuje w sekundach. Nawiasy nie są używane w formułach jednostki. Nie określaj stałe konwersji numerycznej w formułach jednostki; można jednak oddzielnie Definiowanie stałych konwersji przy użyciu jednostek i ich używać w obliczeniach zaznaczone jednostki.

Formuły jednostki, które oznaczają to samo można pisać na różne sposoby równoważne. W związku z tym kompilator konwertuje formuły jednostki spójne formularza, który konwertuje negatywne potęgi odwrotności, grup jednostek do pojedynczego licznik i mianownik i sortuje w kolejności alfabetycznej jednostki w licznik i mianownik.

Na przykład formuły jednostki `kg m s^-2` i `m /s s * kg` konwertowane są na `kg m/s^2`.

Jednostki miary są używane w ruchomy punkt wyrażeń. Za pomocą liczb zmiennoprzecinkowych wraz z skojarzone jednostki miary dodaje kolejny poziom bezpieczeństwa i pomaga uniknąć błędów niezgodności jednostki, które mogą wystąpić w formułach, gdy używasz słabo typizowaną liczb zmiennoprzecinkowych. Jeśli piszesz zmiennoprzecinkowy wyrażenie punktu, który używa jednostki, muszą być zgodne jednostki w wyrażeniu.

Można dodać adnotacje literały przy użyciu formuły jednostki w nawiasy kątowe, jak pokazano w poniższych przykładach.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Nie należy umieszczać odstęp między liczbą a nawias kątowy; Jednakże można dołączyć sufiksu literału takich jak `f`, jak w poniższym przykładzie.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Typ literału tych adnotacji zmieni się z jego typ pierwotny (takich jak `float`) typowi zwymiarowany, takich jak `float<cm>` lub, w tym przypadku `float<miles/hour>`. Jednostka adnotacji `<1>` wskazuje bezwymiarowa ilość, a jego typ jest odpowiednikiem typu pierwotnego bez parametru jednostki.

Typ jednostki miary jest zmiennoprzecinkowej lub podpisany typ całkowity, wraz z adnotacji dodatkowe jednostki, wskazane w nawiasach. Dlatego podczas pisania typ konwersji z `g` (g) do `kg` (kg) opisano typy w następujący sposób.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Jednostki miary są używane dla jednostki kompilacji sprawdzania, ale nie są zachowywane w środowisku uruchomieniowym. W związku z tym nie wpływają na wydajność.

Jednostki miary można zastosować do dowolnego typu, nie tylko zmiennoprzecinkowego punktu; jednak tylko typy zmiennoprzecinkowe, podpisywany typów całkowitych i dziesiętnych typy wymiary techniczną ilości. W związku z tym tylko warto użyć jednostki miary na typy pierwotne i agregacji, które zawierają te typy pierwotne.

Poniższy przykład ilustruje użycie jednostek miary.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

Poniższy kod ilustruje sposób konwertowania z bezwymiarowa liczbę zmiennoprzecinkową do zwymiarowany wartość zmiennoprzecinkową. Możesz po prostu mnożenia 1.0, stosując wymiarów ze 1.0. Możesz to abstrakcyjna do funkcji, takich jak `degreesFahrenheit`.

Ponadto jeśli przekazujesz zwymiarowany wartości do funkcji, które oczekują bezwymiarowa liczb zmiennoprzecinkowych, należy anulować jednostki lub rzutowane na `float` przy użyciu `float` operatora. W tym przykładzie, dzielenie przez `1.0<degC>` dla argumentów `printf` ponieważ `printf` oczekuje bezwymiarowa ilości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Następująca sesja przykład przedstawiono dane wyjściowe z i danych wejściowych do tego kodu.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Przy użyciu ogólnych jednostek

Można napisać ogólnych funkcji, które działają na danych, która ma skojarzone jednostki miary. Można to zrobić, określając typ wraz z ogólnych jednostki jako parametr typu, jak pokazano w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Tworzenie typów agregacji za pomocą ogólnego jednostki

Poniższy kod przedstawia sposób tworzenia typ agregacji, który składa się z pojedynczych wartości zmiennoprzecinkowych, które mają jednostek, które są rodzajowe. Dzięki temu jeden typ ma zostać utworzony, która współdziała z różnych jednostek. Ponadto ogólne jednostki zachować bezpieczeństwo typów, zapewniając, że typ ogólny, który ma jeden zbiór jednostek jest innego typu niż tego samego typu ogólnego z innym zestawem jednostek. Podstawy korzystania z tej techniki jest to, że `Measure` atrybut można stosować do typu parametru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Jednostki w czasie wykonywania

Jednostki miary są używane do sprawdzania typu statycznego. Po skompilowaniu wartości zmiennoprzecinkowe są eliminowane jednostki miary, dlatego jednostki są tracone w czasie wykonywania. W związku z tym wszelkie próby do implementacji funkcji, która zależy od sprawdzania jednostki w czasie wykonywania nie jest możliwe. Na przykład implementacja `ToString` funkcję umożliwiającą wydrukowanie limit jednostek nie jest możliwe.

## <a name="conversions"></a>Konwersje

Można przekonwertować na typ, który ma jednostki (na przykład `float<'u>`) do typu, który nie ma jednostek, można użyć funkcji konwersja standardowa. Na przykład, można użyć `float` do przekonwertowania na `float` wartość, która nie ma jednostek, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Aby przekonwertować wartość unitless wartość, która zawiera jednostki, należy pomnożyć przez wartość 1 lub 1.0, która jest oznaczona przy użyciu odpowiednich jednostek. Do pisania warstwy współdziałanie, istnieją jednak również niektóre funkcje jawne, używanych do konwersji wartości unitless wartości przy użyciu jednostek. Zostały one [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modułu. Na przykład, aby przekonwertować unitless `float` do `float<cm>`, użyj [floatwithmeasure —](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>Jednostki miary w F# podstawowej biblioteki

Biblioteka jednostka jest dostępna w `FSharp.Data.UnitSystems.SI` przestrzeni nazw. Zawiera jednostki SI w ich formie symboli (takich jak `m` dla licznika) w `UnitSymbols` podrzędnej przestrzeni nazw, a ich pełną nazwę (np. `meter` dla licznika) w `UnitNames` podrzędnej przestrzeni nazw.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
