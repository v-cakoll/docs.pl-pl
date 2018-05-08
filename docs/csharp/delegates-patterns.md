---
title: Wspólne wzorce dla delegatów
description: Więcej informacji na temat wspólne wzorce dla używanie delegatów w kodzie, aby uniknąć silne sprzężenia między elementami.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: fceab2b9c6bbd1d687566820366459ec57ae7a2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="common-patterns-for-delegates"></a>Wspólne wzorce dla delegatów

[Poprzednie](delegates-strongly-typed.md)

Obiekty delegowane udostępniają mechanizm umożliwiający projektów oprogramowania obejmujące minimalny sprzężenia między składnikami.

Przykładem doskonała dla tego projektu jest LINQ. Wzorzec wyrażenia zapytań LINQ zależy od delegatów dla wszystkich funkcji. Należy wziąć pod uwagę to prosty przykład:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

To filtruje sekwencji liczb tylko te mniejsza niż wartość 10.
`Where` Metoda używa delegata, który określa, które elementy sekwencji przekazać filtr. Podczas tworzenia zapytania LINQ podanych w tym celu określonych implementacji obiektu delegowanego.

Prototyp w którym metoda jest:

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

W tym przykładzie jest powtarzany z metod, które są częścią LINQ. Wszystkie opierają się na delegatów dla kodu zarządzanego określonej kwerendy. Ten wzorzec projektowy interfejsu API jest bardzo przydatna do nauczenia i zrozumieć.

Ten prosty przykład ilustruje sposób delegatów wymaga bardzo małego sprzężenia między składnikami. Nie trzeba utworzyć klasę pochodną konkretnej klasy podstawowej. Nie należy do implementacji określonego interfejsu.
Jedynym wymaganiem jest zapewnienie stosowania jedną metodę, która jest niezbędne, aby wykonywanego zadania.

## <a name="building-your-own-components-with-delegates"></a>Tworzenie własnych składników z delegatów

Utworzymy w tym na przykład przez tworzenie składnika przy użyciu projektu, który korzysta z obiektów delegowanych.

Umożliwia zdefiniowanie składnik, który może posłużyć komunikatów dziennika w systemie duży. Składniki biblioteki można używać w wielu różnych środowiskach, na wielu różnych platformach. Istnieje wiele typowych funkcji w składniku, która zarządza dzienniki. Trzeba będzie akceptować komunikaty z dowolnego składnika w systemie. Te komunikaty będą mieć różnych priorytetów, które mogą zarządzać podstawowy składnik. Komunikaty powinien mieć sygnatur czasowych końcowego postać archiwizowane. Aby uzyskać bardziej zaawansowanych scenariuszy można filtrować wiadomości przez składnik źródłowy.

Istnieje jeden aspekt funkcję, która zmieni się często: gdzie komunikaty są zapisywane. W niektórych środowiskach może zostać wyświetlony w konsoli błędu. W innych osób, w pliku. Inne możliwości obejmują magazyn baz danych, dzienników zdarzeń systemu operacyjnego lub innych magazynów dokumentu.

Dostępne są także kombinacji danych wyjściowych, które mogą być używane w różnych scenariuszach. Możesz zapisać wiadomości do konsoli i w pliku.

Projekt na podstawie delegatów zapewniają dużą elastyczność i ułatwiają mechanizmów magazynu pomocy technicznej, które mogą zostać dodane w przyszłości.

W tym projekcie składnika dziennika podstawowego można Niewirtualny, nawet zapieczętowane klasy. Można podłączyć do każdego zestawu obiektów delegowanych do zapisywania wiadomości do innego magazynu nośnika. Obsługa wbudowanej obiekty delegowane multiemisji ułatwia scenariusze pomocy technicznej, w którym wiadomości musi być napisana w wielu lokalizacjach (pliku i konsoli).

## <a name="a-first-implementation"></a>Pierwszy implementacji

Zacznijmy małych: implementacja początkowej będzie akceptować nowych komunikatów i zapisze je przy użyciu dowolnego dołączonego obiektu delegowanego. Można uruchomić z jednego delegata, który zapisuje komunikaty do konsoli.

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

Klasa statyczna powyżej jest najprostsza rzecz, którą można pracować. Należy zapisać pojedynczej implementacji metody, która zapisuje komunikaty do konsoli: 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

Na koniec należy Podłączanie delegata przy dołączeniu go do WriteMessage, delegowanie zadeklarowany w rejestratora:

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a>Rozwiązania

Do tej pory naszej próbki jest dość proste, ale pokazuje nadal niektóre ważne wskazówki dla projektów obejmujących delegatów.

Przy użyciu zdefiniowanych w ramach podstawowych typów delegata ułatwia użytkownikom pracę z delegatów. Nie trzeba definiować nowych typów i deweloperów korzystających z biblioteki nie trzeba informacje typach nowe, wyspecjalizowany delegata.

Interfejsy używane są jako minimalna i jak najbardziej elastyczne: Aby utworzyć nowe rejestrowania danych wyjściowych, należy utworzyć jedną metodę. Ta metoda może być metodą statyczną lub metodą wystąpienia. Może mieć dostęp.

## <a name="formatting-output"></a>Formatowanie danych wyjściowych

Bit bardziej niezawodne i ponownie uruchomić tworzenie innych mechanizmów rejestrowania można wprowadzić tej pierwszej wersji.

Następnie Dodajmy mało argumentów dla `LogMessage()` metody, aby klasy dziennika tworzy więcej strukturalnych wiadomości:

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

Następnie można wprowadzić Użyj tego `Severity` wyjściowy argument do filtrowania wiadomości, które są wysyłane do dziennika. 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a>Rozwiązania

Nowe funkcje dodane do infrastruktury rejestrowania. Ponieważ składnik rejestratora jest bardzo luźno powiązane z mechanizmem żadnych danych wyjściowych, można dodać te nowe funkcje bez wpływu na żadnego kodu Implementowanie delegata rejestratora.

Jak zachować kompilowanie to, zobaczysz więcej przykładów jak tym luźne powiązanie zapewnia większą elastyczność podczas aktualizowania części witryny bez wprowadzania żadnych zmian do innych lokalizacji. W rzeczywistości w większej aplikacji klasy wyjściowe rejestratora może znajdować się w innym zestawie, a nawet należy ponownie utworzyć.

## <a name="building-a-second-output-engine"></a>Tworzenie drugiego aparat danych wyjściowych

Składnik dziennika pochodzi wzdłuż źródło. Dodajmy jeden więcej aparat wyjściowy, który rejestruje komunikaty do pliku. Są to wymaga nieco więcej wysiłku aparat danych wyjściowych. Będzie ona klasę, która hermetyzuje operacji na plikach i zapewnia, że plik jest zawsze zamknięte po wykonaniu każdego zapisu. Który zapewnia, że wszystkie dane jest opróżniany na dysku po wygenerowaniu każdego komunikatu.

Oto tego rejestratora plików na podstawie:

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

Po utworzeniu tej klasy można utworzyć i jego LogMessage — metoda dołącza do rejestratora składników:

```csharp
var file = new FileLogger("log.txt");
```

Te dwa nie wykluczają. Można dołączyć obu metod dziennika i generują komunikaty do konsoli i plik:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

Później nawet w tej samej aplikacji, można usunąć jeden z obiektów delegowanych bez żadnych innych problemów w systemie:

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>Rozwiązania

Teraz dodano dodatkowy program obsługi danych wyjściowych dla podsystem rejestrowania.
Ten zestaw wymaga nieco więcej infrastruktury do obsługi poprawnie systemu plików. Delegat jest metodą wystąpienia. Istnieje również Metoda prywatna.
Ponieważ infrastruktura delegata można się połączyć delegatów nie istnieje potrzeba większa ułatwień dostępu.

Po drugie projekt na podstawie delegata umożliwia wielu danych wyjściowych metody bez żadnych dodatkowych kodu. Nie jest potrzebne do tworzenia żadnych dodatkowych infrastruktury do obsługi wielu metod danych wyjściowych. Po prostu stają się one inna metoda na liście wywołania.

Należy zwrócić szczególną uwagę na kod w pliku rejestrowania danych wyjściowych metody. Zakodowanej aby upewnić się, że nie generują żadnych wyjątków. Gdy to nie zawsze jest to niezbędne, często jest dobrym rozwiązaniem. Jeśli jednej z metod delegata zgłasza wyjątek, nie można wywołać pozostałych obiektów delegowanych, które są w wywołaniu.

Jako ostatni Uwaga rejestratora plików muszą zarządzać jego zasobów przez otwieranie i zamykanie plików na wszystkich komunikatach dziennika. Użytkownik może zachować otwarty plik i zaimplementuj interfejs IDisposable, aby zamknąć plik, gdy zostały zakończone.
Każda metoda ma jego zalety i wady. Zarówno należy tworzyć bardziej sprzężenia między klasami.

Brak kodu w klasie rejestratora musi zostać zaktualizowany w celu wprowadzenia albo scenariusza.

## <a name="handling-null-delegates"></a>Obsługa delegatów wartości Null

Na koniec Przyjrzyjmy aktualizacji LogMessage — metoda, aby był niezawodny dla tych przypadków, gdy żaden mechanizm danych wyjściowych jest zaznaczone. Bieżąca implementacja zgłosi `NullReferenceException` podczas `WriteMessage` delegat ma listę wywołań dołączony.
Możesz wybrać projekt, który dyskretnie będzie kontynuowane po nie zostały dołączone żadnych metod. Jest to łatwe przy użyciu operatora warunkowego wartości null, połączeniu z `Delegate.Invoke()` metody:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Operator warunkowy wartości null (`?.`) short-circuits, kiedy Lewy argument operacji (`WriteMessage` w takim przypadku) ma wartość null, co oznacza, nie są podejmowane próby logowania wiadomości.

Nie możesz znaleźć `Invoke()` metody wymienione w dokumentacji dotyczącej `System.Delegate` lub `System.MulticastDelegate`. Kompilator generuje bezpieczne typu `Invoke` metody dla każdego delegować deklaracji typu. W tym przykładzie, oznacza to `Invoke` przyjmuje jeden `string` argumentu, i został zwrócony typ void.

## <a name="summary-of-practices"></a>Podsumowanie rozwiązania

Przedstawiono początku składnik dziennika, który może zostać rozszerzony o innych użytkowników i innych funkcji. Przy użyciu delegatów w projekcie tych różnych składników są bardzo luźno powiązane. Zapewnia kilka korzyści. Jest bardzo proste tworzenie nowych mechanizmów danych wyjściowych i dołącz je do systemu. Mechanizmy te wymagane jest tylko jedna metoda: metodę, która zapisuje komunikat w dzienniku. Jest to projekt, który jest bardzo elastyczne, gdy zostaną dodane nowe funkcje. Kontrakt wymagane dla dowolnego edytora jest wdrożenie jednej metody. Ta metoda może być statycznymi lub metody wystąpienia. Może to być public, private lub innych prawne dostęp.

Klasa rejestratora wprowadzić dowolną liczbę ulepszenia lub zmiany bez wprowadzania zmian, które psuły. Podobnie jak wszystkie klasy nie można zmodyfikować publiczny interfejs API bez ryzyka fundamentalne zmiany. Jednak ponieważ sprzężenia między rejestratora i wszelkie aparatami danych wyjściowych jest tylko za pośrednictwem pełnomocnika, są związane z żadnych innych typów (na przykład interfejsów lub klas podstawowych). Sprzężenia jest możliwie jak najmniejszy.

[Next](events-overview.md)
