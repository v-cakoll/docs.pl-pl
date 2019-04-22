---
title: Wspólne wzorce dla delegatów
description: Poznaj typowe wzorce do używania delegatów w kodzie w celu uniknięcia silne sprzężenia między składnikami.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: ea0e0b7af361b76c4b46b0a180e07b44c1fa07e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095701"
---
# <a name="common-patterns-for-delegates"></a>Wspólne wzorce dla delegatów

[Poprzednie](delegates-strongly-typed.md)

Delegaty zapewniają mechanizm, który umożliwia projekty oprogramowania obejmujące minimalny sprzężenia między składnikami.

Przykładem doskonałe dla tego rodzaju projektu jest LINQ. Wzorzec wyrażenia zapytań LINQ, zależy od delegatów dla wszystkich funkcji. Należy wziąć pod uwagę ten prosty przykład:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Filtruje numery tylko te mniejsza niż wartość 10.
`Where` Metoda używa delegata, która określa, które elementy sekwencji przekazać filtru. Podczas tworzenia zapytania LINQ podajesz implementację delegata do tego określonego celu.

Prototyp w którym metoda jest:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

W tym przykładzie jest powtarzany za pomocą metod, które są częścią LINQ. Wszystkie korzystają z delegatów dla kodu, który zarządza użytego zapytania. Ten wzorzec projektowania interfejsu API jest bardzo zaawansowane i zrozumieć.

Ten prosty przykład ilustruje, jak delegatów wymaga bardzo mało sprzężenia między składnikami. Nie trzeba utworzyć klasę, która pochodzi od konkretnej klasy bazowej. Nie ma potrzeby implementowania określonego interfejsu.
Jedynym wymaganiem jest zapewnienie stosowania jedną metodę, która ma podstawowe znaczenie dla wykonywanego zadania.

## <a name="building-your-own-components-with-delegates"></a>Tworzenie składników przy użyciu delegatów

Utworzymy w tym przykładzie, tworząc składnika za pomocą projektu, który opiera się na delegatów.

Czynnością jest zdefiniowanie składnika, która mogłaby być używana dla dziennika komunikatów w dużym systemie. Składniki biblioteki można używać w wielu różnych środowiskach, na wielu różnych platformach. Istnieje wiele typowych funkcji w składniku, który zarządza dzienniki. Trzeba będzie ją akceptować komunikaty z dowolnego składnika w systemie. Te komunikaty mają różne priorytety, których składnik core można zarządzać. Komunikatów mają sygnatury czasowe w ostatecznej postaci zarchiwizowane. Dla bardziej zaawansowanych scenariuszy można filtrować wiadomości przez składnik źródłowy.

Istnieje jeden z aspektów funkcji, która zmieni się często: gdy komunikaty są zapisywane. W niektórych środowiskach może zostać wyświetlony w konsoli błędu. W innych, plik. Inne możliwości obejmują Magazyn bazy danych, dzienników zdarzeń systemu operacyjnego lub innych przechowywania dokumentów.

Dostępne są także kombinacji danych wyjściowych, które mogą być używane w różnych scenariuszach. Możesz chcieć zapisywania komunikatów w konsoli oraz w pliku.

Projektowanie oparte na delegatach zapewniają dużą elastyczność i ułatwić obsługę magazynu mechanizmów, które mogą zostać dodane w przyszłości.

W tym projekcie dziennika podstawowego składnika może być niewirtualną, nawet zapieczętowanych klas. Można dodać dowolny zbiór delegatów do zapisywania komunikatów do innego magazynu multimediów. Obsługa wbudowane obiekty delegowane multiemisji można łatwo obsługiwane scenariusze, w której wiadomości musi być napisana w wielu lokalizacjach (plik i konsoli).

## <a name="a-first-implementation"></a>Pierwszy implementacji

Zacznijmy od małych: wstępne wdrożenie będzie akceptować nowe wiadomości i zapisać je przy użyciu dowolnego dołączonego delegata. Można uruchomić za pomocą jednego delegata, która wypisuje komunikaty na konsoli.

[!code-csharp[LoggerImplementation](../../samples/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Klasa statyczna powyżej jest najprostszym rzecz, którą można pracować. Potrzebujemy do zapisania pojedynczej implementacji metody, która wypisuje komunikaty na konsoli: 

[!code-csharp[LogToConsole](../../samples/csharp/delegates-and-events/Program.cs#LogToConsole "A Console logger.")]

Na koniec należy Podłączanie delegata, dołączając ją do WriteMessage delegatów zadeklarowanych w rejestratora:

[!code-csharp[ConnectDelegate](../../samples/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Rozwiązania

Do tej pory naszego przykładu jest dość prosta, ale nadal pokazuje niektóre ważne wskazówki dotyczące projektów obejmujących delegatów.

Przy użyciu typy delegatów, określone w ramach Core ułatwia użytkownikom pracę z delegatów. Nie trzeba definiować nowe typy i nie trzeba Dowiedz się, typy delegatów nowe, wyspecjalizowany deweloperzy korzystający z biblioteki.

Interfejsy używane są możliwie i jak najbardziej elastyczny: Aby utworzyć nowego rejestratora danych wyjściowych, należy utworzyć jedną z metod. Ta metoda może być metodą statyczną lub metodą wystąpienia. Może mieć dostęp do wszystkich.

## <a name="formatting-output"></a>Formatowanie danych wyjściowych

Upewnijmy się pierwszej wersji bitowych bardziej niezawodne i ponownie uruchomić tworzenie innych mechanizmów rejestrowania.

Następnie Dodajmy kilka argumentów `LogMessage()` metody, aby klasa dziennika tworzy więcej wiadomości ze strukturą:

[!code-csharp[Severity](../../samples/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Następnie upewnijmy się, użyj tego `Severity` argument do filtrowania wiadomości, które są wysyłane do dziennika danych wyjściowych. 

[!code-csharp[FinalLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Rozwiązania

Nowe funkcje dodano do infrastruktury rejestrowania. Ponieważ składnika modułu logującego się bardzo luźno mechanizmu żadnych danych wyjściowych, można dodać te nowe funkcje bez wpływu na dowolny kod Implementowanie delegata rejestratora.

Jak zachować możesz tworzyć, zobaczysz więcej przykładów jak tym luźne powiązanie umożliwia większą elastyczność w aktualizację części witryny bez konieczności wprowadzania zmian do innych lokalizacji. W rzeczywistości w większej aplikacji klasy wyjściowe rejestratora może znajdować się w innym zestawie, a nawet konieczne jest ponowne skompilowanie.

## <a name="building-a-second-output-engine"></a>Tworzenie drugiej aparatu danych wyjściowych

Składnik Log pochodzi wzdłuż dobrze. Dodajmy jeden więcej aparat danych wyjściowych, który rejestruje komunikaty w pliku. Są to wymaga nieco więcej wysiłku aparatu danych wyjściowych. Będzie ona klasę, która hermetyzuje operacji na plikach i gwarantuje, że plik jest zawsze zamknięte po każdym zapisie. Który zapewnia, że wszystkie dane jest opróżniany do dysku po każdy komunikat jest generowany.

Oto rejestratora tego pliku:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Po utworzeniu tej klasy tworzenia jego instancji i jego logmessage — metoda dołącza do składnika modułu logującego:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Te dwa nie wykluczają się wzajemnie. Można dołączyć obu metod dziennika i generowanie wiadomości do konsoli i plik:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

Później nawet w tej samej aplikacji, możesz usunąć jeden z obiektów delegowanych, bez żadnych innych problemów w systemie:

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>Rozwiązania

Teraz dodaniu drugiego danych wyjściowych procedury obsługi na potrzeby rejestrowania podsystemu.
Ten zestaw wymaga nieco więcej infrastruktury do poprawnie obsługiwać system plików. Delegat jest metodą wystąpienia. Jest również metody prywatnej.
Nie ma potrzeby lepsze ułatwienia dostępu, ponieważ infrastruktury delegata można połączyć delegatów.

Po drugie projektowanie oparte na delegatach umożliwia wielu metod wyjścia metod bez konieczności wprowadzania dodatkowego kodu. Nie trzeba tworzyć jakiejkolwiek dodatkowej infrastruktury do obsługi wielu metod wyjścia. Po prostu stają się one innej metody na liście wywołania.

Należy zwrócić szczególną uwagę na kod w pliku rejestrowania metoda danych wyjściowych. Jest on kodowane, aby upewnić się, że nie generuje żadnych wyjątków. Chociaż nie jest to niezbędne, jest często dobrym rozwiązaniem. Jeśli jednej z metod delegata zgłasza wyjątek, nie można wywołać pozostałych obiektów delegowanych, które znajdują się na wywołanie.

Jako ostatni notatki rejestratora plików muszą zarządzać jego zasobów otwierający i zamykający go na wszystkich komunikatach dziennika. Można pozostawić otwarty plik i zaimplementuj interfejs IDisposable, aby zamknąć go po zakończeniu.
Każda metoda ma swoje zalety i wady. Obie umożliwiają tworzenie bardziej sprzężenia między klasami.

Brak kodu w klasie rejestratora musi zostać zaktualizowane w celu obsługi dowolnego scenariusza.

## <a name="handling-null-delegates"></a>Obsługa wartości Null delegatów

Na koniec spróbujmy aktualizacji logmessage — metoda, aby był niezawodny dla tych przypadków, gdy żaden mechanizm danych wyjściowych jest zaznaczone. Bieżąca implementacja spowoduje zgłoszenie `NullReferenceException` podczas `WriteMessage` delegat nie ma listę wywołań, który jest dołączony.
Możesz projekt, który dyskretnie kontynuowana po dołączono żadnych metod. Jest to łatwe za pomocą operatora warunkowego wartości null, w połączeniu z `Delegate.Invoke()` metody:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Operator warunkowy o wartości null (`?.`) short-circuits, kiedy Lewy argument operacji (`WriteMessage` w tym przypadku) ma wartość null, oznacza to, aby zarejestrować komunikat jest podejmowana próba.

Nie odnajdzie `Invoke()` metody wymienione w dokumentacji dotyczącej `System.Delegate` lub `System.MulticastDelegate`. Kompilator generuje bezpieczny `Invoke` metody dla każdego delegować deklaracji typu. W tym przykładzie, oznacza to, `Invoke` przyjmuje jeden `string` argument, a ma zwracać typ void.

## <a name="summary-of-practices"></a>Podsumowanie rozwiązań

Po zapoznaniu początku składnik dziennika, który może zostać rozszerzona przy użyciu innych składników zapisywania i innych funkcji. Przy użyciu delegatów w projekcie te składniki są bardzo luźno powiązane. Dzięki temu można ze sobą pewne korzyści. Jest bardzo proste utworzyć nowe mechanizmy danych wyjściowych i dołącz je do systemu. Te inne mechanizmy wymagane jest tylko jedna metoda: metoda, która zapisuje komunikat w dzienniku. Jest to projekt, który jest bardzo odporne na błędy, gdy zostaną dodane nowe funkcje. Kontrakt wymagane dla dowolnego edytora jest zaimplementować jedną z metod. Tej metody może być statyczną lub metodę wystąpienia. Można prywatnej, publicznej lub innym prawne dostępu.

Klasa rejestratora wprowadzać dowolną liczbę ulepszenia lub zmiany bez wprowadzania istotnych zmian. Podobnie jak dowolnej klasy nie można zmodyfikować publiczny interfejs API bez ryzyka istotne zmiany. Jednak ponieważ sprzężenie między rejestratora i aparaty żadnych danych wyjściowych jest wyłącznie za pośrednictwem delegata, żadne inne typy (takich jak interfejsy lub klas bazowych) są zaangażowane. Sprzężenia jest tak małej, jak to możliwe.

[Next](events-overview.md)
