---
title: Jednostki miary (F#)
description: 'Dowiedz się, jak zmiennoprzecinkowych i podpisane liczby całkowite w języku F # można skojarzyć jednostki miary, które zwykle są używane do wskazywania długość, wielkości i masowej.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 336a1e04426fb39f5ceb98e06a06cd7eadc36e85
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="units-of-measure"></a>Jednostki miary

Liczby zmiennoprzecinkowe punktu i podpisane liczby całkowite w języku F # można skojarzyć jednostki miary, które zwykle są używane do wskazywania woluminu, długość, masa, i tak dalej. Za pomocą ilości z jednostkami, Włącz kompilator, aby sprawdzić, czy relacje arytmetyczne mają prawidłowe jednostki, co pomaga zapobiec błędy programowania.


## <a name="syntax"></a>Składnia

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Uwagi
Definiuje poprzedniej składni *nazwa jednostki* jednostką miary. Opcjonalny składnik służy do definiowania nowej miary pod względem wcześniej zdefiniowanego jednostki. Na przykład poniższy wiersz definiuje miary `cm` (centymetr).

```fsharp
[<Measure>] type cm
```

Następujący wiersz definiuje miary `ml` (milliliter) jako centymetr sześcienny (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

W poprzednich składni *miary* jest formuła, której dotyczy jednostki. W formułach obejmujących jednostki, integralną uprawnienia są obsługiwane (dodatnie i ujemne), spacji między jednostkami wskazuje iloczyn dwóch jednostek `*` wskazuje także produktu jednostek, a `/` wskazuje iloraz jednostki. Wzajemne jednostki, możesz użyć zasilania ujemnej liczby całkowitej lub `/` wskazujące rozdzielenie licznik i mianownik formuły jednostki. Wiele jednostek w mianownika powinny być ujęte w nawiasy. Jednostki rozdzielone spacjami po `/` będą interpretowane jako część mianownika, ale wszystkie jednostki po `*` będą interpretowane jako część licznik.

Możesz użyć 1 w wyrażeniach jednostki samodzielnie, aby wskazać ilość bez wymiaru, lub wraz z innych jednostek, takich jak licznik. Na przykład jednostki dla stawki powinny być zapisane jako `1/s`, gdzie `s` wskazuje w sekundach. Nawiasy nie są używane w formułach jednostki. Nie określaj konwersja liczbowa stałe w formułach jednostki; można jednak Definiowanie stałych konwersja z jednostki oddzielnie i korzystanie z nich obliczenia zaznaczone jednostki.

Na różne sposoby równoważne można pisać formuły jednostki, które oznaczają to samo. W związku z tym kompilator konwertuje formuły jednostki na spójne formularza, który konwertuje ujemna uprawnień odwrotności, grupy jednostek w jeden licznik i mianownik i sortuje jednostki w liczniku i mianownik w kolejności alfabetycznej.

Na przykład formuły jednostki `kg m s^-2` i `m /s s * kg` konwertowane są na `kg m/s^2`.

Jednostki miary jest używany w przestawne wyrażeniach punktu. Za pomocą liczby zmiennoprzecinkowe oraz skojarzone jednostki miary dodaje kolejny poziom zabezpieczeń i pozwala uniknąć błędów niezgodność jednostki, które mogą wystąpić w formułach, gdy używasz lekko typu liczby zmiennoprzecinkowe. Jeśli piszesz zmiennoprzecinkową punktu wyrażenie, które używa jednostki, muszą być zgodne jednostki w wyrażeniu.

Może dodawać adnotacje do literały z formułą jednostki w nawiasach ostrych, jak pokazano w poniższych przykładach.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Nie należy umieszczać odstęp między liczbą i nawiasu ostrego; jednak można uwzględnić sufiksu literału takich jak `f`, jak w poniższym przykładzie.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Takie adnotacji zmienia typ literału z typu podstawowego (takich jak `float`) do typu wymiarów, takich jak `float<cm>` lub, w tym przypadku `float<miles/hour>`. Jednostka adnotacji `<1>` wskazuje ilość bez wymiaru i jego typ jest odpowiednikiem typu pierwotnego bez parametru jednostki.

Typ jednostki miary jest zmiennoprzecinkowej lub podpisany typ całkowity wraz z jednostki dodatkowych adnotacji, wskazane w nawiasach. W związku z tym podczas zapisu typ konwersji z `g` (g) do `kg` (kg) opisano typy w następujący sposób.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Jednostki miary są używane dla jednostki kompilacji sprawdzania, ale nie są zachowywane w środowisku czasu wykonywania. W związku z tym nie wpływają na wydajność.

Jednostki miary mogą być stosowane do dowolnego typu, nie tylko zmiennoprzecinkową typy punktów; jednak tylko zmiennoprzecinkowych typów, podpisany typów całkowitych i dziesiętnych typy obsługi wymiarów ilości. W związku z tym tylko warto programu jednostki miary w typach pierwotnych i zagregowanych danych, które zawierają te typy pierwotne.

Poniższy przykład przedstawia użycie jednostki miary.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
W poniższym przykładzie przedstawiono sposób konwertowanie bez wymiaru liczba zmiennoprzecinkowa na wymiarów wartość zmiennoprzecinkową. Możesz po prostu należy pomnożyć przez 1.0, stosowania wymiary do 1.0. Można to abstrakcyjnej do funkcji, takich jak `degreesFahrenheit`.

Ponadto podczas wymiarów wartości należy przekazać do funkcji, które oczekują bez wymiaru liczby zmiennoprzecinkowe, musisz anulować limit jednostki lub rzutowane na `float` przy użyciu `float` operatora. W tym przykładzie dzielenia przez `1.0<degC>` dla argumentów do `printf` ponieważ `printf` oczekuje ilości bez wymiaru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

Następująca sesja przykładzie przedstawiono dane wyjściowe z i dane wejściowe, aby ten kod.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Przy użyciu jednostek ogólnych
Można zapisać ogólne funkcje, które działają na dane, które ma skojarzone jednostki miary. W tym celu określanie typu wraz z ogólnym jednostki jako parametr typu, jak pokazano w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>Tworzenie typów agregacji w przypadku ogólnych jednostek
Poniższy kod przedstawia sposób tworzenia typu agregacji, który składa się z poszczególnych wartości zmiennoprzecinkowych mających jednostki, które są ogólne. Dzięki temu jednego typu ma zostać utworzony, który współpracuje z różnych jednostek. Ogólny jednostki zachowują również, typ bezpieczeństwa przez zapewnienie, że typu ogólnego, który ma jeden zestaw jednostek jest innego typu niż tego samego typu ogólnego z innym zestawem jednostek. Podstawy tej metody oznacza, że `Measure` atrybut można stosować do parametru typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>Jednostki w czasie wykonywania
Jednostki miary są używane w celu sprawdzenia typu statycznego. Gdy wartości zmiennoprzecinkowe są kompilowane, jednostki miary są eliminowane, więc jednostki zostaną utracone w czasie wykonywania. W związku z tym każda próba wykonania funkcji zależy od sprawdzania jednostki w czasie wykonywania nie jest możliwe. Na przykład implementacja `ToString` funkcji, aby wydrukować jednostki nie jest możliwe.


## <a name="conversions"></a>Konwersje
Aby przekonwertować typu, który zawiera jednostki (na przykład `float<'u>`) do typu, który nie ma jednostki, możesz użyć funkcji konwersja standardowa. Na przykład można użyć `float` do przekonwertowania na `float` wartość, która nie ma jednostki, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Aby przekonwertować wartość unitless na wartość, która zawiera jednostki, można pomnożyć przez wartość 1 lub 1.0, który jest oznaczony w odpowiednich jednostek. Do pisania warstwy współdziałanie, istnieją jednak także niektóre funkcje explicit, których można użyć do konwersji wartości unitless wartości z jednostkami. Są to [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modułu. Na przykład, aby przekonwertować z unitless `float` do `float<cm>`, użyj [floatwithmeasure —](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a>Jednostki miary w pakiecie zasilania F #
Biblioteka jednostki jest dostępna w PowerPack F #. Biblioteka jednostki zawiera jednostki SI i stałych fizycznych.


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)
