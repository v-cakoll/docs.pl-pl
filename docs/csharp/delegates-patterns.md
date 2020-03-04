---
title: Wspólne wzorce dla delegatów
description: Zapoznaj się z typowymi wzorcami dotyczącymi używania delegatów w kodzie, aby uniknąć silnego sprzężenia między składnikami.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 40e6ced7337e32d6e9b67b12a15ad7e03a77c4b6
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239875"
---
# <a name="common-patterns-for-delegates"></a>Wspólne wzorce dla delegatów

[Wstecz](delegates-strongly-typed.md)

Delegaty zapewniają mechanizm, który umożliwia projekty oprogramowania, które obejmują minimalny sprzężenie między składnikami.

Jednym z doskonały przykładu dla tego rodzaju projektu jest LINQ. Wzorzec wyrażenia zapytania LINQ opiera się na delegatach dla wszystkich swoich funkcji. Rozważmy ten prosty przykład:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

To filtruje sekwencję liczb tylko do wartości mniejszej niż wartość 10.
Metoda `Where` używa delegata, który określa, które elementy sekwencji przechodzą filtr. Podczas tworzenia zapytania LINQ należy podać implementację delegata w tym konkretnym celu.

Prototyp dla metody WHERE:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Ten przykład powtarza się ze wszystkimi metodami, które są częścią LINQ. Wszyscy korzystają z delegatów dla kodu, który zarządza konkretną kwerendą. Ten Wzorzec projektowy interfejsu API jest bardzo wydajny, aby poznać i zrozumieć.

W tym prostym przykładzie przedstawiono sposób, w jaki Delegaty potrzebują bardzo mało sprzężenia między składnikami. Nie musisz tworzyć klasy, która pochodzi od określonej klasy bazowej. Nie trzeba implementować określonego interfejsu.
Jedynym wymaganiem jest zapewnienie implementacji jednej metody, która jest podstawowa dla danego zadania.

## <a name="building-your-own-components-with-delegates"></a>Tworzenie własnych składników za pomocą delegatów

Zacznijmy od tego przykładu, tworząc składnik przy użyciu projektu, który jest zależny od delegatów.

Zdefiniujmy składnik, który może być używany na potrzeby komunikatów dzienników w dużym systemie. Składniki biblioteki mogą być używane w wielu różnych środowiskach na wielu różnych platformach. Składnik zarządzający dziennikami zawiera wiele typowych funkcji. Konieczne będzie zaakceptowanie komunikatów z dowolnego składnika w systemie. Te komunikaty będą mieć różne priorytety, którymi może zarządzać składnik podstawowy. Komunikaty powinny mieć sygnatury czasowe w końcowej zarchiwizowanej postaci. W przypadku bardziej zaawansowanych scenariuszy można filtrować komunikaty według składnika źródłowego.

Istnieje jeden aspekt funkcji, która często zmienia się: gdzie są zapisywane wiadomości. W niektórych środowiskach mogą one być zapisywane w konsoli błędów. W innych, plik. Inne możliwości obejmują Magazyn bazy danych, dzienniki zdarzeń systemu operacyjnego lub inne magazyny dokumentów.

Istnieją także kombinacje danych wyjściowych, które mogą być używane w różnych scenariuszach. Możesz chcieć pisać komunikaty do konsoli programu i do pliku.

Projekt oparty na delegatach zapewnia dużą elastyczność i ułatwia obsługę mechanizmów magazynu, które mogą zostać dodane w przyszłości.

W ramach tego projektu podstawowy składnik dziennika może być niewirtualną, nawet klasą zapieczętowana. Można podłączyć dowolnego zestawu delegatów, aby zapisywać komunikaty na innym nośniku magazynu. Wbudowana obsługa delegatów multiemisji ułatwia obsługę scenariuszy, w których komunikaty muszą być zapisywane w wielu lokalizacjach (pliku i konsoli).

## <a name="a-first-implementation"></a>Pierwsza implementacja

Zacznijmy od początku: początkowa implementacja przyjmie nowe komunikaty i zapisze je przy użyciu dowolnego dołączonego delegata. Możesz rozpocząć od jednego delegata, który zapisuje komunikaty w konsoli programu.

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Powyższa Klasa statyczna jest najprostszą czynnością, którą można obsłużyć. Musimy napisać pojedynczą implementację metody, która zapisuje komunikaty w konsoli: 

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Na koniec należy podłączyć delegata, dołączając go do delegata WriteMessage zadeklarowanego w rejestratorze:

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Procedur

Nasz przykład jest dość prosty, ale nadal pokazuje niektóre z ważnych wytycznych dotyczących projektów obejmujących delegatów.

Użycie typów delegatów zdefiniowanych w podstawowym środowisku ułatwia użytkownikom pracę z delegatami. Nie musisz definiować nowych typów, a deweloperzy korzystający z biblioteki nie muszą uczyć się nowych, wyspecjalizowanych typów delegatów.

Używane interfejsy są minimalne i elastyczne, jak to możliwe: Aby utworzyć nowy Rejestrator danych wyjściowych, należy utworzyć jedną metodę. Ta metoda może być metodą statyczną lub metodą wystąpienia. Może mieć dowolny dostęp.

## <a name="formatting-output"></a>Formatowanie danych wyjściowych

Przypuśćmy, że ta pierwsza wersja jest nieco bardziej niezawodna, a następnie rozpocznie tworzenie innych mechanizmów rejestrowania.

Następnie Dodajmy kilka argumentów do metody `LogMessage()`, aby Klasa log tworzyła bardziej uporządkowane komunikaty:

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Następnie Użyjmy tego argumentu `Severity`, aby odfiltrować komunikaty wysyłane do danych wyjściowych dziennika. 

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Procedur

Dodano nowe funkcje do infrastruktury rejestrowania. Ze względu na to, że składnik rejestratora jest bardzo luźno połączony z jakimkolwiek mechanizmem wyjścia, nowe funkcje mogą być dodawane bez wpływu na żaden kod implementujący delegata rejestratora.

Podczas kompilowania tego procesu zobaczysz więcej przykładów, jak ten luźny sprzężenie zapewnia większą elastyczność aktualizowania części lokacji bez wprowadzania zmian w innych lokalizacjach. W rzeczywistości klasy wyjściowe rejestratora mogą znajdować się w innym zestawie, a nawet nie muszą być odbudowane.

## <a name="building-a-second-output-engine"></a>Kompilowanie drugiego aparatu wyjściowego

Składnik dziennika jest również dobrze. Dodajmy do jednego aparatu wyjściowego, który zapisuje komunikaty do pliku. Będzie to nieco bardziej przeprowadzony aparat wyjściowy. Będzie to Klasa, która hermetyzuje operacje na plikach i gwarantuje, że plik jest zawsze zamykany po każdym zapisie. Gwarantuje to, że wszystkie dane zostaną opróżnione na dysk po wygenerowaniu poszczególnych komunikatów.

Oto ten Rejestrator oparty na plikach:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Po utworzeniu tej klasy można utworzyć jej wystąpienie i dołączyć jej metodę LogMessage do składnika rejestratora:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Te dwa nie wykluczają się wzajemnie. Można dołączyć zarówno metody rejestrowania, jak i generować komunikaty do konsoli programu i pliku:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Później, nawet w tej samej aplikacji, można usunąć jednego z delegatów bez żadnych innych problemów do systemu:

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Procedur

Teraz została dodana druga procedura obsługi danych wyjściowych dla podsystemu rejestrowania.
Wymaga to nieco większej infrastruktury, aby prawidłowo obsługiwać system plików. Delegat jest metodą wystąpienia. Jest to również Metoda prywatna.
Nie ma potrzeby większego ułatwienia dostępu, ponieważ infrastruktura delegatów może połączyć delegatów.

W drugim, projekt oparty na delegatach umożliwia wiele metod wyjściowych bez żadnego dodatkowego kodu. Nie trzeba tworzyć żadnej dodatkowej infrastruktury do obsługi wielu metod wyjściowych. Po prostu stają się one kolejną metodą na liście wywołań.

Zwróć szczególną uwagę na kod w metodzie wyjściowej rejestrowania plików. Jest on kodowany, aby upewnić się, że nie generuje żadnych wyjątków. Chociaż nie zawsze jest to konieczne, jest to często dobre rozwiązanie. Jeśli jedna z metod delegatów zgłasza wyjątek, pozostałe Delegaty, które znajdują się w wywołaniu nie będą wywoływane.

W ostatniej notatce Rejestrator plików musi zarządzać swoimi zasobami, otwierając i zamykając plik w każdym komunikacie dziennika. Po zakończeniu pracy można pozostawić plik otwarty i zaimplementować interfejs IDisposable, aby zamknąć plik.
Każda metoda ma swoje zalety i wady. Oba te elementy tworzą bit więcej sprzęgania między klasami.

Żaden kod w klasie rejestratorów nie musi zostać zaktualizowany w celu obsługi jednego z tych scenariuszy.

## <a name="handling-null-delegates"></a>Obsługa delegatów o wartości null

Na koniec zaktualizujmy metodę LogMessage, tak aby była niezawodna dla tych przypadków, gdy nie wybrano żadnego mechanizmu wyjściowego. Bieżąca implementacja zgłosi `NullReferenceException`, gdy delegat `WriteMessage` nie ma dołączonej listy wywołań.
Możesz preferować projekt, który jest dyskretnie kontynuowany, gdy nie dołączono żadnych metod. Jest to proste użycie operatora warunkowego null, połączonego z metodą `Delegate.Invoke()`:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Dwuobwodowy operator warunkowy o wartości null (`?.`), gdy lewy argument operacji (`WriteMessage` w tym przypadku) ma wartość null, co oznacza, że nie podjęto próby zarejestrowania komunikatu.

Nie znajdziesz metody `Invoke()` wymienionej w dokumentacji `System.Delegate` lub `System.MulticastDelegate`. Kompilator generuje metodę `Invoke` bezpiecznego typu dla dowolnego zadeklarowanego typu delegata. W tym przykładzie oznacza to, że `Invoke` przyjmuje jeden argument `string` i ma zwracany typ void.

## <a name="summary-of-practices"></a>Podsumowanie praktyk

Pojawiły się początek składnika dziennika, który można rozszerzyć za pomocą innych autorów i innych funkcji. Korzystając z delegatów w projekcie, te różne składniki są bardzo luźno sprzężone. Zapewnia to kilka korzyści. Łatwo jest utworzyć nowe mechanizmy wyjściowe i dołączyć je do systemu. Te inne mechanizmy potrzebują tylko jednej metody: metoda, która zapisuje komunikat dziennika. Jest to projekt, który jest bardzo odporny po dodaniu nowych funkcji. Kontrakt wymagany dla każdego składnika zapisywania programu to implementacja jednej metody. Ta metoda może być metodą statyczną lub wystąpieniem. Może to być publiczne, prywatne lub inny dostęp prawny.

Klasa rejestratora może wprowadzać dowolną liczbę ulepszeń lub zmian bez wprowadzania istotnych zmian. Podobnie jak w przypadku każdej klasy, nie można zmodyfikować publicznego interfejsu API bez ryzyka naruszenia zmian. Jednak ponieważ sprzężenie między rejestratorem a wszystkimi aparatami wyjściowymi odbywa się tylko za pomocą delegata, nie są wykorzystywane żadne inne typy (takie jak interfejsy lub klasy bazowe). Sprzęganie jest tak małe, jak to możliwe.

[Dalej](events-overview.md)
