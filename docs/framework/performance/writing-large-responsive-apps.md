---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c2620913aff2ef2934e7c07574c130923c7139
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540666"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych aplikacji .NET Framework lub aplikacje, które przetwarzają dużą ilość danych, takie jak pliki lub bazy danych. Te wskazówki pochodzą ponowne napisanie kompilatory C# i Visual Basic w kodzie zarządzanym, a w tym artykule przedstawiono kilka przykładów rzeczywistych z kompilatorem C#. 
  
 Program .NET Framework jest wysoce wydajna, do tworzenia aplikacji. Zaawansowane i bezpieczne, a bogaty zbiór bibliotek należy wysoce rozwijającemu tworzenia aplikacji. Jednak doskonałym produktywne pochodzi odpowiedzialności. Powinny korzystaj z możliwości programu .NET Framework, ale należy przygotować do dostrajania wydajności kodu, gdy potrzebne. 
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Dlaczego nowe wydajne kompilatora ma zastosowanie do aplikacji  
 Zespół platformy kompilatora .NET ("Roslyn") rewrote języka C# i Kompilatory języka Visual Basic w zarządzany kod, aby podać nowe interfejsy API do modelowania i analizowanie kodu, narzędzia do tworzenia i włączania znacznie bardziej rozbudowane, kod środowiska w programie Visual Studio. Ponowne napisanie kompilatorów i programu Visual Studio do tworzenia środowiska na nowych kompilatory ujawniło szczegółowe informacje o wydajności przydatne, które mają zastosowanie do wszystkich dużych aplikacji .NET Framework lub dowolną aplikację, która przetwarza dużą ilość danych. Nie musisz wiedzieć o kompilatory, aby móc korzystać z szczegółowych informacji i przykłady z kompilatorem C#. 
  
 Visual Studio używa kompilatora interfejsów API do tworzenia wszystkie funkcje IntelliSense, które lubią użytkowników, takie jak zygzaki kolorowanie identyfikatorów i słów kluczowych, uzupełniania składni, błędy, parametr porad, problemów z kodem, i działania kodu. Program Visual Studio zapewnia tę pomoc podczas deweloperów są wpisywania i zmienianie ich kod i programu Visual Studio musi nadal odpowiadać, gdy kompilator stale modeluje kod, który deweloperzy edycji. 
  
 Gdy użytkownikom końcowym interakcję z aplikacją, ich powinien odpowiadać. Wpisywanie lub obsługi polecenia nigdy nie powinien być blokowany. Pomoc powinny się pojawiać, szybko lub zrezygnować, jeśli użytkownik nadal, wpisując. Aplikację należy unikać blokowania wątku interfejsu użytkownika z długich obliczeń, które aplikacji wydawać się wolne. 
  
 Aby uzyskać więcej informacji na temat kompilatory Roslyn zobacz [zestawu SDK platformy kompilatora .NET](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Po prostu fakty  
 Należy wziąć pod uwagę następujące fakty podczas dostosowywania wydajności i tworzenie szybko reagujących aplikacji .NET Framework. 
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Przedwczesne nie Optymalizuj  
 Pisanie kodu, który jest bardziej złożona, nie musi to być naliczane konserwacji, debugowania i wygładzanie kosztów. Doświadczeni programiści mają opanujesz intuicyjny sposób rozwiązywania problemów kodowania i napisać kod, bardziej wydajne. Jednak mogą czasami przedwcześnie optymalizacji ich kodu. Na przykład używają tabeli mieszania podczas prostej tablicy może wystarczyć lub używanie buforowania skomplikowane, że dochodzi do wycieku pamięci, a nie po prostu ponowne obliczanie wartości. Nawet jeśli jesteś programistą środowisko, możesz testowanie wydajności i Analizuj swój kod, gdy znajdziesz problemy. 
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Jeśli użytkownik nie notuje, jesteś zgadywania  
 Profile i pomiarów nie znajdować się. Profile dowiesz się, czy Procesor jest w pełni załadowane lub tego, czy w przypadku zablokowania na We/Wy dysku. Profile wyświetla komunikat informujący o tym, jakiego rodzaju i jak ilość pamięci alokowaniu i czy your CPU zużywa dużo czasu w [wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md) (GC). 
  
 Należy ustawić środowiska lub scenariuszy celami wydajności dla klientów w aplikacji i pisania testów do pomiaru wydajności. Badanie niepowodzenie testów, stosując metodę wykładniczej: aby ułatwiają, hipotezę, co może być problem, użyj profilów i testowanie Twojej hipotezę z eksperymentu lub zmiany kodu. Wraz z upływem czasu z regularnych testowania, należy ustanowić pomiarów wydajności bazowego, dzięki czemu można izolować zmiany, które powodują regresji wydajności. Zbliża się wydajność pracy, w sposób rygorystyczne, będzie uniknąć marnowania czasu za pomocą aktualizacji kodu, które nie są potrzebne. 
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Dobre narzędzia sprawiają, że wszystkie różnicy  
 Dobre narzędzia pozwalają szybko przejść do szczegółów największych problemów z wydajnością (procesor CPU, pamięć lub dysk) i pomoc, możesz znaleźć kod, który powoduje, że te wąskich gardeł. Microsoft dostarczany szeroką gamą narzędzi wydajności, takich jak [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [narzędzie do analizy Windows Phone](https://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), i [narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567). 
  
 Narzędzia PerfView jest bezpłatne i niezwykle wydajne narzędzia, która pozwala skupić się na szczegółowe zagadnienia, takie jak We/Wy dysku, zdarzenia odzyskiwania pamięci i pamięci. Można przechwycić związane z wydajnością [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) zdarzeń (ETW) i widok prosty sposób na aplikację, na proces, na stosie i na informacje o wątku. Narzędzia PerfView pokazuje, ile i jakiego rodzaju pamięci są przydzielane aplikację, i które funkcji lub wywołanie stosów Współtworzenie ile alokacji pamięci. Aby uzyskać więcej informacji, zobacz zaawansowane tematy pomocy, pokazy i filmy wideo, włączone za pomocą narzędzia (takie jak [samouczki narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) w witrynie Channel 9). 
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Przede wszystkim chodzi o alokacji  
 Może się wydawać, że tworzenie szybko reagujących aplikacji .NET Framework to przede wszystkim algorytmy, takie jak za pomocą szybkiego sortowania zamiast sortowania bąbelków, ale nie jest to wymagane. Największe czynnikiem tworzenia szybko reagujących aplikacji jest alokacji pamięci, szczególnie w przypadku, gdy Twoja aplikacja jest bardzo duża lub przetwarza duże ilości danych. 
  
 Prawie wszystko, co środowisk pracy, aby tworzyć odpowiednie środowisko IDE, za pomocą kompilatora nowe interfejsy API związane z unikanie alokacji i zarządzanie nimi strategii buforowania. Ślady narzędzia PerfView Pokaż wydajność nowych Kompilatory języka C# i Visual Basic jest rzadko powiązana procesora CPU. Kompilatory mogą być operacji We/Wy powiązany podczas odczytywania setki tysięcy lub milionów wierszy kodu, podczas odczytywania metadanych, lub emitowania wygenerowanego kodu. Opóźnienia wątku interfejsu użytkownika są prawie wszystkich z powodu wyrzucania elementów bezużytecznych. .NET Framework GC jest ona dostrojona o wysokiej wydajności i wykonuje znaczną część swojej pracy, jednocześnie, gdy kod aplikacji jest wykonywany. Jednak możesz wyzwolić kosztowne pojedynczą alokację [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekcji, zatrzymanie wszystkich wątków. 
  
## <a name="common-allocations-and-examples"></a>Typowe alokacji i przykłady  
 Przykładowe wyrażenia w tej sekcji zostały ukryte alokacje są niewielkie. Jednak w przypadku dużych aplikacji wykonuje wyrażeń kilka razy, mogą oni powoduje, że kilkuset megabajtów, nawet gigabajtów alokacji. Na przykład co minutę testów, które symulowane dewelopera wpisywania w edytorze gigabajtów pamięci przydzielonych i prowadzone zespołu wydajności, aby skoncentrować się na wpisywanie scenariuszy. 
  
### <a name="boxing"></a>Boxing  
 [Konwersja boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy wartość typy, które zwykle na żywo na stosie lub dane struktury są zapakowane w obiekt. Oznacza to przydzielić obiektu w celu przechowywania danych, a następnie zwraca wskaźnik do obiektu. .NET Framework czasami pola wartości, ponieważ podpis metody lub typu lokalizacji magazynu. Zawijanie typu wartości w alokacji pamięci powoduje, że obiekt. Wiele operacji pakowania może współtworzyć zawartość w megabajtach lub gigabajtach alokacji do swojej aplikacji, co oznacza, że aplikacji spowoduje, że więcej wykazów globalnych. .NET Framework i Kompilatory języka uniknąć pakowania, gdy jest to możliwe, ale czasami występuje, jeśli co najmniej oczekuje. 
  
 Aby zobaczyć pakowania w PerfView, otwórz śledzenia i przyjrzyj się stosy alokacji sterty GC w swojej aplikacji, nazwa procesu (Pamiętaj, że narzędzia PerfView raport dotyczący wszystkich procesów). Jeśli widzisz typów, takich jak <xref:System.Int32?displayProperty=nameWithType> i <xref:System.Char?displayProperty=nameWithType> w ramach przydziałów, czy konwersja boxing typów wartości. Wybranie jednego z następujących typów zostaną wyświetlone stosy i funkcje, w których są ramce. 
  
 **Przykład 1: ciąg metody i wartości argumentów typu**  
  
 Ten przykładowy kod przedstawia potencjalnie niepotrzebnych i nadmierne opakowania:  
  
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
  
 Ten kod zawiera funkcje rejestrowania, dzięki czemu aplikacja może wywołać `Log` często może działać milionów razy. Problem jest wywołanie `string.Format` jest rozpoznawana jako <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> przeciążenia. 
  
 To przeciążenie wymaga programu .NET Framework do pola `int` wartości na obiekty w celu przekazania ich wywołanie tej metody. Częściowe obejście polega na wywołanie `id.ToString()` i `size.ToString()` i Przekaż wszystkie ciągi, (które są obiektami) do `string.Format` wywołania. Wywoływanie `ToString()` przydzielić ciągu, jednak, że alokacji zostanie obsłużony mimo to w `string.Format`. 
  
 Należy rozważyć oznacza w tym podstawowe wywołanie `string.Format` jest po prostu ciągów, dzięki czemu może napisać ten kod:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Jednak ten wiersz kodu wprowadza alokacji pakowanie, ponieważ kompiluje, aby <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>. .NET Framework należy polu znak literału do wywołania `Concat`  
  
 **Na przykład rozwiązać 1**  
  
 Pełne poprawka jest proste. Wystarczy zastąpić literał znakowy z ciągiem literału, którą jest naliczana nie pakowanie, ponieważ ciągi są już obiektami:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Przykład 2: wyliczenia pakowania**  
  
 W tym przykładzie była odpowiedzialna za ogromna ilość alokacji w nowych Kompilatory języka C# i Visual Basic z powodu często są używane typy wyliczeniowe, szczególnie w przypadku operacji wyszukiwania w słowniku. 
  
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
  
 Ten problem jest bardzo subtelne. Narzędzia PerfView będzie Zgłoś to jako <xref:System.Enum.GetHashCode> pakowanie, ponieważ metody pól bazowego reprezentacja na typ wyliczenia ze względów implementacji. Jeśli wygląda ściśle znajduje się w PerfView, może zostać wyświetlony dwóch alokacje pakowania dla każdego wywołania <xref:System.Enum.GetHashCode>. Kompilator powoduje wstawienie jednego, a .NET Framework drugiego. 
  
 **Na przykład rozwiązać 2**  
  
 Łatwo można uniknąć zarówno alokacje przez rzutowanie do podstawowej reprezentacji przed wywołaniem <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Jest innym źródłem wspólnej pakowania na typy wyliczeniowe <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metody. Argumentu przekazanego do <xref:System.Enum.HasFlag%28System.Enum%29> musi zostać opakowany. W większości przypadków zastępowania wywołań do <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> bitowe testu jest prostszy i zwolnić alokacji. 
  
 Pamiętać pierwszy fakt wydajności (czyli nie przedwcześnie Optymalizacja) i nie należy uruchamiać ponowne napisanie kodu w ten sposób. Należy pamiętać o tych kosztów pakowania, ale tylko po profilowania aplikacji i znajdowanie punktów aktywnych zmian w kodzie. 
  
### <a name="strings"></a>Ciągi  
 Działań na ciągach są niektóre z największych sprawcami dla alokacji i są one często wyświetlane w PerfView w alokacjach pięć. Programy używać parametrów dla serializacji JSON i interfejsów API REST. Ciągi jako programowe stałe służy do współpracy z systemami, gdy nie można używać typów wyliczeń. Gdy usługi profilowania wskazuje, czy ciągi są wysoce wpływających na wydajność, poszukaj wywołania <xref:System.String> metody takie jak <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>i tak dalej. Za pomocą <xref:System.Text.StringBuilder> Aby uniknąć kosztów tworzenie jednego ciągu z wielu fragmentów pomaga, ale nawet przydzielanie <xref:System.Text.StringBuilder> obiektu może stać się wąskim gardłem, potrzebne do zarządzania. 
  
 **Przykład 3: operacje na ciągach**  
  
 Kompilator języka C# nie ten kod, który zapisuje tekst sformatowany komentarza dokumentacji XML:  
  
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
  
 Aby zobaczyć, że ten kod wykonuje wiele manipulowanie ciągami. Kod używa metody biblioteki do podziału wierszy w oddzielnych ciągi, można przycięcia biały znak, aby sprawdzić, czy argument `text` jest komentarz dokumentacji XML i wyodrębnianie podciągów z wierszy. 
  
 W pierwszym wierszu wewnątrz `WriteFormattedDocComment`, `text.Split` wywołanie za każdym razem, gdy jest on nazywany przydziela nowe trzy elementowej tablicy jako argument. Kompilator musi emitują kod, aby przydzielić każdorazowo tej tablicy. To, ponieważ kompilator nie wie, jeśli <xref:System.String.Split%2A> przechowuje tablicy gdzieś gdzie tablicy mogą zostać zmodyfikowane przez inny kod, który będzie wpływać na nowsze wywołania `WriteFormattedDocComment`. Wywołanie <xref:System.String.Split%2A> również przydziela ciąg dla każdego wiersza w `text` i przydziela innej pamięci do wykonania tej operacji. 
  
 `WriteFormattedDocComment` ma trzy wywołania <xref:System.String.TrimStart%2A> metody. Dwa znajdują się w wewnętrznej pętli, które zduplikowane pracy i przydziałów. Zapewnienie liczy co gorsza, wywołanie <xref:System.String.TrimStart%2A> metody bez argumentów przydziela pusta tablica (dla `params` parametr) oprócz wynikowy ciąg. 
  
 Ponadto występuje po wywołaniu <xref:System.String.Substring%2A> metody, która zwykle przydziela nowy ciąg. 
  
 **Na przykład rozwiązać 3**  
  
 W przeciwieństwie do wcześniejszych przykładach drobnych modyfikacji nie może rozwiązać tych przydziałów. Musisz cofnijmy, Przyjrzyj się problem i podejście do inaczej. Na przykład, można zauważyć, że argument `WriteFormattedDocComment()` jest ciągiem, który zawiera wszystkie informacje, które wymaga metody, dzięki czemu kod może zrobić więcej indeksowania, zamiast przydzielać wiele ciągi częściowe. 
  
 Kompilator wydajności zespołu rozwiązywane tych przydziałów za pomocą kodu w następujący sposób:  
  
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
  
 Pierwsza wersja `WriteFormattedDocComment()` przydzielone tablicę, kilku podciągów i podciągu przycięcia wraz z pustą `params` tablicy. Również sprawdzane dla "/ / /". Poprawiony kod wykorzystuje tylko indeksowania i przydziela nothing. Znajduje pierwszy znak, który nie jest biały znak, a następnie sprawdza, czy znak po znaku aby zobaczyć, czy ciąg rozpoczyna się od "/ / /". Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` zamiast <xref:System.String.TrimStart%2A> do zwrócenia pierwszego indeksu (po wskaźniku początkową), w którym występuje znak inny niż biały. Poprawka nie została ukończona, ale możesz dowiedzieć się, jak można zastosować poprawki podobne pełne rozwiązanie. Dzięki zastosowaniu tej metody w całym kodzie, można usunąć wszystkie alokacje w `WriteFormattedDocComment()`. 
  
 **Przykład 4: StringBuilder**  
  
 W tym przykładzie użyto <xref:System.Text.StringBuilder> obiektu. Poniższa funkcja generuje Pełna nazwa typu dla typów ogólnych:  
  
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
  
 Fokus znajduje się w wierszu, który tworzy nową <xref:System.Text.StringBuilder> wystąpienia. Kod powoduje, że przydział `sb.ToString()` i wewnętrzne alokacje w ramach <xref:System.Text.StringBuilder> implementacji, ale nie można kontrolować te alokacji, jeśli chcesz, aby wynikowy ciąg. 
  
 **Na przykład rozwiązać 4**  
  
 Aby naprawić `StringBuilder` obiekt alokacji; obiektu w pamięci podręcznej. Buforowanie nawet pojedyncze wystąpienie, które mogą uzyskać wyrzucać może znacznie poprawić wydajność. Jest to funkcja nową metodę implementacji, pomijając cały kod, z wyjątkiem nowej linii imię i nazwisko:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Kluczowe elementy są nowe `AcquireBuilder()` i `GetStringAndReleaseBuilder()` funkcje:  
  
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
  
 Ponieważ kompilatory nowe korzystają z wątków, tych implementacji użyć pola statyczne wątku (<xref:System.ThreadStaticAttribute> atrybutu) do pamięci podręcznej <xref:System.Text.StringBuilder>, i prawdopodobnie można uniknąć `ThreadStatic` deklaracji. Pola statyczne wątku przechowuje unikatową wartość dla każdego wątku, który jest wykonywany ten kod. 
  
 `AcquireBuilder()` Zwraca buforowane <xref:System.Text.StringBuilder> wystąpienia, jeśli istnieje, po ich czyszczenie i ustawienie pola lub pamięci podręcznej na wartość null. W przeciwnym razie `AcquireBuilder()` tworzy nowe wystąpienie i zwraca go, pozostawiając pole lub pamięci podręcznej zestawu o wartości null. 
  
 Gdy ukończysz pracę z <xref:System.Text.StringBuilder> , należy wywołać `GetStringAndReleaseBuilder()` można pobrać wynik ciągu, Zapisz <xref:System.Text.StringBuilder> wystąpienia w polu lub pamięci podręcznej, a następnie zwraca wynik. Jest możliwe do wykonania, ponownie wprowadź ten kod i utworzyć wiele <xref:System.Text.StringBuilder> obiektów (chociaż, rzadko wykonywane). Zapisuje kodu tylko ostatnia wydana <xref:System.Text.StringBuilder> wystąpienia do późniejszego użycia. Ten prosty strategii buforowania znacząco zmniejszyć alokacji w nowych kompilatory. Części środowiska .NET Framework i programu MSBuild ("MSBuild") użyć podobne techniki, aby zwiększyć wydajność. 
  
 Ten prosty strategii buforowania działa zgodnie z projektu dobre pamięci podręcznej, ponieważ ma ona limit rozmiaru. Istnieje jednak więcej kodu teraz niż w oryginalnym, co oznacza więcej kosztów konserwacji. Należy przyjąć strategii buforowania, tylko wtedy, gdy wykryto problemy z wydajnością, narzędzia PerfView wykazało, że <xref:System.Text.StringBuilder> są znaczące współautora. 
  
### <a name="linq-and-lambdas"></a>LINQ i wyrażeń lambda  
Language-Integrated Query (LINQ), w połączeniu z wyrażenia lambda jest przykładem funkcji produktywności. Jednak jego użycia może mieć znaczący wpływ na wydajność wraz z upływem czasu i może się okazać, że trzeba poprawić kod.
  
 **Przykład 5: Wyrażenia lambda, lista\<T >, a IEnumerable\<T >**  
  
 W tym przykładzie użyto [LINQ i funkcjonalności stylu kodu](https://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) można znaleźć symbolu w modelu kompilatora podany ciąg nazwy:  
  
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
  
 Nowy kompilator i środowisk IDE zbudowane na nim wywołania `FindMatchingSymbol()` bardzo często i są kilka ukryte alokacji w tej funkcji nawet jednego wiersza kodu. Aby zbadać te przydziały, najpierw podzielić funkcji nawet jednego wiersza kodu dwa wiersze:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 W pierwszym wierszu [wyrażenia lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [zamyka za pośrednictwem](https://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) zmienna lokalna `name`. Oznacza to, że oprócz przydzielanie obiektu dla [delegować](~/docs/csharp/language-reference/keywords/delegate.md) , `predicate` przechowuje, kod przydziela klasy statycznej, aby pomieścić środowisko, które przechwytuje wartość `name`. Kompilator generuje kod, jak pokazano poniżej:  
  
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
  
 Dwa `new` alokacje (jeden dla klasy środowiska) i jeden dla delegata jawne są teraz. 
  
 Teraz sprawdźmy wywołanie `FirstOrDefault`. Ta metoda rozszerzenia na <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu jest zbyt naliczana alokacji. Ponieważ `FirstOrDefault` przyjmuje <xref:System.Collections.Generic.IEnumerable%601> obiektu jako pierwszego argumentu, można rozwinąć wywołanie następujący kod (uproszczony nieco dla dyskusji):  
  
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
  
 `symbols` Zmienna ma typ <xref:System.Collections.Generic.List%601>. <xref:System.Collections.Generic.List%601> Kolekcji typ implementuje <xref:System.Collections.Generic.IEnumerable%601> i sprytnie definiuje moduł wyliczający (<xref:System.Collections.Generic.IEnumerator%601> interfejsu) który <xref:System.Collections.Generic.List%601> implementuje z `struct`. Przy użyciu struktury zamiast klasy oznacza, że zwykle należy unikać Alokacje sterty, które z kolei może mieć wpływ na wydajność odzyskiwania pamięci zbierania danych. Moduły wyliczające są zwykle używane w języku `foreach` pętli, która używa struktury modułu wyliczającego, ponieważ jest on zwracany w stosie wywołań. Zwiększanie wskaźnika stosu wywołań, aby zwolnić miejsce dla obiektu nie wpływa na tak jak w alokacji sterty GC. 
  
 W przypadku rozwiniętym okienku `FirstOrDefault` wywołaniu, kod musi wywołać `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>. Przypisywanie `symbols` do `enumerable` zmiennej typu `IEnumerable<Symbol>` utraci informacje faktyczny obiekt <xref:System.Collections.Generic.List%601>. Oznacza to, że gdy kod pobiera moduł wyliczający z `enumerable.GetEnumerator()`, ma pola zwróconej struktury, aby przypisać je do programu .NET Framework `enumerator` zmiennej. 
  
 **Na przykład rozwiązać 5**  
  
 Obejście polega na edycji `FindMatchingSymbol` następująco, zastępując sześć wierszy kodu, które są nadal zwięzły, łatwe do odczytania i zinterpretowania i łatwa w obsłudze jego nawet jednego wiersza kodu:  
  
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
  
 Ten kod nie korzysta z metod rozszerzeń LINQ, wyrażenia lambda lub moduły wyliczające i wiąże się nie alokacji. Istnieją nie alokacji, ponieważ kompilator może być wyświetlana `symbols` kolekcja jest <xref:System.Collections.Generic.List%601> i może powiązać wynikowy modułu wyliczającego (struktury) do zmiennej lokalnej przy użyciu właściwego typu, aby uniknąć pakowania. Oryginalna wersja tej funkcji został świetny przykład wszechstronnym możliwościom języka C# i efektywność programu .NET Framework. Ta wersja nowe i bardziej wydajne zachowuje tych klas bez dodawania żadnych złożonego kodu do konserwowania. 
  
### <a name="async-method-caching"></a>Buforowanie metody asynchronicznej  

W kolejnym przykładzie pokazano powszechny problem podczas próby użycia pamięci podręcznej powoduje [async](../../csharp/programming-guide/concepts/async/index.md) metody.
  
 **Przykład 6: buforowanie w metodach asynchronicznych**  
  
 Funkcje środowiska IDE programu Visual Studio, zbudowany na nowej Kompilatory języka C# i Visual Basic często pobrać drzewa składni i kompilatorów zachować za pomocą async czyniąc programu Visual Studio dynamiczny. Poniżej przedstawiono pierwszą wersję kodu, który może zapisać, można pobrać drzewa składni:  
  
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
  
 Widać, że wywołanie `GetSyntaxTreeAsync()` tworzy `Parser`, analizuje kod, a następnie zwraca <xref:System.Threading.Tasks.Task> obiektu `Task<SyntaxTree>`. Przydzielanie jest kosztowne część `Parser` wystąpienie i analizy kodu. Funkcja zwraca <xref:System.Threading.Tasks.Task> tak, aby obiekty wywołujące mogą await pracy analizy i bezpłatnie przez wątek interfejsu użytkownika, aby reagować na dane wejściowe użytkownika. 
  
 Kilka funkcji programu Visual Studio może próbować uzyskać tym samym drzewie składni, dzięki czemu można napisać następujący kod do Zbuforuj wynik analizy, aby oszczędzić czas i alokacje. Jednak ten kod powoduje alokację:  
  
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
  
 Możesz zobaczyć, że nowy kod za pomocą pamięci podręcznej ma `SyntaxTree` pole o nazwie `cachedResult`. Gdy to pole ma wartość null, `GetSyntaxTreeAsync()` wykonuje pracę i zapisuje wynik w pamięci podręcznej. `GetSyntaxTreeAsync()` Zwraca `SyntaxTree` obiektu. Ten problem występuje wtedy, gdy masz `async` — funkcja typu `Task<SyntaxTree>`, i zwracanie wartości typu `SyntaxTree`, kompilator generuje kod do przydzielania zadań do przechowywania wyników (przy użyciu `Task<SyntaxTree>.FromResult()`). Zadanie jest oznaczone jako ukończone, a wynik jest natychmiast dostępna. W kodzie dla nowych kompilatorów <xref:System.Threading.Tasks.Task> obiektów, które już zakończono wystąpił tak często oznacza naprawiania tych przydziałów zwiększona szybkość reakcji znacznie. 
  
 **Na przykład rozwiązać 6**  
  
 Aby usunąć ukończoną <xref:System.Threading.Tasks.Task> alokacji, można buforować obiekt zadania z wynikiem zakończone:  
  
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
  
 Ten kod zmienia typ `cachedResult` do `Task<SyntaxTree>` i stosuje `async` funkcja pomocnicza, która zawiera oryginalny kod z `GetSyntaxTreeAsync()`. `GetSyntaxTreeAsync()` używa teraz [null operatora łączącego](../../csharp/language-reference/operators/null-coalescing-operator.md) do zwrócenia `cachedResult` Jeśli nie ma wartości null. Jeśli `cachedResult` ma wartość null, następnie `GetSyntaxTreeAsync()` wywołania `GetSyntaxTreeUncachedAsync()` i zapisuje wynik w pamięci podręcznej. Należy zauważyć, że `GetSyntaxTreeAsync()` nie await wywołanie `GetSyntaxTreeUncachedAsync()` jako kod normalny. Nie używa await oznacza że w przypadku `GetSyntaxTreeUncachedAsync()` zwraca jego <xref:System.Threading.Tasks.Task> obiektu `GetSyntaxTreeAsync()` natychmiast zwraca <xref:System.Threading.Tasks.Task>. Teraz jest buforowany wynik <xref:System.Threading.Tasks.Task>, więc nie ma żadnych alokacji do zwrócenia wyniku pamięci podręcznej. 
  
### <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Poniżej przedstawiono kilka więcej punktów o potencjalnych problemach w dużych aplikacji lub aplikacji, które przetwarzają dużą ilość danych. 
  
 **słowniki**  
  
 Słowniki są używane w wielu programach w ubiquitously i mimo że słowniki są bardzo wygodny i wydajny założenia. Jednak często służą one niewłaściwie. W Visual Studio i nowe kompilatory analizy pokazuje, że wiele słowników zawiera pojedynczy element lub były puste. Pusta <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pola i zajmuje 48 bajtów na stosie na x86 maszyny. Słowniki to idealne rozwiązanie w przypadku, gdy będziesz potrzebować mapowanie lub asocjacyjnych struktury danych z wyszukiwanie w czasie stałym. Jednak jeśli masz tylko kilka elementów, możesz tracić dużo miejsca za pomocą słownika. Zamiast tego, na przykład, można wielokrotnie poszukać za pośrednictwem `List<KeyValuePair\<K,V>>`, po prostu tak szybko. Jeśli używasz słownik tylko do załadować je z danymi, a następnie zapoznaj się z niego (bardzo typowy wzorzec) posortowaną tablicę przy użyciu wyszukiwania N(log(N)) może być prawie jako szybkiego działania, w zależności od liczby elementów, których używasz. 
  
 **Klas lub struktur**  
  
 W sposób bezpieczny klas i struktur Obejmij kosztem klasycznego miejsca/godziny dostosowywania aplikacji. Klasy pociągnąć za sobą 12-bajtowy obciążenie x86 komputera, nawet jeśli mają one żadnych pól, ale są one niedrogie w celu przejścia wokół, ponieważ tylko pobiera wskaźnik do odwoływania się do wystąpienia klasy. Struktury pociągnąć za sobą nie alokacji sterty, jeśli nie są one zapakowany, ale podczas przekazywania dużych struktury jako argumenty funkcji lub zwracania wartości zajmuje trochę czasu procesora CPU niepodzielne skopiować wszystkie składowe danych struktury. Zwróć uwagę na wielokrotnego wywołania do właściwości, które zwracają struktur i wartości właściwości w zmiennej lokalnej, aby uniknąć nadmiernego kopiowania danych w pamięci podręcznej. 
  
 **Caches**  
  
 Typowe wydajności jest do wyników z pamięci podręcznej. Jednak bez zasad zakończenia lub usuwania rozmiar pamięci podręcznej może być przeciek pamięci. Podczas przetwarzania dużych ilości danych, jeśli przytrzymasz dużej ilości pamięci w pamięci podręcznej, można wywołać wyrzucanie elementów bezużytecznych zastąpić korzyści wynikające z Twojej wyszukiwań w pamięci podręcznej. 
  
 W tym artykule omówiono, jak należy pamiętać o objawy wąskich gardeł wydajności, które mogą wpływać na czas reakcji aplikacji, szczególnie w przypadku dużych systemów i systemów, które przetwarzają duże ilości danych. Typowe sprawcami obejmują pakowania, działań na ciągach, LINQ i lambda, buforowania w metodach asynchronicznych, buforowanie bez rozmiar limit lub usuwania zasad, nieodpowiednie użycie słowniki i przekazywanie wokół struktury. Należy pamiętać, cztery fakty dostrojenia aplikacji:  
  
-   Nie przedwcześnie Optymalizuj — produktywności i dostrajanie aplikacji, gdy zauważać problemy. 
  
-   Profile nie leży — jesteś zgadywania, jeśli nie pomiarowego. 
  
-   Dobre narzędzia zależy od — Pobierz narzędzia PerfView i wypróbuj jej działanie. 
  
-   To wszystko o alokacji — oznacza to, gdzie zespół platformy kompilatora poświęcony większość czasu poprawę wydajności nowych kompilatory. 
  
## <a name="see-also"></a>Zobacz także

- [Film wideo: prezentacja części tego tematu](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Profilowanie wydajności — przewodnik dla początkujących](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Wydajność](../../../docs/framework/performance/index.md)
- [Wskazówki dotyczące wydajności .NET](https://msdn.microsoft.com/library/ms973839.aspx)
- [Narzędzie do analizy wydajności Windows Phone](https://msdn.microsoft.com/magazine/hh781024.aspx)
- [Znajdź wąskie gardła za pomocą programu Visual Studio Profiler](https://msdn.microsoft.com/magazine/cc337887.aspx)
- [Channel 9 samouczki narzędzia PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [Zestaw SDK platformy kompilatora .NET](../../csharp/roslyn-sdk/index.md)
- [repozytorium DotNet/roslyn w witrynie GitHub](https://github.com/dotnet/roslyn)
