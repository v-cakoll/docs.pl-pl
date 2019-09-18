---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e4b5822306fa8f4e6b4437f4a1bef92b53a86b9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046135"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych .NET Framework aplikacji lub aplikacji, które przetwarzają duże ilości danych, takich jak pliki lub bazy danych. Te porady pochodzą z ponownego zapisywania kompilatorów C# i Visual Basic w kodzie zarządzanym, a ten artykuł zawiera kilka rzeczywistych przykładów z C# kompilatora. 
  
 .NET Framework jest wysoce wydajny w przypadku kompilowania aplikacji. Zaawansowane i bezpieczne języki oraz bogate kolekcje bibliotek sprawiają, że tworzenie aplikacji jest wysoce rozwijającemu. Jednak dzięki doskonałej produktywności spoczywa odpowiedzialność. Należy używać wszystkich możliwości .NET Framework, ale należy przygotować się do dostrajania wydajności kodu, jeśli jest to konieczne. 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Dlaczego Nowa wydajność kompilatora ma zastosowanie do aplikacji  
 Zespół .NET Compiler Platform ("Roslyn") zapisał w kodzie C# zarządzanym i Visual Basic kompilatory w celu udostępnienia nowych interfejsów API do modelowania i analizowania kodu, tworzenia narzędzi i włączania znacznie bogatszych rozwiązań obsługujących kod w programie Visual Studio. Przepisanie kompilatorów i Tworzenie środowiska programu Visual Studio na nowych kompilatorach ujawniło przydatny wgląd w dane dotyczące wydajności, które mają zastosowanie do dowolnej dużej aplikacji .NET Framework lub dowolnej aplikacji, która przetwarza dużą ilość danych. Nie musisz wiedzieć o kompilatorach, aby skorzystać z szczegółowych informacji i przykładów z C# kompilatora. 
  
 Program Visual Studio korzysta z interfejsów API kompilatora do kompilowania wszystkich funkcji IntelliSense, które są miłość przez użytkowników, takich jak kolorowanie identyfikatorów i słów kluczowych, listy uzupełniania składni, zygzaki dla błędów, wskazówki dotyczące parametrów, problemy z kodem i akcje związane z kodem. Program Visual Studio udostępnia tę pomoc podczas wpisywania i zmieniania kodu przez deweloperów, a program Visual Studio musi przestać odpowiadać, gdy kompilator ciągle modeluje deweloperów kodu. 
  
 Gdy użytkownicy końcowi współpracują z aplikacją, spodziewają się, że odpowiadają. Wpisywanie lub obsługa poleceń nie powinna być nigdy blokowana. Pomoc powinna być wyświetlona szybko lub w przypadku, gdy użytkownik kontynuuje wpisywanie. Aplikacja powinna unikać blokowania wątku interfejsu użytkownika z długimi obliczeniami, które sprawiają, że aplikacja jest powolna. 
  
 Aby uzyskać więcej informacji na temat kompilatorów Roslyn, zobacz [zestaw SDK .NET compiler platform](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Tylko fakty  
 Te fakty należy wziąć pod uwagę podczas dostrajania wydajności i tworzenia odpowiedzi .NET Framework aplikacji. 
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Nie Optymalizuj przedwcześnie  
 Pisanie kodu, który jest bardziej skomplikowany niż musi być związane z konserwacją, debugowaniem i polerowaniem. Doświadczeni programiści mają intuicyjny opanujesz sposobu rozwiązywania problemów z kodowaniem i pisania bardziej wydajnego kodu. Jednak czasami w sposób przedwcześnie optymalizuje swój kod. Na przykład korzystają one z tabeli skrótów, gdy prosta tablica wystarcza, lub użyj skomplikowanej pamięci podręcznej, która może wyciekać pamięć, a nie po prostu reobliczaniu wartości. Nawet jeśli jesteś programistą, należy przetestować wydajność i analizować kod, gdy znajdziesz problemy. 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Jeśli nie mierzy się, nastąpi odgadnięcie  
 Profile i pomiary nie znajdują się. Profile pokazują, czy procesor CPU jest w pełni załadowany, czy też jest blokowany na dyskach we/wy. Profile informują o rodzaju i ilości pamięci, która jest przydzielana, oraz o tym, czy procesor CPU poświęca dużo czasu na [wyrzucanie elementów bezużytecznych](../../standard/garbage-collection/index.md) (GC). 
  
 Należy ustawić cele wydajnościowe najważniejszych środowisk klienta lub scenariuszy w aplikacji oraz testy zapisu w celu mierzenia wydajności. Zbadaj nieudane testy, stosując metodę naukową: Użyj profilów, aby Ci pomóc, hypothesize się, co może być problemem, i przetestuj hipotezę przy użyciu eksperymentu lub zmiany kodu. Ustalaj bazowe pomiary wydajności w czasie z regularnym testowaniem, dzięki czemu można izolować zmiany powodujące wydajność regresji. Dzięki podejściu wydajności w rygorystyczny sposób można uniknąć marnowania czasu z niepotrzebnymi aktualizacjami kodu. 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Dobre narzędzia sprawiają, że wszystkie różnice  
 Dobre narzędzia pozwalają szybko przechodzić do największych problemów z wydajnością (procesor CPU, pamięć lub dysk) i pomóc w znalezieniu kodu, który powoduje te wąskie gardła. Firma Microsoft dostarcza różnorodne narzędzia do oceny wydajności, takie jak [program Visual Studio profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) i [Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567). 
  
 Narzędzia PerfView to bezpłatne i wszechstronne narzędzie, które ułatwia skoncentrowanie się na szczegółowych problemach, takich jak we/wy dysku, zdarzenia GC i pamięć. Można przechwytywać zdarzenia [śledzenia zdarzeń dotyczące wydajności dla systemu Windows](../wcf/samples/etw-tracing.md) (ETW) i łatwo przeglądać dla każdej aplikacji, na jeden proces, na stos i informacje o wątkach. Narzędzia PerfView pokazuje, jak dużo i jakiego rodzaju pamięci przydziela aplikacja oraz które funkcje lub stosy wywołań przyczyniają się do przydzielenia pamięci. Aby uzyskać szczegółowe informacje, zobacz temat rozbudowane tematy pomocy, pokazy i filmy wideo dołączone do narzędzia (na przykład [samouczki narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) w witrynie Channel 9). 
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Wszystkie przydziały  
 Możesz zastanowić się nad tworzeniem aplikacji, która odpowiada .NET Framework wszystkim algorytmom, na przykład przy użyciu szybkiego sortowania zamiast sortowania bąbelkowego, ale nie jest to przypadek. Największym czynnikiem podczas tworzenia aplikacji, która odpowiada, jest przydzielanie pamięci, zwłaszcza gdy aplikacja jest bardzo duża lub przetwarza duże ilości danych. 
  
 Prawie wszystkie prace do tworzenia odpowiedzi na środowisko IDE dzięki nowym interfejsom API kompilatora, które mają na celu uniknięcie alokacji i zarządzania strategiami buforowania. Ślady narzędzia PerfView pokazują, że wydajność nowych C# i kompilatorów Visual Basic jest rzadko związana z procesorem CPU. Kompilatory mogą być powiązane we/wy w przypadku odczytywania setek tysięcy lub milionów wierszy kodu, odczytywania metadanych lub emitowania wygenerowanego kodu. Opóźnienia wątku interfejsu użytkownika są niemal wszystkie ze względu na wyrzucanie elementów bezużytecznych. .NET Framework GC jest wysoce dostrojony do wydajności i wykonuje wiele zadań jednocześnie podczas wykonywania kodu aplikacji. Jednak pojedyncze alokacje mogą wyzwalać kosztowną kolekcję [Gen2](../../standard/garbage-collection/fundamentals.md) , zatrzymując wszystkie wątki. 
  
## <a name="common-allocations-and-examples"></a>Typowe alokacje i przykłady  
 W przykładowych wyrażeniach w tej sekcji znajdują się ukryte przydziały, które są wyświetlane jako małe. Jeśli jednak duża aplikacja wykonuje wyrażenia wystarczająco długo, może to spowodować setki megabajtów, nawet gigabajtów przydziałów. Na przykład testy jednominutowe, które symulują wpisywanie przez dewelopera w edytorze przydzieloną gigabajty pamięci i doprowadziły do skoncentrowania się zespołu wydajności w przypadku wpisywania scenariuszy. 
  
### <a name="boxing"></a>Boxing  
 [Opakowanie](../../csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy typy wartości, które zwykle znajdują się na stosie lub w strukturach danych, są zawijane w obiekcie. Oznacza to, że przydzielasz obiekt do przechowywania danych, a następnie zwracasz wskaźnik do obiektu. .NET Framework czasami pola wartości ze względu na podpis metody lub typu lokalizacji magazynu. Otoka typu wartości w obiekcie powoduje alokację pamięci. Wiele operacji pakowania może współtworzyć megabajty lub gigabajty alokacji dla aplikacji, co oznacza, że aplikacja spowoduje więcej operacje odzyskiwania pamięci. .NET Framework i kompilatory języka unikają pakowania, gdy jest to możliwe, ale czasami zdarza się, gdy jest to konieczne. 
  
 Aby zobaczyć opakowanie w narzędzia PerfView, Otwórz ślad i sprawdź stosy alokacji sterty GC pod nazwą procesu aplikacji (Pamiętaj, narzędzia PerfView raporty dotyczące wszystkich procesów). Jeśli widzisz typy takie <xref:System.Int32?displayProperty=nameWithType> jak <xref:System.Char?displayProperty=nameWithType> i w obszarze alokacje, nastąpi wypakowywanie typów wartości. Wybranie jednego z tych typów spowoduje wyświetlenie stosów i funkcji, w których są one opakowane. 
  
 **Przykład 1: metody ciągów i argumenty typu wartości**  
  
 Ten przykładowy kod ilustruje potencjalnie niepotrzebne i nadmierne opakowanie:  
  
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
  
 Ten kod udostępnia funkcje rejestrowania, dzięki czemu aplikacja może często wywoływać `Log` funkcję, co może być miliony razy. Problem polega na tym, że wywołanie `string.Format` jest rozpoznawane <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> jako Przeciążenie. 
  
 To Przeciążenie wymaga .NET Framework do `int` umieszczania wartości w obiektach, aby przekazać je do tego wywołania metody. Częściowa poprawka polega na wywołaniu `id.ToString()` i `size.ToString()` przejściu wszystkich ciągów (które `string.Format` są obiektami) do wywołania. Wywołanie `ToString()` przydzieli ciąg, ale ta alokacja będzie nadal w `string.Format`obrębie. 
  
 Można wziąć pod uwagę, że to podstawowe `string.Format` wywołanie jest tylko ciąg łączenia, więc można napisać ten kod zamiast:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Jednak ten wiersz kodu wprowadza alokację opakowania, ponieważ kompiluje się do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>. .NET Framework musi mieć pole literału znakowego do wywołania`Concat`  
  
 **Poprawka na przykład 1**  
  
 Pełna poprawka jest prosta. Po prostu Zastąp literał znakowy literałem ciągu, który nie jest używany, ponieważ ciągi są już obiektami:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Przykład 2: opakowanie enum**  
  
 Ten przykład był odpowiedzialny za ogromną ilość przydziału w nowych C# i Visual Basic kompilatorach ze względu na częste korzystanie z typów wyliczeniowych, szczególnie w operacjach wyszukiwania słownika. 
  
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
  
 Ten problem jest bardzo delikatny. Narzędzia PerfView mógłby zgłosić ten fakt <xref:System.Enum.GetHashCode> jako opakowanie, ponieważ metoda pola przedstawia podstawową reprezentację typu wyliczenia, ze względów związanych z implementacją. Jeśli szukasz blisko w narzędzia PerfView, mogą zostać wyświetlone dwa przydziały dla każdego wywołania <xref:System.Enum.GetHashCode>. Kompilator wstawia jeden, a .NET Framework wstawia pozostałe. 
  
 **Poprawka na przykład 2**  
  
 Można łatwo uniknąć obydwu przydziałów przez rzutowanie na podstawową reprezentację przed wywołaniem <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Innym wspólnym źródłem opakowania w typach wyliczeniowych jest <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> Metoda. Argument przeszedł do <xref:System.Enum.HasFlag%28System.Enum%29> musi być opakowany. W większości przypadków zastępowanie wywołań <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> z testem bitowym jest prostsze i bezpłatne. 
  
 Zachowaj pierwszy fakt wydajności (to oznacza, że nie jest przedwcześnie zoptymalizowany) i nie rozpoczynaj ponownego zapisywania całego kodu w ten sposób. Zapoznaj się z tymi kosztami opakowania, ale Zmień kod tylko po przeprowadzeniu profilowania aplikacji i znalezieniu aktywnych miejsc. 
  
### <a name="strings"></a>Ciągi  
 Manipulowanie ciągami to niektóre największe culprits dla przydziałów i często są one wyświetlane w narzędzia PerfView w pierwszych pięciu alokacjach. Programy używają ciągów do serializacji, JSON i interfejsów API REST. Można używać ciągów jako stałych programistycznych do współdziałania z systemami, gdy nie można używać typów wyliczeniowych. Gdy profilowanie pokazuje <xref:System.String> , że ciągi mają wysoce wpływ na wydajność, należy poszukać wywołań metod, takich jak <xref:System.String.Join%2A> <xref:System.String.Format%2A>, <xref:System.String.Substring%2A> <xref:System.String.Concat%2A> <xref:System.String.Split%2A>,,, i tak dalej. Użycie <xref:System.Text.StringBuilder> usługi pozwala uniknąć ponoszenia kosztów tworzenia jednego ciągu z wielu kawałków, ale nawet przydzielenie <xref:System.Text.StringBuilder> obiektu może stać się wąskim gardłem, który trzeba zarządzać. 
  
 **Przykład 3: operacje na ciągach**  
  
 C# Kompilator miał ten kod, który zapisuje tekst sformatowanego komentarza dokumentu XML:  
  
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
  
 Można zobaczyć, że ten kod wykonuje wiele operacji manipulowania ciągiem. Kod używa metod biblioteki do dzielenia wierszy na osobne ciągi, do przycinania białego znaku, aby sprawdzić, czy `text` argument jest komentarzem dokumentacji XML i wyodrębnić podciągi z wierszy. 
  
 W pierwszym wierszu wewnątrz `WriteFormattedDocComment` `text.Split` , wywołanie przydziela nową tablicę trzech elementów jako argument przy każdym wywołaniu. Kompilator musi emitować kod, aby przydzielić tę tablicę za każdym razem. Dzieje się tak, ponieważ kompilator nie wie <xref:System.String.Split%2A> , czy przechowuje tablicę w miejscu, w którym tablica może być modyfikowana przez inny kod, co `WriteFormattedDocComment`wpłynie na późniejsze wywołania do. Wywołanie w celu <xref:System.String.Split%2A> przydzielania również ciągu dla każdego wiersza w `text` i przydziela inne pamięci do wykonania operacji. 
  
 `WriteFormattedDocComment`ma trzy wywołania <xref:System.String.TrimStart%2A> metody. Dwa znajdują się w wewnętrznych pętlach, które duplikują zadania i przydziały. Aby przyczynić się do gorszenia <xref:System.String.TrimStart%2A> , wywołanie metody bez argumentów przypisuje pustą tablicę ( `params` dla parametru) oprócz wyniku ciągu. 
  
 Na koniec istnieje wywołanie <xref:System.String.Substring%2A> metody, która zwykle przypisuje nowy ciąg. 
  
 **Poprawka na przykład 3**  
  
 W przeciwieństwie do wcześniejszych przykładów, małe edycje nie mogą naprawić tych przydziałów. Należy wykonać krok po kroku, przyjrzeć się problemowi i zastosować go inaczej. Na przykład można zauważyć, że argument `WriteFormattedDocComment()` jest ciągiem, który zawiera wszystkie informacje, których potrzebuje Metoda, więc kod może przetworzyć więcej indeksowania zamiast alokowania wiele ciągów częściowych. 
  
 Zespół wydajności kompilatora wszystkie te przydziały z kodem podobnym do poniższego:  
  
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
  
 Pierwsza wersja `WriteFormattedDocComment()` przydzieloną tablicę, kilka podciągów i przycięty podciąg wraz z pustą `params` tablicą. Sprawdzana jest również wartość "///". Poprawiony kod używa tylko indeksowania i alokuje Nothing. Znajduje pierwszy znak, który nie jest biały, a następnie sprawdza znak według znaku, aby zobaczyć, czy ciąg rozpoczyna się od "///". Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` <xref:System.String.TrimStart%2A> zamiast nie zwracać pierwszego indeksu (po określonym indeksie początkowym), w którym występuje znak niebędący odstępem. Naprawa nie została ukończona, ale możesz zobaczyć, jak zastosować podobne poprawki do kompletnego rozwiązania. Stosując to podejście w całym kodzie, można usunąć wszystkie alokacje w `WriteFormattedDocComment()`. 
  
 **Przykład 4: StringBuilder**  
  
 W <xref:System.Text.StringBuilder> tym przykładzie używa obiektu. Następująca funkcja generuje pełną nazwę typu dla typów ogólnych:  
  
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
  
 Fokus znajduje się w wierszu, który tworzy nowe <xref:System.Text.StringBuilder> wystąpienie. Kod powoduje alokację `sb.ToString()` i wewnętrzne przydziały <xref:System.Text.StringBuilder> w ramach implementacji, ale nie można kontrolować tych alokacji, jeśli chcesz uzyskać wynik ciągu. 
  
 **Poprawka na przykład 4**  
  
 Aby naprawić `StringBuilder` alokację obiektu, przebuforuj obiekt. Nawet buforowanie pojedynczego wystąpienia, które może zostać wywołane, może znacząco poprawić wydajność. Jest to nowa implementacja funkcji, pomijając cały kod z wyjątkiem nowych i ostatnich wierszy:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Najważniejsze części to nowe `AcquireBuilder()` i `GetStringAndReleaseBuilder()` funkcje:  
  
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
  
 Ponieważ nowe kompilatory używają wątków, te implementacje używają pola statycznego wątku (<xref:System.ThreadStaticAttribute> atrybutu) do <xref:System.Text.StringBuilder>buforowania i prawdopodobnie można forgo `ThreadStatic` deklarację. Pole statyczne wątku przechowuje unikatową wartość dla każdego wątku, który wykonuje ten kod. 
  
 `AcquireBuilder()`Zwraca buforowane <xref:System.Text.StringBuilder> wystąpienie, jeśli istnieje, po jego wyczyszczeniu i ustawieniu pola lub pamięci podręcznej na wartość null. W przeciwnym razie tworzy nowe wystąpienie i zwraca je, pozostawiając pole lub pamięć podręczną ustawioną na wartość null. `AcquireBuilder()` 
  
 Gdy wszystko będzie gotowe <xref:System.Text.StringBuilder> , należy wywołać `GetStringAndReleaseBuilder()` , aby uzyskać wynik <xref:System.Text.StringBuilder> ciągu, zapisać wystąpienie w polu lub w pamięci podręcznej, a następnie zwrócić wynik. Można wykonać ponowne wprowadzenie tego kodu i utworzyć wiele <xref:System.Text.StringBuilder> obiektów (chociaż zdarza się to rzadko). Kod zapisuje tylko ostatnio wydane <xref:System.Text.StringBuilder> wystąpienie do późniejszego użycia. Ta prosta strategia buforowania znacznie zmniejsza alokacje w nowych kompilatorach. Części .NET Framework i MSBuild ("MSBuild") używają podobnej metody w celu zwiększenia wydajności. 
  
 Ta prosta strategia buforowania jest zgodna z dobrym projektem pamięci podręcznej, ponieważ ma limit rozmiaru. Jednak więcej kodu jest teraz niż w oryginalnym, co oznacza więcej kosztów konserwacji. Strategię buforowania należy zastosować tylko wtedy, gdy znaleziono problem z wydajnością, a narzędzia PerfView wykazało, <xref:System.Text.StringBuilder> że alokacje są istotnym współautorem. 
  
### <a name="linq-and-lambdas"></a>LINQ i lambda  
W połączeniu z wyrażeniami lambda jest przykładem funkcji produktywności (LINQ, Language-Integrated Query). Jednak jego użycie może mieć znaczny wpływ na wydajność w miarę upływu czasu i może być konieczne ponowne napisanie kodu.
  
 **Przykład 5: Wyrażenia lambda, listy\<T > i IEnumerable\<t >**  
  
 W tym przykładzie używa [kodu LINQ i języka stylu funkcjonalności](https://blogs.msdn.microsoft.com/charlie/2007/01/27/anders-hejlsberg-on-linq-and-functional-programming/) , aby znaleźć symbol w modelu kompilatora, przy użyciu ciągu nazwy:  
  
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
  
 Nowy kompilator i środowiska IDE, które są oparte na wywołaniu `FindMatchingSymbol()` IT bardzo często, i istnieje kilka ukrytych alokacji w jednym wierszu kodu tej funkcji. Aby przejrzeć te przydziały, najpierw Podziel pojedynczy wiersz kodu funkcji na dwa wiersze:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 W pierwszym wierszu [wyrażenie](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` lambda jest [zamykane](https://blogs.msdn.microsoft.com/ericlippert/2003/09/17/what-are-closures/) na zmiennej `name`lokalnej. Oznacza to, że oprócz przydzielenia obiektu [delegata](../../csharp/language-reference/keywords/delegate.md) , który `predicate` przechowuje, kod przydziela klasę statyczną do przechowywania środowiska, które `name`przechwytuje wartość. Kompilator generuje kod podobny do następującego:  
  
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
  
 Dwa `new` alokacje (jeden dla klasy środowiska i jeden dla delegata) są teraz jawne. 
  
 Teraz przyjrzyj się `FirstOrDefault`wywołaniu. Ta metoda <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozszerzania typu powoduje również alokację. `FirstOrDefault` Ponieważ<xref:System.Collections.Generic.IEnumerable%601> przyjmuje obiekt jako pierwszy argument, można rozszerzyć wywołanie do następującego kodu (uproszczony bit na potrzeby dyskusji):  
  
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
  
 Zmienna ma typ <xref:System.Collections.Generic.List%601>. `symbols` <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601> `struct`Typ kolekcji implementuje i Cleverly definiuje<xref:System.Collections.Generic.List%601> moduł wyliczający (interfejs) implementujący za pomocą. <xref:System.Collections.Generic.List%601> Użycie struktury zamiast klasy oznacza zwykle uniknięcie przydziałów sterty, co z kolei może wpłynąć na wydajność odzyskiwania pamięci. Moduły wyliczające są zwykle używane z `foreach` pętlą języka, która używa struktury modułu wyliczającego, gdy zostanie zwrócona na stosie wywołań. Zwiększenie wskaźnika stosu wywołań w celu zapewnienia pokoju dla obiektu nie ma wpływu na sposób alokacji sterty. 
  
 W przypadku wywołania rozszerzonego `FirstOrDefault` kod musi wywołać `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>. Przypisanie `symbols` <xref:System.Collections.Generic.List%601>do zmiennej typu `IEnumerable<Symbol>` powoduje utratę informacji, które są rzeczywistym obiektem. `enumerable` Oznacza to, że gdy kod pobiera moduł wyliczający z `enumerable.GetEnumerator()`, .NET Framework musi mieć pole zwróconej struktury, aby przypisać go `enumerator` do zmiennej. 
  
 **Poprawka na przykład 5**  
  
 Poprawkę należy wykonać `FindMatchingSymbol` w następujący sposób, zamieniając swój pojedynczy wiersz kodu na sześć wierszy kodu, które są nadal zwięzłe, czytelne i zrozumiałe oraz łatwe w obsłudze:  
  
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
  
 Ten kod nie używa metod rozszerzeń LINQ, wyrażeń lambda ani modułów wyliczających i nie ma żadnych przydziałów. Nie ma żadnych alokacji, ponieważ kompilator może zobaczyć, że `symbols` kolekcja <xref:System.Collections.Generic.List%601> jest i może powiązać powstający moduł wyliczający (strukturę) ze zmienną lokalną z właściwym typem, aby uniknąć napakowywania. Oryginalną wersją tej funkcji była doskonały Przykładowa moc C# i produktywność .NET Framework. Ta nowa i wydajniejsza wersja zachowuje te cechy bez dodawania kodu złożonego do obsługi. 
  
### <a name="async-method-caching"></a>Buforowanie metod asynchronicznych  

W następnym przykładzie przedstawiono typowy problem występujący podczas próby użycia zbuforowanych wyników w metodzie [asynchronicznej](../../csharp/programming-guide/concepts/async/index.md) .
  
 **Przykład 6: buforowanie w metodach asynchronicznych**  
  
 Funkcje środowiska IDE programu Visual Studio oparte na nowych C# i Visual Basic kompilatorach często pobierają drzewa składniowe, a kompilatory używają Async w celu zapewnienia, że program Visual Studio reaguje. Oto pierwsza wersja kodu, którą można napisać, aby uzyskać drzewo składni:  
  
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
  
 Można zobaczyć, że wywoływanie `GetSyntaxTreeAsync()` tworzy wystąpienia a `Parser`, analizuje kod <xref:System.Threading.Tasks.Task> , a następnie zwraca obiekt, `Task<SyntaxTree>`. Kosztowna część przydziela `Parser` wystąpienie i analizuje kod. Funkcja zwraca obiekt <xref:System.Threading.Tasks.Task> , aby wywołujący mogą oczekiwać na przeanalizowanie i zwolnić wątek interfejsu użytkownika, aby odpowiadał na dane wejściowe użytkownika. 
  
 Kilka funkcji programu Visual Studio może próbować uzyskać to samo drzewo składni, więc można napisać następujący kod w celu przetworzenia pamięci podręcznej wynik analizy w celu zaoszczędzenia czasu i alokacji. Jednak ten kod wiąże się z alokacją:  
  
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
  
 Zobaczysz, że nowy kod z buforowaniem ma `SyntaxTree` pole o `cachedResult`nazwie. Gdy to pole ma wartość null `GetSyntaxTreeAsync()` , program wykonuje i zapisuje wynik w pamięci podręcznej. `GetSyntaxTreeAsync()``SyntaxTree` zwraca obiekt. Problem polega na `async` tym, że jeśli masz funkcję typu `Task<SyntaxTree>`i zwracasz wartość typu `SyntaxTree`, kompilator emituje kod w celu przydzielenia zadania do przechowywania wyniku (przy użyciu `Task<SyntaxTree>.FromResult()`). Zadanie jest oznaczane jako ukończone, a wynik jest natychmiast dostępny. W kodzie dla nowych kompilatorów obiekty, które <xref:System.Threading.Tasks.Task> zostały już wykonane, były tak często, że te przydziały znacznie poprawiają czas odpowiedzi. 
  
 **Poprawka na przykład 6**  
  
 Aby usunąć kompletną <xref:System.Threading.Tasks.Task> alokację, można buforować obiekt zadania z wynikiem ukończenia:  
  
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
  
 Ten kod zmienia `cachedResult` typ do `Task<SyntaxTree>` i `async` korzysta z funkcji pomocnika, która zawiera oryginalny kod z `GetSyntaxTreeAsync()`. `GetSyntaxTreeAsync()`teraz używa [operatora łączenia wartości null](../../csharp/language-reference/operators/null-coalescing-operator.md) do zwrócenia `cachedResult` , jeśli nie ma wartości null. Jeśli `cachedResult` ma wartość null `GetSyntaxTreeAsync()` , wywołuje `GetSyntaxTreeUncachedAsync()` i buforuje wynik. Zwróć uwagę `GetSyntaxTreeAsync()` , że nie oczekujemy `GetSyntaxTreeUncachedAsync()` , że wywołanie jako kod normalnie będzie się powtarzać. Nie przy użyciu oczekiwania oznacza, `GetSyntaxTreeUncachedAsync()` że gdy <xref:System.Threading.Tasks.Task> zwraca swój `GetSyntaxTreeAsync()` <xref:System.Threading.Tasks.Task>obiekt, natychmiast zwraca. Teraz buforowany wynik to a <xref:System.Threading.Tasks.Task>, więc nie ma żadnych alokacji, aby zwrócić zbuforowany wynik. 
  
### <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Poniżej przedstawiono kilka dodatkowych kwestii dotyczących potencjalnych problemów z dużymi aplikacjami lub aplikacjami, które przetwarzają wiele danych. 
  
 **Słownik**  
  
 Słowniki są powszechnie używane w wielu programach, a słowniki są bardzo wygodne i najbardziej wydajne. Jednak są one często używane w sposób niewłaściwy. W programie Visual Studio i w nowych kompilatorach analiza pokazuje, że wiele słowników zawiera pojedynczy element lub był pusty. Pusta <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pól i zajmuje 48 bajtów na stercie na komputerze z procesorem x86. Słowniki są doskonałe, gdy potrzebne jest mapowanie lub kojarzenie struktury danych z wyszukiwaniem w czasie stałym. Niemniej jednak, jeśli masz tylko kilka elementów, możesz użyć słownika. Zamiast tego można na przykład zajrzeć przez `List<KeyValuePair\<K,V>>`, tak jak szybko. Jeśli używasz słownika tylko do ładowania danych z danymi, a następnie od niego odczytasz (bardzo powszechny wzorzec), za pomocą posortowanej tablicy z wyszukiwaniem N (log (N)) może być niemal równie szybka, w zależności od liczby używanych elementów. 
  
 **Klasy a struktury**  
  
 W ten sposób klasy i struktury zapewniają klasyczną przestrzeń czasową/kompromis do dostrajania aplikacji. Klasy składają się z 12 bajtów na komputerze z procesorem x86, nawet jeśli nie mają żadnych pól, ale są niedrogi do obejścia, ponieważ przyjmuje tylko wskaźnik odwołujący się do wystąpienia klasy. Struktury nie ponoszą żadnych alokacji sterty, jeśli nie są opakowane, ale w przypadku przekazywania dużych struktur jako argumentów funkcji lub wartości zwracanych przez procesor czas procesora w celu niepodzielnego kopiowania wszystkich elementów członkowskich danych struktur. Obejrzyj powtarzające się wywołania właściwości, które zwracają struktury, i Buforuj wartość właściwości w zmiennej lokalnej, aby uniknąć nadmiernego kopiowania danych. 
  
 **Pamięci podręcznych**  
  
 Częstą lewę z wydajnością jest buforowanie wyników. Jednak pamięć podręczna bez zasad limitu rozmiaru lub usuwania może być przeciekiem pamięci. W przypadku przetwarzania dużych ilości danych, jeśli w pamięci podręcznej znajduje się dużo pamięci, można spowodować wyrzucanie elementów bezużytecznych w celu zastąpienia korzyści z buforowanych wyszukiwań. 
  
 W tym artykule omówiono, jak należy wiedzieć, jak należy pamiętać o problemach z wąskim gardła wydajności, które mogą wpływać na czas odpowiedzi aplikacji, szczególnie w przypadku dużych systemów i systemów, które przetwarzają duże ilości danych. Typowe culprits obejmują pakowanie, manipulowanie ciągami, LINQ i lambda, buforowanie w metodach asynchronicznych, buforowanie bez limitu rozmiaru lub zasad usuwania, nieodpowiednie użycie słowników i przekazywanie wokół struktur. Weź pod uwagę cztery fakty dotyczące dostrajania aplikacji:  
  
- Nie przeprowadzaj przedwcześnie optymalizacji — Zwiększ produktywność i Dostosuj swoją aplikację w przypadku problemów. 
  
- Profile nie znajdują się — nastąpi odpuszczenie, że nie są mierzone pomiary. 
  
- Dobre narzędzia sprawiają, że wszystkie różnice — Pobieranie narzędzia PerfView i wypróbowanie. 
  
- Wszystkie przydziały — w przypadku, gdy zespół platform kompilator poświęca większość czasu na zwiększenie wydajności nowych kompilatorów. 
  
## <a name="see-also"></a>Zobacz także

- [Wideo przedstawiające prezentację tego tematu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Profilowanie wydajności — przewodnik dla początkujących](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Wydajność](index.md)
- [Porady dotyczące wydajności .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))
- [Samouczki narzędzia PerfView kanału 9](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [Zestaw SDK .NET Compiler Platform](../../csharp/roslyn-sdk/index.md)
- [repozytorium dotnet/Roslyn w witrynie GitHub](https://github.com/dotnet/roslyn)
