---
title: "Switch — słowo kluczowe (odwołanie w C#)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c345d0c6c935271600a386752e18c19a25cc389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="switch-c-reference"></a>switch (odwołanie w C#)
`switch`jest instrukcja wyboru, która wybiera jeden *przełącznika sekcji* do wykonania z listy kandydatów na podstawie dopasowania wzorca z *pasuje do wyrażenia*. 
  
 [!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

`switch` Instrukcji jest często używana jako alternatywę [if-else](if-else.md) utworzenia, jeśli jedno wyrażenie jest testowana co najmniej trzy warunki. Na przykład następująca `switch` instrukcji określa, czy zmienna typu `Color` ma jeden z trzech wartości: 

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

Jest to równoważne do poniższego przykładu, która używa `if` - `else` utworzenia. 

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a>Wyrażenie dopasowania

Wyrażenie dopasowania zawiera wartość do dopasowania do wzorców w `case` etykiety. Składnia to:

```csharp
   switch (expr)
```

W języku C# 6 wyrażenie dopasowania musi być wyrażenie zwracające wartości z następujących typów:

- [char](char.md).
- [ciąg](string.md).
- [bool](bool.md). 
- wartość typem całkowitym, takich jak [int](int.md) lub [długi](long.md).
- [wyliczenia](enum.md) wartość.

Wyrażenie dopasowania, począwszy od C# 7, może być dowolne wyrażenie inne niż null.
 
## <a name="the-switch-section"></a>W sekcji przełącznika
 
 A `switch` instrukcja zawiera co najmniej jednej sekcji przełącznika. Każda sekcja przełącznika zawiera jeden lub więcej *etykiety case* następuje jeden lub więcej instrukcji. W poniższym przykładzie przedstawiono prosty `switch` instrukcji, która zawiera trzy sekcje przełącznika. Każda sekcja przełącznika ma jednej etykiety case, takich jak `case 1:`, a dwie instrukcje.
 
  A `switch` instrukcja może zawierać dowolną liczbę sekcjach przełącznik, a każda sekcja może mieć co najmniej jeden etykiety case, jak pokazano w poniższym przykładzie. Jednak dwie etykiety case nie może zawierać jednego wyrażenia.  

 [!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 Wykonuje sekcji tylko jednego przełącznika w instrukcji switch. C# nie zezwala na kontynuację z jednej sekcji przełącznika do następnego wykonywania. W związku z tym następujący kod generuje błąd kompilatora CS0163: "Sterowanie nie może przechodzić od jednej etykiety case (<case label>) do innej."  

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
To wymaganie można spełnić zwykle przez jawnie Kończenie sekcji przełącznika za pomocą [podziału](break.md), [goto](goto.md), lub [zwracać](return.md) instrukcji. Poniższy kod jest jednak również nieprawidłowe, ponieważ gwarantuje, że formant programu nie może przechodzić do `default` przełącznika sekcji.
  
 [!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 Wykonanie na liście instrukcji w sekcji przełącznika wielkości etykietą, która odpowiada wyrażeniu dopasowania rozpoczyna się od pierwszej instrukcji i obejmującego na liście instrukcji zwykle do instrukcji szybkiego dostępu, takich jak `break`, `goto case`, `goto label`, `return`, lub `throw`, który limit zostanie osiągnięty. W tym momencie sterowania są przesyłane poza `switch` instrukcji lub innej etykiety case. A `goto` instrukcji, jeśli jest on używany, należy przenieść formant do stałej etykiety. To ograniczenie jest konieczne, ponieważ próby przekazywania kontroli z etykietą niestałe może mieć niepożądane skutki uboczne, takie transferowanie formantu do niezamierzone lokalizacji w kodzie lub tworzenia pętli nieskończonej.

## <a name="case-labels"></a>Etykiety Case

 Każda etykieta case Określa wzorzec do porównania wyrażenie dopasowania ( `caseSwitch` zmiennej w poprzednich przykładach). Jeśli są zgodne, sterowanie jest przekazywane do sekcji przełącznika, który zawiera **pierwszy** pasującego etykiety case. Jeśli nie etykiety case wzorzec jest zgodny z wyrażeniem dopasowania, formantu zostanie przeniesiony do sekcji o `default` etykiety case, jeśli istnieje. W przypadku nie `default` przypadku żadnych instrukcji w żadnej sekcji przełącznika są wykonywane i sterowania są przesyłane poza `switch` instrukcji.

 Aby uzyskać informacje dotyczące `switch` instrukcji i dopasowywanie do wzorców, zobacz [dopasowywanie do wzorca za `switch` instrukcji](#pattern) sekcji.

 C# 6 obsługuje tylko stałe wzorzec i nie zezwala na powtarzanie stałe wartości, dlatego etykiety case zdefiniować wartości wykluczają się wzajemnie, a tylko jeden wzorzec może dopasować wyrażenie dopasowania. W rezultacie, w kolejności `case` instrukcje wyświetlane jest bez znaczenia.

 W języku C# 7 jednak ponieważ inne wzorce są obsługiwane, etykiety case nie należy definiować wartości wykluczają się wzajemnie i wielu wzorców może dopasować wyrażenie dopasowania. Ponieważ są wykonywane tylko instrukcji w sekcji przełącznika, który zawiera pierwszy pasujący wzorzec, w kolejności `case` instrukcje pojawiają się teraz jest ważne. Jeśli C# wykryje sekcji przełącznika, których instrukcji case lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120, "przypadek switch już został obsłużony w przypadku poprzednich." 

 Poniższy przykład przedstawia `switch` instrukcji, która korzysta z różnych wzorców nie wykluczają się wzajemnie. Jeśli przeniesiesz `case 0:` przełącznika sekcji, dzięki czemu nie jest już w pierwszej sekcji `switch` instrukcji, C# generuje błąd kompilatora, ponieważ całkowitą, którego wartość wynosi zero jest podzbiorem wszystkich liczb całkowitych, czyli wzorcowi określonemu przez `case int val` instrukcji.

 [!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

Można rozwiązać ten problem i wyeliminować ostrzeżenia kompilatora w jeden z dwóch sposobów:

- Zmieniając kolejność sekcji przełącznika. 
 
- Przy użyciu < /a name = "kiedy" > po klauzuli</a> w `case` etykiety.
 
## <a name="the-default-case"></a>`default` Case

`default` Case określa sekcji przełącznika do wykonania, jeśli wyrażenie dopasowania nie jest zgodna z wszystkimi innymi `case` etykiety. Jeśli `default` case nie jest obecny i wyrażenie dopasowania nie odpowiada żadnej innej `case` etykiety, przepływem programu znajduje się za pośrednictwem `switch` instrukcji.

`default` Przypadku mogą być wyświetlane w dowolnej kolejności w `switch` instrukcji. Niezależnie od ich kolejność w kodzie źródłowym jest zawsze Szacowana ostatnio, po wszystkich `case` zostały ocenione etykiety.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" />Dopasowywanie do wzorca za `switch` — instrukcja
  
Każdy `case` instrukcji definiuje wzorzec powodujący, jeśli jest on zgodny wyrażenie dopasowania zawierającego sekcji przełącznika do wykonania. Wszystkie wersje języka C# obsługuje stałe wzorzec. Pozostałe wzorce są obsługiwane począwszy od C# 7. 
  
### <a name="constant-pattern"></a>Stałe wzorzec 

Stałe wzorzec sprawdza, czy wyrażenie dopasowania jest równe określonej stałej. Składnia to:

```csharp
   case constant:
```

gdzie *stałej* jest wartość do testowania. *Stała* może być dowolny z następujących wyrażenia stałe: 

- A [bool](bool.md) literału, albo `true` lub `false`.
- Wszystkie typy całkowite stałej, takich jak [int](int.md), [długi](long.md), lub [bajtów](byte.md). 
- Nazwy deklarowanych `const` zmiennej.
- Stała wyliczenia.
- A [char](char.md) literału.
- A [ciąg](string.md) literału.

Stałe wyrażenie jest obliczane w następujący sposób:

- Jeśli *wyrażenie* i *stałej* są typy całkowite operator równości C# Określa, czy wyrażenie zwraca `true` (to znaczy czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie do statycznego [Object.Equals (wyrażenie stałej)](xref:System.Object.Equals(System.Object,System.Object)) metody.  

W poniższym przykładzie użyto stałe wzorzec czy określonej daty jest weekendy, pierwszego dnia tygodnia pracy, ostatni dzień tygodnia pracy lub w środku tygodnia pracy. Oblicza <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwości bieżącego dnia dla członków <xref:System.DayOfWeek> wyliczenia. 

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

W poniższym przykładzie użyto stałe wzorzec do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje maszyny do automatycznego kawy.
  
 [!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a>Wzorzec typu

Wzorzec typu umożliwia oceny zwięzła, typ i konwersji. W przypadku użycia z `switch` instrukcji, aby wykonać dopasowywania do wzorca on sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli można ją, rzutuje zmiennej tego typu. Składnia to:

```csharp
   case type varname 
```
gdzie *typu* jest nazwa typu, do którego wynik *wyrażenie* należy skonwertować i *nazwa_zmiennej* obiektu, do którego wynik *wyrażenie*przekonwertowaniu Jeśli dopasowania zakończy się powodzeniem. 

`case` Wyrażenie jest `true` Jeśli jest spełniony jeden z następujących czynności:

- *wyrażenie* jest wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu pochodzącego od *typu*. Innymi słowy, wynik *wyrażenie* może być upcast na wystąpienie *typu*.

- *wyrażenie* zawiera typ kompilacji jest klasą podstawową *typu*, i *wyrażenie* ma typ obsługi, który jest *typu* lub pochodzi z *typu* . *Typu kompilacji* zmiennej jest typu zmienną, zgodnie z definicją w jego deklaracji typu. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, który jest przypisany do tej zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

Jeśli wyrażenie case ma wartość true, *nazwa_zmiennej* ostatecznie jest przypisany i ma zasięg lokalny w ramach tej sekcji przełącznika.

Należy pamiętać, że `null` jest niezgodny z typem. Aby dopasować `null`, użyj następującego `case` etykiety:

```csharp
case null:
```
 
W poniższym przykładzie użyto ze wzorcem typu, aby podać informacje o różnych rodzajów typy kolekcji.

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Bez wzorca dopasowania, ten kod może być zapisana w następujący sposób. Użycie typu dopasowanie wzorca tworzy kodu mniejszych, który może zostać odczytany, eliminując konieczność, aby sprawdzić, czy wynik konwersji jest `null` lub wykonać rzutowania powtórzony.  

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case` Instrukcji i `when` — klauzula

C# 7, począwszy od ponieważ instrukcji case nie muszą być wykluczają się wzajemnie, można użyć dodać `when` klauzuli, aby określić dodatkowe warunku muszą być spełnione dla instrukcji case wyliczona jako true. `when` Klauzula może być dowolne wyrażenie zwracające wartość logiczną. Jedną z najczęściej zastosowania `when` jest używana do sekcji przełącznika uniemożliwić wykonywanie, gdy wartość wyrażenia dopasowanie jest `null`. 

 W poniższym przykładzie zdefiniowano podstawowej `Shape` klasy, `Rectangle` klasą pochodzącą z `Shape`, a `Square` klasą pochodzącą z `Rectangle`. Używa `when` klauzuli, aby upewnić się, że `ShowShapeInfo` traktuje `Rectangle` obiekt, który został przypisany równy długości i szerokości jako `Square` nawet jeśli nie zostało utworzone jako `Square` obiektu. Metoda nie jest podejmowana próba wyświetlenia informacji o obiekt, który jest `null` lub kształt, w których obszar wynosi zero. 

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
Należy pamiętać, że `when` klauzuli w przykładzie podejmowanych w celu przetestowania czy `Shape` obiekt jest `null` nie wykonuj. Wzorzec poprawnego typu do testowania `null` jest `case null:`.

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  

 [Odwołanie w C#](../index.md)  
 [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
 [Słowa kluczowe języka C#](index.md)  
 [if-else](if-else.md)  
 [Dopasowanie wzorca](../../pattern-matching.md)  
 

 
