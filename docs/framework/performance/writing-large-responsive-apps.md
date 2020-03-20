---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180579"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework

Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych aplikacji programu .NET Framework lub aplikacji przetwarzanych przez dużą ilość danych, takich jak pliki lub bazy danych. Te wskazówki pochodzą z przepisywania kompilatorów języka C# i Visual Basic w kodzie zarządzanym, a ten artykuł zawiera kilka rzeczywistych przykładów z kompilatora języka C#.
  
.NET Framework jest wysoce wydajne do tworzenia aplikacji. Potężne i bezpieczne języki i bogata kolekcja bibliotek sprawiają, że tworzenie aplikacji jest bardzo owocne. Jednak z dużą wydajnością przychodzi odpowiedzialność. Należy użyć wszystkich uprawnień .NET Framework, ale należy przygotować się do dostrojenia wydajności kodu w razie potrzeby.
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Dlaczego nowa wydajność kompilatora ma zastosowanie do aplikacji  
 Zespół platformy kompilatora platformy .NET ("Roslyn") przepisał kompilatory języka C# i Visual Basic w kodzie zarządzanym, aby zapewnić nowe interfejsy API do modelowania i analizowania kodu, narzędzi do tworzenia i włączania znacznie bogatszych, świadomych kodu środowisk w programie Visual Studio. Przepisywanie kompilatorów i tworzenie środowiska programu Visual Studio na nowych kompilatorach ujawniło przydatne szczegółowe informacje o wydajności, które mają zastosowanie do dowolnej dużej aplikacji .NET Framework lub dowolnej aplikacji, która przetwarza dużo danych. Nie musisz wiedzieć o kompilatorów, aby skorzystać z szczegółowych informacji i przykładów z kompilatora języka C#.
  
 Visual Studio używa interfejsów API kompilatora do tworzenia wszystkich funkcji IntelliSense, które użytkownicy kochają, takich jak kolorowanie identyfikatorów i słów kluczowych, listy uzupełnień składni, squiggles dla błędów, porady parametrów, problemy z kodem i akcje kodu. Visual Studio zapewnia tę pomoc, podczas gdy deweloperzy wpisują i zmieniają swój kod, a program Visual Studio musi pozostać responsywny, podczas gdy kompilator stale modeluje edycję kodu przez deweloperów.
  
 Gdy użytkownicy końcowi wchodzą w interakcję z aplikacją, oczekują, że będzie responsywna. Pisanie lub obsługa poleceń nigdy nie powinny być blokowane. Pomoc powinna szybko wyskoczyć lub zrezygnować, jeśli użytkownik kontynuuje wpisywanie tekstu. Aplikacja powinna unikać blokowania wątku interfejsu użytkownika z długimi obliczeniami, które sprawiają, że aplikacja czuje się powolna.
  
 Aby uzyskać więcej informacji na temat kompilatorów Roslyn, zobacz [zestaw SDK platformy kompilatora .NET](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Tylko fakty  
 Należy wziąć pod uwagę te fakty podczas dostrajania wydajności i tworzenia elastycznych aplikacji .NET Framework.
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Nie przedwcześnie optymalizuj  
 Pisanie kodu, który jest bardziej złożony niż musi być poniesie koszty konserwacji, debugowania i polerowania. Doświadczeni programiści mają intuicyjne zrozumienie, jak rozwiązywać problemy z kodowaniem i pisać bardziej wydajny kod. Jednak czasami przedwcześnie optymalizują swój kod. Na przykład używają tabeli mieszania, gdy wystarczy prosta tablica, lub używają skomplikowanego buforowania, które może przeciekać pamięci zamiast po prostu ponownie obliczać wartości. Nawet jeśli jesteś programistą środowiska, należy przetestować pod kątem wydajności i analizować kod, gdy znajdziesz problemy.
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Jeśli nie mierzysz, zgadujesz  
 Profile i pomiary nie kłamią. Profile pokazują, czy procesor jest w pełni załadowany, czy też jesteś zablokowany na we/wy dysku. Profile informują, jakiego rodzaju i ile pamięci przydzielasz i czy procesor cpu spędza dużo czasu w [wyrzucaniu elementów bezużytecznych](../../standard/garbage-collection/index.md) (GC).
  
 Należy ustawić cele wydajności dla kluczowych środowisk klienta lub scenariuszy w aplikacji i napisać testy do pomiaru wydajności. Zbadaj nieudane testy, stosując metodę naukową: użyj profili, aby cię poprowadzić, hipotezę, co może być problemem, i przetestuj swoją hipotezę za pomocą eksperymentu lub zmiany kodu. Ustal podstawowe pomiary wydajności w czasie za pomocą regularnych testów, dzięki czemu można wyizolować zmiany, które powodują regresji w wydajności. Zbliżając się do pracy wydajności w sposób rygorystyczny, można uniknąć marnowania czasu z aktualizacji kodu, które nie są potrzebne.
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Dobre narzędzia robią różnicę  
 Dobre narzędzia pozwalają szybko drążyć największe problemy z wydajnością (procesora, pamięci lub dysku) i pomóc zlokalizować kod, który powoduje te wąskie gardła. Firma Microsoft dostarcza wiele narzędzi wydajności, takich jak [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) i [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).
  
 PerfView to bezpłatne i niezwykle potężne narzędzie, które pomaga skupić się na głębokich problemach, takich jak we/wy dysku, zdarzenia GC i pamięć. Śledzenie zdarzeń związanych z wydajnością [dla systemu Windows](../wcf/samples/etw-tracing.md) (ETW) można łatwo przeglądać na aplikację, na proces, na stos i informacje na wątek. PerfView pokazuje, ile i jakiego rodzaju pamięci przydziela aplikacja i które funkcje lub stosy wywołań przyczyniają się ile do alokacji pamięci. Aby uzyskać szczegółowe informacje, zobacz zaawansowane tematy pomocy, wersje demonstracyjne i klipy wideo dołączone do narzędzia (takie jak [samouczki PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) w kanale 9).
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Chodzi o przydziały  
 Można pomyśleć, że tworzenie elastycznej aplikacji .NET Framework jest o algorytmy, takie jak przy użyciu szybkiego sortowania zamiast sortowania bąbelków, ale to nie jest przypadek. Największym czynnikiem w tworzeniu aplikacji responsywnej jest przydzielanie pamięci, zwłaszcza gdy aplikacja jest bardzo duża lub przetwarza duże ilości danych.
  
 Prawie cała praca nad tworzeniem elastycznych środowisk IDE za pomocą nowych interfejsów API kompilatora obejmowała unikanie alokacji i zarządzanie strategiami buforowania. Ślady PerfView pokazują, że wydajność nowych kompilatorów Języka C# i Visual Basic rzadko jest powiązana z procesorem CPU. Kompilatory mogą być powiązane we/wy podczas odczytywania setek tysięcy lub milionów wierszy kodu, odczytywania metadanych lub emitowania wygenerowanego kodu. Opóźnienia wątku interfejsu użytkownika są prawie wszystkie z powodu wyrzucania elementów bezużytecznych. .NET Framework GC jest wysoce dostrojony pod kątem wydajności i wykonuje wiele swojej pracy jednocześnie podczas wykonywania kodu aplikacji. Jednak pojedyncza alokacja może wyzwolić kosztowną [kolekcję gen2,](../../standard/garbage-collection/fundamentals.md) zatrzymując wszystkie wątki.
  
## <a name="common-allocations-and-examples"></a>Wspólne alokacje i przykłady  
 Przykładowe wyrażenia w tej sekcji mają ukryte alokacje, które wydają się małe. Jednak jeśli duża aplikacja wykonuje wyrażenia tyle razy, mogą one powoduje setki megabajtów, nawet gigabajtów alokacji. Na przykład jednominutowe testy, które symulowały wpisywanie przez dewelopera w edytorze, przydzielały gigabajty pamięci i powodowały, że zespół wydajności skupił się na scenariuszach pisania.
  
### <a name="boxing"></a>Boxing  
 [Boks](../../csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy typy wartości, które zwykle działają na stosie lub w strukturach danych są zawijane w obiekcie. Oznacza to, że można przydzielić obiekt do przechowywania danych, a następnie zwrócić wskaźnik do obiektu. .NET Framework czasami pola wartości ze względu na podpis metody lub typu lokalizacji magazynu. Zawijanie typu wartości w obiekcie powoduje alokację pamięci. Wiele operacji bokserskich może przyczynić się do megabajtów lub gigabajtów alokacji do aplikacji, co oznacza, że aplikacja spowoduje więcej kontrolerów domeny. .NET Framework i kompilatory języka uniknąć boksu, gdy jest to możliwe, ale czasami dzieje się, gdy najmniej się tego spodziewać.
  
 Aby zobaczyć boks w PerfView, otwórz śledzenie i spójrz na stosy alloc sterty GC pod nazwą procesu aplikacji (pamiętaj, PerfView raportuje wszystkie procesy). Jeśli widzisz typy, takie jak <xref:System.Int32?displayProperty=nameWithType> i <xref:System.Char?displayProperty=nameWithType> w ramach alokacji, są typy wartości boksu. Wybranie jednego z tych typów pokaże stosy i funkcje, w których są one zapakowane.
  
 **Przykład 1: metody ciągu i argumenty typu wartości**  
  
 Ten przykładowy kod ilustruje potencjalnie niepotrzebne i nadmierne boks:  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 Ten kod zapewnia funkcje rejestrowania, więc `Log` aplikacja może często wywoływać funkcję, może miliony razy. Problem polega na tym, że wywołanie `string.Format` rozwiązuje <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> przeciążenia.
  
 To przeciążenie wymaga .NET `int` Framework do pola wartości do obiektów, aby przekazać je do tej metody wywołania. Częściowa poprawka jest `id.ToString()` `size.ToString()` wywołanie i przekazać wszystkie ciągi `string.Format` (które są obiektami) do wywołania. Wywołanie `ToString()` przydziela ciąg, ale ta alokacja i tak nastąpi w środku `string.Format`.
  
 Można uznać, że to `string.Format` podstawowe wywołanie jest tylko łączenie ciągów, więc można napisać ten kod zamiast:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Jednak ten wiersz kodu wprowadza alokacji boksu, ponieważ kompiluje do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>. Program .NET Framework musi zawierać literał znaku, aby wywołać`Concat`  
  
 **Poprawka na przykład 1**  
  
 Kompletna poprawka jest prosta. Wystarczy zastąpić literał znaku literałem, który nie ponosi żadnego boksu, ponieważ ciągi są już obiektami:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Przykład 2: boks wyliczenia**  
  
 W tym przykładzie był odpowiedzialny za ogromną ilość alokacji w nowych kompilatorów Języka C# i Visual Basic ze względu na częste używanie typów wyliczenia, szczególnie w operacjach wyszukiwania słownika.
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 Ten problem jest bardzo subtelny. PerfView będzie raport <xref:System.Enum.GetHashCode> to jako boks, ponieważ pola metody podstawowej reprezentacji typu wyliczenia, ze względu na implementację. Jeśli przyjrzysz się uważnie w PerfView, możesz zobaczyć <xref:System.Enum.GetHashCode>dwie alokacje boksu dla każdego wywołania . Kompilator wstawia jeden, a program .NET Framework wstawia drugą.
  
 **Poprawka na przykład 2**  
  
 Można łatwo uniknąć obu alokacji, rzucając <xref:System.Enum.GetHashCode>do podstawowej reprezentacji przed wywołaniem:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Innym typowym źródłem boksu na <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> typy wyliczenia jest metoda. Argument przekazany <xref:System.Enum.HasFlag%28System.Enum%29> do musi być zapakowany. W większości przypadków zastępowanie wywołań <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> testem bitowym jest prostsze i wolne od alokacji.
  
 Pamiętaj o pierwszym fakcie wydajności (czyli nie przedwcześnie optymalizuj) i nie uruchamiaj przepisywania całego kodu w ten sposób. Należy pamiętać o tych kosztów boksu, ale zmienić kod tylko po profilowaniu aplikacji i znalezienie hot spotów.
  
### <a name="strings"></a>Ciągi  
 Manipulacje ciągami są jednymi z największych winowajców alokacji i często pojawiają się w PerfView w pierwszej piątce alokacji. Programy używają ciągów do serializacji, JSON i REST INTERFEJSÓW API. Ciągów można używać jako stałych programowych do współpracy z systemami, gdy nie można używać typów wyliczenia. Gdy profilowanie pokazuje, że ciągi mają duży <xref:System.String> wpływ na <xref:System.String.Format%2A> <xref:System.String.Concat%2A>wydajność, poszukaj wywołań metod, takich jak , <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>i tak dalej. Aby <xref:System.Text.StringBuilder> uniknąć kosztów tworzenia jednego ciągu z wielu elementów pomaga, <xref:System.Text.StringBuilder> ale nawet przydzielanie obiektu może stać się wąskim gardłem, które należy zarządzać.
  
 **Przykład 3: operacje ciągu**  
  
 Kompilator języka C# miał ten kod, który zapisuje tekst sformatowanego komentarza doc XML:  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 Widać, że ten kod wykonuje wiele manipulacji ciągami. Kod używa metod biblioteki do dzielenia wierszy na oddzielne ciągi, `text` do przycinania białych znaków, sprawdzania, czy argument jest komentarzem dokumentacji XML i wyodrębniania podciągów z wierszy.
  
 W pierwszym wierszu `WriteFormattedDocComment` `text.Split` wewnątrz wywołania przydziela nową tablicę trzyelementową jako argument za każdym razem, gdy jest wywoływana. Kompilator musi emitować kod, aby przydzielić tę tablicę za każdym razem. To dlatego, że kompilator nie <xref:System.String.Split%2A> wie, czy przechowuje tablicę gdzieś, gdzie tablica może `WriteFormattedDocComment`być modyfikowana przez inny kod, co miałoby wpływ na późniejsze wywołania . Wywołanie <xref:System.String.Split%2A> również przydziela ciąg dla każdego `text` wiersza i przydziela inną pamięć do wykonania operacji.
  
 `WriteFormattedDocComment`ma trzy wywołania do <xref:System.String.TrimStart%2A> metody. Dwa znajdują się w wewnętrznych pętlach, które powielają pracę i alokacje. Co gorsza, wywołanie <xref:System.String.TrimStart%2A> metody bez argumentów przydziela pustą `params` tablicę (dla parametru) oprócz wyniku ciągu.
  
 Wreszcie istnieje wywołanie <xref:System.String.Substring%2A> metody, która zwykle przydziela nowy ciąg.
  
 **Poprawka na przykład 3**  
  
 W przeciwieństwie do wcześniejszych przykładów, małe zmiany nie można naprawić tych alokacji. Musisz cofnąć się, spojrzeć na problem i podejść do niego inaczej. Na przykład można zauważyć, że `WriteFormattedDocComment()` argument jest ciągiem, który ma wszystkie informacje, które metoda potrzebuje, więc kod może zrobić więcej indeksowania zamiast przydzielania wielu ciągów częściowych.
  
 Zespół wydajności kompilatora rozwiązał wszystkie te alokacje za pomocą kodu w ten sposób:  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 Pierwsza wersja `WriteFormattedDocComment()` przydzielonej tablicy, kilka podciągów i przycięty podciąg wraz z pustą `params` tablicą. To również zaznaczone dla "///". Poprawiony kod używa tylko indeksowania i nic nie przydziela. Znajduje pierwszy znak, który nie jest biały znak, a następnie sprawdza znak według znaku, aby sprawdzić, czy ciąg zaczyna się od "///". Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` zamiast <xref:System.String.TrimStart%2A> zwracać pierwszy indeks (po indeksie początkowym określony), gdzie występuje znak niebiałki. Poprawka nie jest kompletna, ale możesz zobaczyć, jak zastosować podobne poprawki dla kompletnego rozwiązania. Stosując to podejście w całym kodzie, można usunąć `WriteFormattedDocComment()`wszystkie alokacje w .
  
 **Przykład 4: StringBuilder**  
  
 W tym przykładzie użyto <xref:System.Text.StringBuilder> obiektu. Następująca funkcja generuje pełną nazwę typu dla typów ogólnych:  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 Fokus jest na wierszu, który tworzy nowe <xref:System.Text.StringBuilder> wystąpienie. Kod powoduje alokacji `sb.ToString()` i alokacji <xref:System.Text.StringBuilder> wewnętrznej w ramach implementacji, ale nie można kontrolować te alokacje, jeśli chcesz wynik ciągu.
  
 **Poprawka na przykład 4**  
  
 Aby naprawić `StringBuilder` alokację obiektu, buforuj obiekt. Nawet buforowanie pojedynczego wystąpienia, które może zostać odrzucone, może znacznie poprawić wydajność. Jest to nowa implementacja funkcji, pomijając cały kod z wyjątkiem nowego pierwszego i ostatniego wiersza:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Kluczowymi częściami `AcquireBuilder()` są `GetStringAndReleaseBuilder()` nowe i funkcje:  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 Ponieważ nowe kompilatory używają wątków, te implementacje<xref:System.ThreadStaticAttribute> używają pola statycznego <xref:System.Text.StringBuilder>wątku (atrybut) `ThreadStatic` do buforowania , i prawdopodobnie można zrezygnować z deklaracji. Pole statyczne wątku posiada unikatową wartość dla każdego wątku, który wykonuje ten kod.
  
 `AcquireBuilder()`zwraca buforowane <xref:System.Text.StringBuilder> wystąpienie, jeśli istnieje, po wyczyszczeniu go i ustawieniu pola lub pamięci podręcznej na wartość null. W `AcquireBuilder()` przeciwnym razie utworzy nowe wystąpienie i zwróci je, pozostawiając pole lub pamięć podręczną ustawioną na wartość null.
  
 Po zakończeniu z <xref:System.Text.StringBuilder> , wywołać, `GetStringAndReleaseBuilder()` aby uzyskać wynik <xref:System.Text.StringBuilder> ciągu, zapisać wystąpienie w polu lub pamięci podręcznej, a następnie zwrócić wynik. Jest możliwe wykonanie, aby ponownie wprowadzić ten <xref:System.Text.StringBuilder> kod i utworzyć wiele obiektów (chociaż rzadko się zdarza). Kod zapisuje tylko ostatnie <xref:System.Text.StringBuilder> zwolnione wystąpienie do późniejszego użycia. Ta prosta strategia buforowania znacznie zmniejszyła alokacje w nowych kompilatorach. Części programu .NET Framework i MSBuild ("MSBuild") używają podobnej techniki w celu zwiększenia wydajności.
  
 Ta prosta strategia buforowania jest zgodna z dobrym projektem pamięci podręcznej, ponieważ ma limit rozmiaru. Jednak teraz jest więcej kodu niż w oryginale, co oznacza więcej kosztów konserwacji. Strategię buforowania należy przyjąć tylko wtedy, gdy stwierdzono problem z wydajnością, <xref:System.Text.StringBuilder> a perfView pokazał, że alokacje są znaczącym czynnikiem przyczyniającym się.
  
### <a name="linq-and-lambdas"></a>LINQ i lambdas  
Zapytanie zintegrowane z językiem (LINQ), w połączeniu z wyrażeniami lambda, jest przykładem funkcji produktywności. Jednak jego użycie może mieć znaczący wpływ na wydajność w czasie i może się okazać, że trzeba przepisać kod.
  
 **Przykład 5: Lambdas, Lista\<T> i IEnumerable\<T>**  
  
 W tym przykładzie użyto [LINQ i kod stylu funkcjonalnego,](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) aby znaleźć symbol w modelu kompilatora, biorąc pod uwagę ciąg nazwy:  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 Nowy kompilator i środowiska IDE `FindMatchingSymbol()` zbudowany na nim wywołać bardzo często i istnieje kilka ukrytych alokacji w jednej linii tej funkcji kodu. Aby zbadać te alokacje, najpierw podziel pojedynczy wiersz kodu funkcji na dwa wiersze:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 W pierwszym wierszu `s => s.Name == name` [wyrażenie lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) zamyka się `name` [nad](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) zmienną lokalną . Oznacza to, że oprócz przydzielania obiektu dla [delegata,](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) który `predicate` posiada, kod przydziela klasę statyczną do `name`przechowywania środowiska, które przechwytuje wartość . Kompilator generuje kod, podobnie jak następujące:  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 Dwie `new` alokacje (jeden dla klasy środowiska i jeden dla delegata) są teraz jawne.
  
 Teraz spójrz na `FirstOrDefault`wezwanie do . Ta metoda rozszerzenia <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> na typ wiąże się z alokacji zbyt. Ponieważ `FirstOrDefault` przyjmuje <xref:System.Collections.Generic.IEnumerable%601> obiekt jako swój pierwszy argument, można rozwinąć wywołanie do następującego kodu (uproszczony bit do dyskusji):  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 Zmienna `symbols` ma <xref:System.Collections.Generic.List%601>typ . Typ <xref:System.Collections.Generic.List%601> kolekcji <xref:System.Collections.Generic.IEnumerable%601> implementuje i sprytnie definiuje moduł<xref:System.Collections.Generic.IEnumerator%601> wyliczacza (interfejs), który <xref:System.Collections.Generic.List%601> implementuje z . `struct` Przy użyciu struktury zamiast klasy oznacza, że zwykle uniknąć alokacji sterty, co z kolei może mieć wpływ na wydajność wyrzucania elementów bezużytecznych. Wyliczacze są zazwyczaj używane z `foreach` pętli języka, który używa struktury wyliczacza, ponieważ jest zwracany na stosie wywołań. Zwiększanie wskaźnik stosu wywołań, aby zrobić miejsce dla obiektu nie wpływa na GC sposób alokacji sterty nie.
  
 W przypadku rozszerzonego `FirstOrDefault` połączenia kod musi `GetEnumerator()` wywołać <xref:System.Collections.Generic.IEnumerable%601>. Przypisanie `symbols` do `enumerable` zmiennej `IEnumerable<Symbol>` typu traci informacje, że <xref:System.Collections.Generic.List%601>rzeczywisty obiekt jest . Oznacza to, że gdy kod pobiera wyliczacz z `enumerable.GetEnumerator()`, .NET Framework musi pole `enumerator` zwróconej struktury, aby przypisać go do zmiennej.
  
 **Poprawka na przykład 5**  
  
 Poprawka jest przepisać w następujący sposób, zastępując jego pojedynczy wiersz kodu z sześciu wierszy kodu, które są nadal zwięzłe, `FindMatchingSymbol` łatwe do odczytania i zrozumienia i łatwe do utrzymania:  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 Ten kod nie używa metod rozszerzenia LINQ, lambdas lub wyliczaczy i nie ponosi żadnych alokacji. Nie ma żadnych alokacji, ponieważ kompilator może zobaczyć, że `symbols` kolekcja jest <xref:System.Collections.Generic.List%601> i może powiązać wynikowy wyliczacz (strukturę) ze zmienną lokalną o odpowiednim typie, aby uniknąć boksu. Oryginalna wersja tej funkcji był doskonałym przykładem ekspresji moc C# i produktywności .NET Framework. Ta nowa i bardziej wydajna wersja zachowuje te cechy bez dodawania żadnego złożonego kodu do utrzymania.
  
### <a name="async-method-caching"></a>Buforowanie metody asynchronii  

W następnym przykładzie pokazano typowy problem podczas próby użycia buforowanych wyników w metodzie [asynchronii.](../../csharp/programming-guide/concepts/async/index.md)
  
 **Przykład 6: buforowanie metod asynchronizowych**  
  
 Funkcje IDE programu Visual Studio oparte na nowych kompilatorach Języka C# i Visual Basic często pobierają drzewa składni, a kompilatory używają asynchronacji, aby zachować responsywność programu Visual Studio. Oto pierwsza wersja kodu, który można napisać, aby uzyskać drzewo składni:  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 Widać, że `GetSyntaxTreeAsync()` wywołanie wywołuje `Parser`wystąpienia , analizuje kod, a <xref:System.Threading.Tasks.Task> następnie `Task<SyntaxTree>`zwraca obiekt, . Kosztowna część jest przydzielanie `Parser` wystąpienia i analizowanie kodu. Funkcja <xref:System.Threading.Tasks.Task> zwraca, dzięki czemu wywołujący mogą oczekiwać na pracę analizy i zwolnić wątku interfejsu użytkownika, aby reagować na dane wejściowe użytkownika.
  
 Kilka funkcji programu Visual Studio może próbować uzyskać tego samego drzewa składni, więc można napisać następujący kod do pamięci podręcznej wynik analizy, aby zaoszczędzić czas i alokacje. Jednak ten kod ponosi alokacji:  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 Widzisz, że nowy kod z buforowania ma `SyntaxTree` pole o nazwie `cachedResult`. Gdy to pole `GetSyntaxTreeAsync()` ma wartość null, wykonuje pracę i zapisuje wynik w pamięci podręcznej. `GetSyntaxTreeAsync()`zwraca `SyntaxTree` obiekt. Problem polega na tym, `async` że `Task<SyntaxTree>`gdy masz funkcję typu `SyntaxTree`, a zwracasz wartość typu, kompilator emituje `Task<SyntaxTree>.FromResult()`kod, aby przydzielić zadanie do przechowywania wyniku (za pomocą ). Zadanie jest oznaczone jako ukończone, a wynik jest natychmiast dostępny. W kodzie dla nowych <xref:System.Threading.Tasks.Task> kompilatorów obiekty, które zostały już ukończone wystąpił tak często, że ustalenie tych alokacji znacznie poprawiła czas reakcji.
  
 **Poprawka na przykład 6**  
  
 Aby usunąć <xref:System.Threading.Tasks.Task> ukończoną alokację, można buforować obiekt Zadanie z ukończonym wynikiem:  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 Ten kod zmienia `cachedResult` typ `Task<SyntaxTree>` funkcji `async` pomocnika, która przechowuje oryginalny `GetSyntaxTreeAsync()`kod z . `GetSyntaxTreeAsync()`teraz używa [operatora scalania null](../../csharp/language-reference/operators/null-coalescing-operator.md) `cachedResult` do zwrócenia, jeśli nie jest null. Jeśli `cachedResult` jest null, a następnie `GetSyntaxTreeAsync()` wywołuje `GetSyntaxTreeUncachedAsync()` i buforuje wynik. Należy `GetSyntaxTreeAsync()` zauważyć, że nie `GetSyntaxTreeUncachedAsync()` oczekuje na wywołanie, jak kod normalnie. Nieużywany await `GetSyntaxTreeUncachedAsync()` oznacza, `GetSyntaxTreeAsync()` że gdy <xref:System.Threading.Tasks.Task>zwraca jego <xref:System.Threading.Tasks.Task> obiekt, natychmiast zwraca . Teraz buforowany wynik jest <xref:System.Threading.Tasks.Task>, więc nie ma żadnych alokacji, aby zwrócić wynik w pamięci podręcznej.
  
### <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Oto kilka punktów dotyczących potencjalnych problemów w dużych aplikacjach lub aplikacjach, które przetwarzają dużo danych.
  
 **Słowniki**  
  
 Słowniki są używane wszechobecne w wielu programach, i choć słowniki są bardzo wygodne i z natury skuteczne. Jednak są one często używane niewłaściwie. W programie Visual Studio i nowych kompilatorów analizy pokazuje, że wiele słowników zawiera jeden element lub były puste. Pusty <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pól i zajmuje 48 bajtów na stercie na komputerze x86. Słowniki są świetne, gdy potrzebujesz struktury mapowania lub danych zespolowych z wyszukiwaniem w czasie stałym. Jednak, gdy masz tylko kilka elementów, tracisz dużo miejsca za pomocą słownika. Zamiast tego, na przykład, można iteratively patrzeć przez `List<KeyValuePair\<K,V>>`, tak szybko. Jeśli słownik jest używany tylko do ładowania go z danymi, a następnie odczytać z niego (bardzo często wzorzec), przy użyciu tablicy posortowane z N(log(N)) wyszukiwania może być prawie tak szybko, w zależności od liczby elementów, których używasz.
  
 **Klasy a struktury**  
  
 W pewnym sensie klasy i struktury zapewniają klasyczny kompromis przestrzeni/czasu do strojenia aplikacji. Klasy ponoszą 12 bajtów narzutów na komputerze x86, nawet jeśli nie mają żadnych pól, ale są one niedrogie do przekazania, ponieważ zajmuje tylko wskaźnik do odwoływania się do wystąpienia klasy. Struktury nie ponoszą alokacji sterty, jeśli nie są one zapakowane, ale po przeniesieniu dużych struktur jako argumenty funkcji lub zwracanie wartości, zajmuje czas procesora CPU, aby niepodzielnie skopiować wszystkie elementy członkowskie danych struktur. Uważaj na powtarzające się wywołania właściwości, które zwracają struktury i buforują wartość właściwości w zmiennej lokalnej, aby uniknąć nadmiernego kopiowania danych.
  
 **Pamięci podręczne**  
  
 Typowym trikiem wydajności jest buforowanie wyników. Jednak pamięć podręczna bez ograniczenia rozmiaru lub zasady usuwania może być przeciek pamięci. Podczas przetwarzania dużych ilości danych, jeśli trzymasz dużo pamięci w pamięci podręcznej, może spowodować wyrzucanie elementów bezużytecznych zastąpić korzyści z wyszukiwania w pamięci podręcznej.
  
 W tym artykule omówiliśmy, jak należy pamiętać o objawów wąskiego gardła wydajności, które mogą mieć wpływ na szybkość reakcji aplikacji, szczególnie w przypadku dużych systemów lub systemów, które przetwarzają dużą ilość danych. Typowe winowajców obejmują boks, manipulacje ciągami, LINQ i lambda, buforowanie metod asynchronizowanych, buforowanie bez limitu rozmiaru lub zasady usuwania, niewłaściwe użycie słowników i przekazywanie struktur. Pamiętaj o czterech faktach dotyczących dostrajania aplikacji:  
  
- Nie optymalizuj przedwcześnie — bądź produktywny i dostrajaj aplikację, gdy zauważysz problemy.
  
- Profile nie kłamią – zgadujesz, jeśli nie mierzysz.
  
- Dobre narzędzia robią różnicę - pobierz PerfView i wypróbuj.
  
- Chodzi o alokacje — to jest, gdy zespół platformy kompilator spędził większość czasu na poprawę wydajności nowych kompilatorów.
  
## <a name="see-also"></a>Zobacz też

- [Film przedstawiający prezentację tego tematu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Przewodnik dla początkujących do profilowania wydajności](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Wydajność](index.md)
- [Wskazówki dotyczące wydajności .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Samouczek Kanału 9 PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [Zestaw SDK platformy kompilatora platformy .NET](../../csharp/roslyn-sdk/index.md)
- [repozytorium dotnet/roslyn na GitHub](https://github.com/dotnet/roslyn)
