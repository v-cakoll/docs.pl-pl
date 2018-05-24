---
title: Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846d41c31687df98b019f103e42cf586a23d8ff1
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="writing-large-responsive-net-framework-apps"></a>Pisanie dużych i sprawnie działających aplikacji platformy .NET Framework
Ten artykuł zawiera wskazówki dotyczące poprawy wydajności dużych aplikacji .NET Framework lub aplikacje, które przetwarzają dużą ilość danych, takich jak pliki lub bazy danych. Te wskazówki pochodzi z ponowne zapisywanie C# i Visual Basic kompilatory w kodzie zarządzanym i ten artykuł zawiera kilka przykładów rzeczywistych kompilatora C#.  
  
 .NET Framework jest wydajne do tworzenia aplikacji.  Wydajne i bezpieczne i sformatowanego kolekcja bibliotek upewnij wysokiej owocnej Kompilowanie aplikacji.  Jednak z doskonałą wydajność jest dostarczany odpowiedzialności.  Należy wykorzystać wszystkie możliwości programu .NET Framework, ale można go przygotować do dopasowywania wydajności swój kod w razie potrzeby.  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Dlaczego nowe wydajności kompilatora ma zastosowanie do aplikacji  
 Zespół platformy kompilatora .NET ("Roslyn") rewrote C# i Kompilatory języka Visual Basic w zarządzany kod, aby podać nowe interfejsy API do modelowania i analizowanie kodu, narzędzia do tworzenia i włączania znacznie bardziej rozbudowane, obsługujący kod doświadczeń w programie Visual Studio.  Ponowne zapisywanie kompilatory i kompilowania programu Visual Studio doświadczeń w nowych kompilatory ujawniony szczegółowe informacje o wydajności przydatne mających zastosowanie do wszystkich dużych aplikacji .NET Framework lub dowolną aplikację, która przetwarza dużą ilość danych.  Nie trzeba wiedzieć o kompilatory przeprowadzać szczegółowe informacje i przykłady kompilatora C#.  
  
 Visual Studio będzie korzystać kompilatora interfejsów API do tworzenia wszystkie funkcje IntelliSense, które użytkownicy lubią, takie jak zygzaki kolorowania identyfikatorów i słów kluczowych, listy uzupełniania składni, błędów, parametr porady, problemy z kodem i działania kodu.  Visual Studio zapewnia tę pomoc podczas Deweloperzy są wpisując i zmiany ich kodu i Visual Studio musi pozostać odpowiadać podczas kompilator stale modele deweloperom edytowanie kodu.  
  
 Gdy użytkownikom końcowym interakcję z aplikacją, ich powinien odpowiadać.  Wpisywanie lub Obsługa polecenia nigdy nie powinien zostać zablokowany.  Pomoc powinna wyskakujące szybko lub zrezygnować, jeśli użytkownik nie zniknie, wpisując polecenie.  Aplikację należy unikać blokowania wątku interfejsu użytkownika o długie obliczeń zapewnić, że wolna aplikacji.  
  
 Aby uzyskać więcej informacji na temat kompilatory Roslyn, odwiedź stronę [dotnet/roslyn](https://github.com/dotnet/roslyn) repozytorium w witrynie GitHub.
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a>Po prostu faktów  
 Należy wziąć pod uwagę następujące fakty podczas dostrajania wydajności i tworzenia reakcji aplikacji .NET Framework.  
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fakt 1: Przedwcześnie nie optymalizacji.  
 Pisanie kodu, który jest bardziej złożone niż musi on być wiąże konserwacji, debugowanie i wygładzanie kosztów.  Doświadczeni programiści ma intuicyjne ujmij sposobu rozwiązywania problemów kodowania i większą wydajność w kodzie.  Jednak ich czasami przedwcześnie optymalizacji ich kodu.  Na przykład używa tablicy skrótów przy proste tablicy może wystarczyć lub Używaj buforowania skomplikowane, który dochodzi do wycieku pamięci zamiast po prostu recomputing wartości.  Nawet jeśli programista środowisko, należy testowanie wydajności i analizowania kodu w przypadku napotkania problemów.  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fakt 2: Jeśli nie notuje, użytkownik jest odgadnięcie  
 Profile i pomiarów nie znajdują się.  Profili wyświetlić czy Procesora jest w pełni załadowany lub czy jest zablokowany na We/Wy dysku.  Profile wyświetla komunikat informujący o tym, jakiego rodzaju i ilość pamięci w przypadku alokowania i czy ten Procesor zużywa dużo czasu, w [wyrzucanie elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md) (GC).  
  
 Należy ustawić cele dotyczące wydajności dla klucza klienta środowiska lub scenariuszy w aplikacji i napisać testy do pomiaru wydajności.  Zbadaj w przypadku braku testy, stosując metodę wykładniczej: Profile umożliwiają pomocne, można przyjąć hipotezę, co może być problem i przetestować użytkownika hipoteza z eksperyment lub zmiany kodu.  Ustanowić miary wydajności bazowej wraz z upływem czasu z testowaniem regularnie, więc można odizolować zmiany, które powodują regresji w wydajności.  W sposób rygorystyczne zbliża się wydajność pracy, będzie uniknąć traci czasu z aktualizacjami kodu, które nie są potrzebne.  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fakt 3: Dobrej narzędziom do wszystkich różnicy  
 Dobrym narzędzia pozwalają szybko przejść do szczegółów największych problemy z wydajnością (procesora CPU, pamięć lub dysk) i pomocy możesz znaleźć kod, który powoduje, że te wąskich gardeł.  Microsoft dostarczany różnych narzędzi wydajności, takich jak [programu Visual Studio profilera](/visualstudio/profiling/beginners-guide-to-performance-profiling), [narzędzie do analizy Windows Phone](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), i [narzędzia PerfView](http://www.microsoft.com/download/details.aspx?id=28567).  
  
 Narzędzia PerfView jest bezpłatny i zdumiewająco zaawansowane narzędzie, które pozwala skupić się na bezpośrednich problemów, takich jak We/Wy dysku, zdarzenia GC i pamięci.  Można przechwycić związanych z wydajnością [śledzenia zdarzeń dla systemu Windows](../../../docs/framework/wcf/samples/etw-tracing.md) zdarzeń (ETW) i widoku łatwo na aplikacji, na proces, na stosie i na informacje o wątku.  Narzędzia PerfView pokazuje, ile i jakie rodzaj pamięci są przydzielane aplikacji, które funkcje i wywołania stosy współtworzyć ile alokacji pamięci. Aby uzyskać więcej informacji, zobacz sformatowanego tematy pomocy, pokazy i filmy wideo uwzględnione za pomocą narzędzia (takie jak [samouczki narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial) witrynie Channel 9).  
  
### <a name="fact-4-its-all-about-allocations"></a>Fakt 4: Przede wszystkim chodzi o alokacji  
 Może się okazać, że tworzenie dynamiczne aplikacja .NET Framework jest wszystkie informacje dotyczące algorytmów, takich jak użycie szybkiego sortowania zamiast bąbelków sortowania, ale nie jest to.  Współczynnik największych z tworzeniem reakcji aplikacji jest przydzielenie pamięci, szczególnie w przypadku, gdy aplikacja jest bardzo duże lub przetwarzania dużych ilości danych.  
  
 Prawie wszystkie wykonywania pracy, aby utworzyć odpowiednie środowisko IDE przez kompilator nowych interfejsów API zaangażowane unikanie alokacji i zarządzanie strategii buforowania.  Ślady narzędzia PerfView pokazują, że wydajność nowej Kompilatory języka C# i Visual Basic rzadko jest powiązany procesora CPU.  Kompilatory może być we/wy powiązany podczas odczytywania setki tysięcy lub miliony wierszy kodu, odczytywanie metadanych, lub emitowanie wygenerowanego kodu.  Opóźnienia wątku interfejsu użytkownika są prawie wszystkie ze względu na wyrzucanie elementów bezużytecznych.  .NET Framework GC wysokiej dostosowana pod kątem wydajności i wykona większość pracy, jednocześnie, gdy kod aplikacji jest wykonywany.  Jednak pojedynczy alokacji może wyzwolić kosztowne [gen2](../../../docs/standard/garbage-collection/fundamentals.md) kolekcji zatrzymywanie wszystkie wątki.  
  
## <a name="common-allocations-and-examples"></a>Typowe przykłady i alokacji  
 Przykładowe wyrażenia w tej sekcji zostały ukryte przydziałów, które są niewielkie.  Jednak jeśli dużych aplikacji wykonuje wyrażeń razy, ich można przyczyny setki megabajtów, nawet gigabajtów alokacji.  Na przykład co minutę testy symulowane developer, wpisując w edytorze przydzielone gigabajtów pamięci, które doprowadziły zespołu wydajności skupić się na wpisanie scenariuszy.  
  
### <a name="boxing"></a>Boxing  
 [Konwersja boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) występuje, gdy wartość typy, które zwykle na żywo na stosie lub w danych struktury są pakowane w obiekcie.  Oznacza to przydzielić obiektu w celu przechowywania danych, a następnie zwraca wskaźnik do obiektu.  .NET Framework czasami pola wartości z powodu podpisu metody lub typu lokalizacji magazynu.  Zawijanie typu wartości w alokacji pamięci powoduje, że obiekt.  Wiele operacji opakowanie może przyczynić się w megabajtach lub gigabajtach alokacji do aplikacji, co oznacza, że więcej GC spowoduje, że aplikacja. .NET Framework i Kompilatory języka uniknąć pakującej, gdy jest to możliwe, ale czasami występuje, jeśli oczekujesz najmniej.  
  
 Aby wyświetlić opakowanie w narzędzia PerfView, otwórz śledzenia i przyjrzyj się stosy alokacji sterty GC pod nazwą procesu aplikacji (należy pamiętać, że narzędzia PerfView raporty dotyczące wszystkich procesów).  Jeśli widzisz wykresach <xref:System.Int32?displayProperty=nameWithType> i <xref:System.Char?displayProperty=nameWithType> w ramach przydziałów, są konwersja boxing typów wartości.  Wybranie jednej z tych typów zostaną wyświetlone stosy i funkcje, w których są ramce.  
  
 **Przykład 1: string, metody i wartości argumentów typu**  
  
 Ten przykładowy kod przedstawia potencjalnie niepotrzebnych i nadmierne opakowanie:  
  
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
  
 Ten kod zawiera funkcje rejestrowania, aplikacja może wywołać `Log` często, funkcja może być miliony razy.  Problem jest wywołanie `string.Format` jest rozpoznawana jako <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> przeciążenia.  
  
 To przeciążenie wymaga programu .NET Framework do pola `int` wartości do obiektów w celu przekazania ich wywołanie tej metody.  Częściowe poprawka jest wywołanie `id.ToString()` i `size.ToString()` i Przekaż wszystkie ciągi (które są obiektami) do `string.Format` wywołania.  Wywoływanie `ToString()` przydzielić ciągu, ale ten przydział nastąpi mimo to wewnątrz `string.Format`.  
  
 Należy rozważyć to tym podstawowe wywołanie `string.Format` jest po prostu ciągów, dlatego może być napisać ten kod:  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Jednak wiersza kodu wprowadzono alokacji pakującej, ponieważ kompiluje się do <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.  .NET Framework musi polu znak literału do wywołania `Concat`  
  
 **Na przykład rozwiązać 1**  
  
 Zakończenie poprawka jest proste.  Po prostu zastąpić literał znakowy z ciągiem literału, które generuje nie pakującej ponieważ ciągi są już obiekty:  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Przykład 2: opakowywanie wyliczenia**  
  
 W tym przykładzie jest odpowiedzialny za ogromnych ilości alokacji w nowych Kompilatory języka C# i Visual Basic z powodu częste używanie typów wyliczenia, szczególnie w słowniku operacji wyszukiwania.  
  
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
  
 Ten problem jest bardzo niewielkie.  Narzędzia PerfView rozpoczną przesyłanie raportów jako <xref:System.Enum.GetHashCode> konwersja boxing, ponieważ metoda pola źródłowego reprezentacja typu wyliczenia ze względów implementacji.  Jeśli narzędzia PerfView wyglądać ściśle, mogą pojawić się dwa pakującej alokacji dla każdego wywołania <xref:System.Enum.GetHashCode>.   Kompilator powoduje wstawienie jednego, a .NET Framework innych.  
  
 **Na przykład rozwiązać 2**  
  
 Łatwo można uniknąć zarówno alokacji przez rzutowanie do podstawowej reprezentacja przed wywołaniem <xref:System.Enum.GetHashCode>:  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Inny wspólne źródło pakującej na typy wyliczeniowe jest <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> metody.  Argument przekazany do <xref:System.Enum.HasFlag%28System.Enum%29> musi zostać opakowany.  W większości przypadków, zastępując wywołań <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> z bitowego testu jest prostsze i bez alokacji.  
  
 Pamiętać pierwszy fakt wydajności (to znaczy nie przedwcześnie Optymalizacja) i nie należy uruchamiać ponowne zapisanie całego kodu w ten sposób.    Należy pamiętać o tych kosztów pakującej, ale Zmień swój kod, tylko po profilowania aplikacji i znajdowanie punkty aktywne.  
  
### <a name="strings"></a>Ciągi  
 Na ciągach są niektóre z najważniejszych sprawcami dla alokacji i ich często wyświetlane w narzędzia PerfView w alokacjach 5.  Programy ciąg znaków używany do serializacji, JSON i interfejsów API REST.  Ciągi jako stałe programowe służącego do współpracy z systemów, gdy nie można użyć typów wyliczenia.  Gdy Twoje profilowania pokazuje, że ciągi wysokiej mają wpływ na wydajność, wyszukaj wywołań <xref:System.String> metod, takich jak <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>i tak dalej.  Przy użyciu <xref:System.Text.StringBuilder> Aby uniknąć kosztów Tworzenie ciągu z wielu części pomaga, ale nawet przydziału <xref:System.Text.StringBuilder> obiektu mogą stać się wąskiego gardła, które muszą zarządzać.  
  
 **Przykład 3: operacje na ciągach**  
  
 Kompilator języka C# nie ten kod, który zapisuje tekst sformatowany komentarz dokumentu XML:  
  
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
  
 Widać, że ten kod wykonuje wiele manipulowanie ciągami.  W kodzie użyto metody biblioteki podziału wierszy w oddzielnych ciągów, aby przyciąć biały znak, aby sprawdzić, czy argument `text` jest komentarz dokumentacji XML i wyodrębnić podciągów z wierszy.  
  
 W pierwszym wierszu wewnątrz `WriteFormattedDocComment`, `text.Split` wywołanie za każdym razem, gdy jest ona wywoływana przydziela nowej tablicy elementu trzech jako argument.  Kompilator ma Emituj kod, aby przydzielić tej tablicy zawsze.  Wynika to z faktu kompilator nie może ustalić, czy <xref:System.String.Split%2A> przechowuje tablicy miejsce gdzie tablicy mogą zostać zmodyfikowane innego kodu, co może wpływać na nowsze wywołania `WriteFormattedDocComment`.  Wywołanie <xref:System.String.Split%2A> również przydziela ciąg dla każdego wiersza w `text` i przydziela innych pamięci do wykonania tej operacji.  
  
 `WriteFormattedDocComment` ma trzy wywołania <xref:System.String.TrimStart%2A> metody.  Dwa znajdują się w wewnętrznej pętle, zawierające zduplikowane pracy i alokacji.  Aby co gorsza sprawach, wywoływania <xref:System.String.TrimStart%2A> metody bez argumentów przydziela pustą tablicę (dla `params` parametru) oprócz wynik ciągu.  
  
 Ponadto jest to wywołanie <xref:System.String.Substring%2A> metodę, która zwykle przydziela nowe parametry.  
  
 **Na przykład rozwiązać 3**  
  
 W przeciwieństwie do wcześniejszych przykłady małych zmiany nie można naprawić tych przydziałów.  Musisz kroku Wstecz, obejrzyj ten problem i zbliżających się inaczej.  Na przykład można zauważyć, że argument `WriteFormattedDocComment()` jest ciągiem, który ma wszystkie informacje o wymagające metody, więc kod może zrobić więcej indeksowania zamiast przydzielania wiele ciągi częściowe.  
  
 Zespół wydajności kompilatora rozwiązywane tych przydziałów z kodem następująco:  
  
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
  
 Pierwszą wersję `WriteFormattedDocComment()` przydzielone tablicy, kilku podciągów i przycięte podciąg wraz z pustą `params` tablicy.  On również sprawdzane pod kątem `"///"`.  Poprawione kod używa tylko indeksowanie i przydziela nothing.  Znajdzie pierwszego znaku, który nie jest biały znak, a następnie sprawdza znak po znaku, aby zobaczyć, czy ciąg rozpoczyna się od `"///"`.  Nowy kod używa `IndexOfFirstNonWhiteSpaceChar` zamiast <xref:System.String.TrimStart%2A> do zwracania indeks pierwszego (po indeks datą początkową), w których występuje znak odstępem.  Ta poprawka nie została ukończona, ale możesz dowiedzieć się, jak zastosować poprawki podobne do kompletnego rozwiązania.  Przy zastosowaniu tej metody w całym kodzie, należy usunąć wszystkie alokacji w `WriteFormattedDocComment()`.  
  
 **Przykład 4: StringBuilder**  
  
 W tym przykładzie użyto <xref:System.Text.StringBuilder> obiektu.  Następująca funkcja generuje Pełna nazwa typu dla typów ogólnych:  
  
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
  
 Koncentruje się na wiersz, który tworzy nową <xref:System.Text.StringBuilder> wystąpienia.  Kod powoduje, że przydział `sb.ToString()` i wewnętrznych alokacji w <xref:System.Text.StringBuilder> implementacji, ale nie może kontrolować te przydziały, jeśli wynik ciąg.  
  
 **Na przykład rozwiązać 4**  
  
 Aby naprawić `StringBuilder` obiekt alokacji, pamięci podręcznej obiektu.  Buforowanie nawet pojedyncze wystąpienie, które mogą uzyskać wyrzucać może znacząco zwiększyć wydajność.  Jest to funkcja nowej implementacji, pomijając cały kod z wyjątkiem nowych wierszy imię i nazwisko:  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Części klucza są nowe `AcquireBuilder()` i `GetStringAndReleaseBuilder()` funkcje:  
  
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
  
 Użyj pola statyczne dla wątku, nowe kompilatory używają wątków, tych implementacji (<xref:System.ThreadStaticAttribute> atrybut) do pamięci podręcznej <xref:System.Text.StringBuilder>, i prawdopodobnie można uniknąć `ThreadStatic` deklaracji.  Pole statyczne dla wątku zawiera unikatową wartość dla każdego wątku, który wykonuje ten kod.  
  
 `AcquireBuilder()` Zwraca buforowane <xref:System.Text.StringBuilder> wystąpienia, jeśli istnieje, po wyczyszczeniem i ustawienie pola lub pamięci podręcznej na wartość null.  W przeciwnym razie `AcquireBuilder()` tworzy nowe wystąpienie i zwraca go, pozostawiając pole lub pamięci podręcznej zestawu wartości null.  
  
 Po zakończeniu z <xref:System.Text.StringBuilder> , należy wywołać `GetStringAndReleaseBuilder()` można pobrać wyniku ciągu, Zapisz <xref:System.Text.StringBuilder> wystąpienia w polu lub pamięci podręcznej, a następnie zwracają wynik.  Istnieje możliwość wykonywania ponowne wprowadzenie tego kodu i utworzyć wiele <xref:System.Text.StringBuilder> obiektów (chociaż tak się rzadko stanie).  Zapisuje kod wydane tylko ostatnich <xref:System.Text.StringBuilder> wystąpienie do późniejszego użycia.  To proste strategii buforowania znacznie zmniejszyć alokacji w nowych kompilatory.  Części programu .NET Framework i program MSBuild ("MSBuild") użyć technika podobne do zwiększenia wydajności.  
  
 To proste strategii buforowania opiera się na dobrej pamięci podręcznej, ponieważ ma ona limit rozmiaru.  Istnieje jednak jeden kod teraz niż w oryginalnym, czyli więcej kosztów obsługi.  Powinna przyjąć strategii buforowania tylko wtedy, gdy uda Ci się znaleźć problemy z wydajnością i narzędzia PerfView wykazała, że <xref:System.Text.StringBuilder> są znaczące współautora.  
  
### <a name="linq-and-lambdas"></a>LINQ i wyrażeń lambda  
 Za pomocą wyrażeń język Language-Integrated zapytania (LINQ) i lambda jest doskonałym przykładem zastosowania produktywności funkcje, które mogą być później potrzebne do edycji, gdy kod stanie się znaczący wpływ na wydajność.  
  
 **Przykład 5: Wyrażeń lambda, lista\<T >, a IEnumerable\<T >**  
  
 W tym przykładzie użyto [LINQ i kodu stylu funkcjonalności](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) można znaleźć symbolu w modelu kompilatora podany ciąg nazwy:  
  
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
  
 Nowy kompilator i środowiska IDE oparty na jej wywołać `FindMatchingSymbol()` bardzo często i są kilka ukryte alokacji w tej funkcji w jednym wierszu kodu.  Badanie tych przydziałów, najpierw podzielić funkcji pojedynczy wiersz kodu na dwa wiersze:  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 W pierwszym wierszu [wyrażenia lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[zamyka za pośrednictwem](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) zmiennej lokalnej `name`.  Oznacza to, że oprócz przydziału dla obiekt [delegować](~/docs/csharp/language-reference/keywords/delegate.md) który `predicate` zawiera kod przydziela Klasa statyczna przechowująca środowiska, który przechwytuje wartość `name`.  Kompilator generuje kod podobne do poniższych:  
  
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
  
 Dwa `new` (jeden dla klasy środowiska) i drugi dla obiekt delegowany są jawne teraz.  
  
 Teraz wyglądać na wywołanie `FirstOrDefault`. Tę metodę rozszerzenie w <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu generuje zbyt alokacji.  Ponieważ `FirstOrDefault` przyjmuje <xref:System.Collections.Generic.IEnumerable%601> obiekt jako pierwszego argumentu, można rozszerzyć wywołanie następujący kod (uproszczony nieco omówienie):  
  
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
  
 `symbols` Zmienna ma typ <xref:System.Collections.Generic.List%601>.  <xref:System.Collections.Generic.List%601> Implementuje typ kolekcji <xref:System.Collections.Generic.IEnumerable%601> i sprytnie definiuje moduł wyliczający (<xref:System.Collections.Generic.IEnumerator%601> interfejsu) który <xref:System.Collections.Generic.List%601> implementuje z `struct`.  Za pomocą struktury zamiast klasy oznacza zwykle uniknąć Alokacje sterty, co z kolei może negatywnie wpłynąć na wydajność zbierania danych pamięci.  Moduły wyliczające są zazwyczaj używane w języku `foreach` pętli, który używa struktury modułu wyliczającego jest zwracany w stosie wywołań.  Zwiększanie wskaźnik stosu wywołań, aby zwolnić miejsce dla obiekt nie ma wpływu na tak jak w alokacji sterty GC.  
  
 W przypadku rozwinięte `FirstOrDefault` wywołanie, kod musi wywołać `GetEnumerator()` na <xref:System.Collections.Generic.IEnumerable%601>.  Przypisywanie `symbols` do `enumerable` zmiennej typu `IEnumerable<Symbol>` utraci informacje rzeczywistego obiektu <xref:System.Collections.Generic.List%601>.  Oznacza to, że jeśli kod pobiera moduł wyliczający z `enumerable.GetEnumerator()`, .NET Framework ma pole zwrócony struktury można przypisać go do `enumerator` zmiennej.  
  
 **Na przykład rozwiązać 5**  
  
 Rozwiązanie polega na edycji `FindMatchingSymbol` , zastępując jego pojedynczy wiersz kodu sześć wierszy kodu, które nadal zwięzła, łatwych do przeczytane i zrozumiane i łatwe w konserwacji:  
  
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
  
 Ten kod nie korzysta z metody rozszerzenia LINQ, wyrażenia lambda lub moduły wyliczające i wiąże się nie przydziału.  Ponieważ kompilator można stwierdzić, że istnieją nie przydziału `symbols` kolekcja jest <xref:System.Collections.Generic.List%601> i może powiązać wynikowy modułu wyliczającego (struktury) do zmiennej lokalnej z odpowiedniego typu, aby uniknąć boxing.  Oryginalną wersją z tej funkcji jest doskonałym przykładem wszechstronnym możliwościom języka C# i wydajności programu .NET Framework.  Ta wersja nowych i bardziej wydajnych zachowuje tych klas bez dodawania żadnych złożonego kodu do obsługi.  
  
### <a name="async-method-caching"></a>Buforowanie metody asynchronicznej  
 W kolejnym przykładzie pokazano to powszechny problem podczas próby użycia buforowane wyniki w [async](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) metody.  
  
 **Przykład 6: buforowanie w metodach asynchronicznych**  
  
 Funkcje programu Visual Studio IDE zbudowany na nowej Kompilatory języka C# i Visual Basic często pobrać drzewa składni i kompilatory umożliwia asynchroniczne czyniąc zachowanie reakcji programu Visual Studio.  Poniżej przedstawiono pierwszą wersję kodu, który może zapisać można pobrać drzewa składni:  
  
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
  
 Widać, że wywołania `GetSyntaxTreeAsync()` tworzy `Parser`, analizuje kod, a następnie zwraca <xref:System.Threading.Tasks.Task> obiektu `Task<SyntaxTree>`.  Przydzielanie jest kosztowne części `Parser` wystąpienia i analizy kodu.  Funkcja zwraca <xref:System.Threading.Tasks.Task> tak, aby obiekty wywołujące można oczekiwać podczas analizowania pracy oraz o wolnym wątku interfejsu użytkownika można odbierać dane wejściowe użytkownika.  
  
 Niektóre funkcje programu Visual Studio może podjąć próbę pobrania tym samym drzewie składni, więc mogą pisać następujący kod do pamięci podręcznej podczas analizowania wyników, aby zaoszczędzić czas i alokacji.  Jednak ten kod wiąże się z alokacji:  
  
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
  
 Zobacz, czy nowy kod z buforowaniem ma `SyntaxTree` pola o nazwie `cachedResult`.  Gdy to pole ma wartość null, `GetSyntaxTreeAsync()` wykonuje pracę i zapisuje go w pamięci podręcznej.  `GetSyntaxTreeAsync()` Zwraca `SyntaxTree` obiektu.  Problem występuje wtedy, gdy masz `async` — funkcja typu `Task<SyntaxTree>`, i zwracać wartość typu `SyntaxTree`, kompilator emituje kod, aby przydzielić zadania do przechowywania wynik (przy użyciu `Task<SyntaxTree>.FromResult()`).  Zadanie zostanie oznaczone jako wykonane, a wynik jest natychmiast dostępna.  W kodzie dla nowego kompilatorów <xref:System.Threading.Tasks.Task> obiektów, które zostały już wykonane wystąpił, dlatego często oznacza ustalające tych przydziałów poprawia czas odpowiedzi znacznie.  
  
 **Na przykład rozwiązać 6**  
  
 Aby usunąć ukończonej <xref:System.Threading.Tasks.Task> alokacji, może buforować obiekt zadania z wynikiem zakończone:  
  
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
  
 Ten kod zmienia typ `cachedResult` do `Task<SyntaxTree>` i wykorzystuje `async` funkcji Pomocnik, która przechowuje oryginalny kod z `GetSyntaxTreeAsync()`.  `GetSyntaxTreeAsync()` używa teraz [null operatora łączącego](../../csharp/language-reference/operators/null-coalescing-operator.md) do zwrócenia `cachedResult` Jeśli nie ma wartości null.  Jeśli `cachedResult` ma wartość null, następnie `GetSyntaxTreeAsync()` wywołania `GetSyntaxTreeUncachedAsync()` i buforuje wynik.  Zwróć uwagę, że `GetSyntaxTreeAsync()` nie await wywołanie `GetSyntaxTreeUncachedAsync()` jako kod normalnie.  Nie używa await oznacza że w przypadku `GetSyntaxTreeUncachedAsync()` zwraca jego <xref:System.Threading.Tasks.Task> obiektu `GetSyntaxTreeAsync()` natychmiast zwraca <xref:System.Threading.Tasks.Task>.  Teraz jest buforowanego zestawu wyników <xref:System.Threading.Tasks.Task>, więc nie nie przydziału do zwrócenia wyniku pamięci podręcznej.  
  
### <a name="additional-considerations"></a>Dodatkowe uwagi  
 Oto kilka punktów więcej o potencjalnych problemach w dużych aplikacji lub aplikacji, które przetwarzają dużą ilość danych.  
  
 **słowników**  
  
 Słowniki są używane ubiquitously w wielu programach i jednak słowniki są bardzo wygodny i z założenia wydajne.  Jednak są często używane niewłaściwie.  W Visual Studio i nowych kompilatory analizy wskazuje, że wiele słowników zawiera pojedynczy element lub były puste.  Pusta <xref:System.Collections.Generic.Dictionary%602> ma dziesięć pól i zajmuje 48 bajtów w stercie na x86 maszyny.  Słowniki są doskonałe gdy będziesz potrzebować mapowania lub asocjacyjnych struktury danych z stała czas wyszukiwania.  Jednak jeśli masz tylko kilka elementów można odpady dużo miejsca za pomocą słownika.  Zamiast tego, na przykład można wielokrotnie powtarzane dostępne za pośrednictwem `List<KeyValuePair\<K,V>>`, jak szybki.  Jeśli używasz słownik tylko do ładowania danych i następnie odczytanie z niego (bardzo typowy wzorzec) przy użyciu tablicy posortowane w usłudze wyszukiwania N(log(N)) może być niemal jako szybkiego, w zależności od liczby elementów, którego używasz.  
  
 **Klasy i struktury**  
  
 Klasy i struktury w sposób, podaj zależnościami klasycznego miejsca i godziny dla Dostrajanie aplikacji.  Klasy pociągnąć za sobą 12 bajtów obciążenie x86 komputera nawet wtedy, gdy mają one nie ma pól, ale są one niedrogich do przekazania wokół, ponieważ trwa tylko wskaźnik do odwoływania się do wystąpienia klasy.  Struktury pociągnąć za sobą nie Alokacje sterty, jeśli nie są one opakowany, ale podczas przekazywania dużych struktury jako argumenty funkcji lub wartości zwracane, czas procesora CPU automatycznie skopiować wszystkie elementy członkowskie danych struktury.  Zwróć uwagę na powtarzane wywołania do właściwości, które zwraca struktury i pamięci podręcznej wartość właściwości w zmiennej lokalnej, aby uniknąć nadmiernego dane kopiowanie.  
  
 **Pamięci podręczne**  
  
 Typowe lewy wydajności jest wyniki pamięci podręcznej.  Jednak bez zakończenia lub usuwania zasad rozmiar pamięci podręcznej może być przeciek pamięci.  Podczas przetwarzania dużych ilości danych, jeśli mają celu dużej ilości pamięci w pamięci podręcznej, może spowodować wyrzucanie elementów bezużytecznych do przesłonięcia korzyści z pamięci podręcznej wyszukiwania.  
  
 W tym artykule omówiono sposób należy zwrócić uwagę objawy wąskich gardeł wydajności, które mogą wpłynąć na czas odpowiedzi aplikacji, zwłaszcza w przypadku dużych systemów lub systemów, które przetwarzają dużą ilość danych. Typowe sprawcami obejmują pakującej, działań na ciągach, LINQ i lambda, buforowanie w metodach asynchronicznych buforowanie bez rozmiar limit lub usuwania zasad, nieodpowiednie użycie słowniki i przekazywanie wokół struktury.  Należy pamiętać, cztery faktów dostrojenia aplikacji:  
  
-   Nie przedwcześnie Optymalizacja — produktywności i dostrajania aplikacji, gdy dodatkowe problemy.  
  
-   Profile nie znajdują się — w przypadku odgadnięcie, jeśli użytkownik nie notuje.  
  
-   Dobrym narzędzi zależy od — Pobierz narzędzia PerfView i wypróbować jej możliwości.  
  
-   Jest wszystkie o alokacji — czyli gdzie zespołu platformy kompilatora poświęconego większość czasu zwiększanie wydajności kompilatory nowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Wideo prezentacji w tym temacie](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [Profilowanie wydajności — przewodnik dla początkujących](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [Wydajność](../../../docs/framework/performance/index.md)  
 [Porady dotyczące wydajności .NET](http://msdn.microsoft.com/library/ms973839.aspx)  
 [Narzędzie do analizy wydajności Windows Phone](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [Znajdź wąskich gardeł aplikacji z profilera Visual Studio](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [Kanał 9 samouczki narzędzia PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [Porady dotyczące wydajności wysokiego poziomu](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [repozytorium DotNet/roslyn w witrynie GitHub](https://github.com/dotnet/roslyn)
