---
title: Wspólne wzorce dla delegatów
description: Dowiedz się więcej o typowych wzorców do używania delegatów w kodzie, aby uniknąć silnego sprzężenia między składnikami.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 22ab88e5b139381e3a8921baa20df035f1405146
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399666"
---
# <a name="common-patterns-for-delegates"></a>Wspólne wzorce dla delegatów

[Wstecz](delegates-strongly-typed.md)

Delegaci zapewniają mechanizm, który umożliwia projektowanie oprogramowania obejmujące minimalne sprzężenie między komponentami.

Doskonałym przykładem tego rodzaju konstrukcji jest LINQ. Wzorzec wyrażenia kwerendy LINQ opiera się na delegatów dla wszystkich jego funkcji. Rozważmy ten prosty przykład:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Spowoduje to filtrsekwencję liczb tylko do tych, które są mniejsze niż wartość 10.
Metoda `Where` używa delegata, który określa, które elementy sekwencji przekazać filtr. Podczas tworzenia kwerendy LINQ, należy podać implementację pełnomocnika w tym konkretnym celu.

Prototypem metody Where jest:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

W tym przykładzie jest powtarzany ze wszystkimi metodami, które są częścią LINQ. Wszystkie one opierają się na delegatów dla kodu, który zarządza określonej kwerendy. Ten wzorzec projektowania interfejsu API jest bardzo potężny, aby dowiedzieć się i zrozumieć.

W tym prostym przykładzie przedstawiono, jak delegaci wymagają bardzo mało sprzężenia między składnikami. Nie trzeba tworzyć klasy, która pochodzi z określonej klasy podstawowej. Nie trzeba implementować określonego interfejsu.
Jedynym wymogiem jest zapewnienie wdrożenia jednej metody, która ma podstawowe znaczenie dla wykonywanego zadania.

## <a name="building-your-own-components-with-delegates"></a>Budowanie własnych komponentów z delegatami

Skorzystajmy na tym przykładzie, tworząc składnik przy użyciu projektu, który opiera się na delegatów.

Zdefiniujmy składnik, który może służyć do wiadomości dziennika w dużym systemie. Składniki biblioteki mogą być używane w wielu różnych środowiskach, na wielu różnych platformach. Istnieje wiele typowych funkcji w składniku, który zarządza dzienników. Będzie musiał akceptować wiadomości z dowolnego składnika w systemie. Te komunikaty będą miały różne priorytety, którymi może zarządzać podstawowy składnik. Wiadomości powinny mieć sygnatury czasowe w ostatecznej formie archiwizowanej. W przypadku bardziej zaawansowanych scenariuszy można filtrować wiadomości według składnika źródłowego.

Jest jeden aspekt funkcji, który często się zmienia: gdzie wiadomości są zapisywane. W niektórych środowiskach mogą być zapisywane w konsoli błędów. W innych plik. Inne możliwości obejmują przechowywanie bazy danych, dzienniki zdarzeń systemu operacyjnego lub inne magazyny dokumentów.

Istnieją również kombinacje danych wyjściowych, które mogą być używane w różnych scenariuszach. Możesz napisać wiadomości do konsoli i do pliku.

Projekt oparty na delegatach zapewni dużą elastyczność i ułatwi obsługę mechanizmów przechowywania, które mogą zostać dodane w przyszłości.

Zgodnie z tym projektem podstawowy składnik dziennika może być niewirtualną, nawet zapieczętowaną klasą. Można podłączyć dowolny zestaw delegatów do zapisywania wiadomości na różnych nośnikach magazynu. Wbudowana obsługa delegatów multiemisji ułatwia obsługę scenariuszy, w których wiadomości muszą być zapisywane w wielu lokalizacjach (pliku i konsoli).

## <a name="a-first-implementation"></a>Pierwsza implementacja

Zacznijmy od małych: początkowej implementacji będzie akceptować nowe wiadomości i zapisywać je przy użyciu dowolnego dołączonego delegata. Możesz zacząć od jednego pełnomocnika, który zapisuje wiadomości do konsoli.

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Klasa statyczna powyżej jest najprostszą rzeczą, która może działać. Musimy napisać pojedynczą implementację dla metody, która zapisuje wiadomości do konsoli:

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Na koniec należy podłączyć delegata, dołączając go do delegata WriteMessage zadeklarowanego w rejestratorze:

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Praktyk

Nasza dotychczasowa próbka jest dość prosta, ale nadal pokazuje niektóre z ważnych wytycznych dotyczących projektów z udziałem delegatów.

Korzystanie z typów delegatów zdefiniowanych w ramach podstawowej ułatwia użytkownikom pracę z delegatami. Nie trzeba definiować nowych typów, a deweloperzy korzystający z biblioteki nie muszą uczyć się nowych, wyspecjalizowanych typów delegatów.

Interfejsy używane są tak minimalne i elastyczne, jak to możliwe: Aby utworzyć nowy rejestrator wyjściowy, należy utworzyć jedną metodę. Ta metoda może być metodą statyczną lub metodą wystąpienia. Może mieć dowolny dostęp.

## <a name="formatting-output"></a>Wyjście formatowania

Zróbmy tę pierwszą wersję nieco bardziej niezawodne, a następnie rozpocząć tworzenie innych mechanizmów rejestrowania.

Następnie dodajmy kilka argumentów do `LogMessage()` metody, aby klasa dziennika tworzył bardziej uporządkowane komunikaty:

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Następnie użyjmy tego `Severity` argumentu do filtrowania wiadomości, które są wysyłane do danych wyjściowych dziennika.

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Praktyk

Dodano nowe funkcje do infrastruktury rejestrowania. Ponieważ składnik rejestratora jest bardzo luźno sprzężona z dowolnym mechanizmem wyjściowym, te nowe funkcje można dodać bez wpływu na którykolwiek z kodu implementującego delegata rejestratora.

Podczas tworzenia tego, zobaczysz więcej przykładów, jak to luźne sprzęgło umożliwia większą elastyczność w aktualizowaniu części witryny bez żadnych zmian w innych lokalizacjach. W rzeczywistości w większej aplikacji klasy danych wyjściowych rejestratora może być w innym zestawie, a nawet nie muszą być przebudowany.

## <a name="building-a-second-output-engine"></a>Budowa drugiego silnika wyjściowego

Składnik Dziennik nadchodzi dobrze. Dodajmy jeszcze jeden aparat wyjściowy, który rejestruje wiadomości do pliku. Będzie to nieco bardziej zaangażowany silnik wyjściowy. Będzie to klasa, która hermetyzuje operacje pliku i zapewnia, że plik jest zawsze zamknięty po każdym zapisie. Gwarantuje to, że wszystkie dane są opróżniane na dysku po wygenerowaniu każdej wiadomości.

Oto, że plik na logger:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Po utworzeniu tej klasy można utworzyć jej wystąpienia i dołączyć metodę LogMessage do składnika Logger:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Te dwa nie wykluczają się wzajemnie. Można dołączyć obie metody dziennika i wygenerować wiadomości do konsoli i pliku:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Później, nawet w tej samej aplikacji, można usunąć jednego z delegatów bez żadnych innych problemów z systemem:

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Praktyk

Teraz dodano drugi program obsługi danych wyjściowych dla podsystemu rejestrowania.
Ten potrzebuje nieco więcej infrastruktury, aby poprawnie obsługiwać system plików. Delegat jest metodą wystąpienia. Jest to również metoda prywatna.
Nie ma potrzeby większej dostępności, ponieważ infrastruktura delegata można połączyć delegatów.

Po drugie, projekt oparty na delegowaniu umożliwia wiele metod wyjściowych bez dodatkowego kodu. Nie trzeba tworzyć żadnej dodatkowej infrastruktury do obsługi wielu metod wyjściowych. Po prostu stają się inną metodą na liście wywołania.

Należy zwrócić szczególną uwagę na kod w metodzie danych wyjściowych rejestrowania plików. Jest kodowany, aby upewnić się, że nie zgłasza żadnych wyjątków. Chociaż nie zawsze jest to absolutnie konieczne, często jest to dobra praktyka. Jeśli którakolwiek z metod delegata zgłasza wyjątek, pozostałych delegatów, które są na wywołanie nie będą wywoływane.

W ostatniej uwadze rejestrator plików musi zarządzać swoimi zasobami, otwierając i zamykając plik w każdej wiadomości dziennika. Można zachować plik otwarty i zaimplementować IDisposable, aby zamknąć plik po zakończeniu.
Każda z tych metod ma swoje zalety i wady. Oba utworzyć nieco więcej sprzężenia między klasami.

Żaden kod w Logger klasy musiałby zostać zaktualizowany w celu obsługi obu scenariuszy.

## <a name="handling-null-delegates"></a>Obsługa delegatów null

Na koniec zaktualizujmy LogMessage metody tak, aby była niezawodna dla tych przypadków, gdy nie jest wybrany mechanizm wyjściowy. Bieżąca implementacja `NullReferenceException` spowoduje `WriteMessage` wyświetlenie a, gdy pełnomocnik nie ma listy wywołania dołączone.
Możesz preferować projekt, który po cichu trwa, gdy nie zostały dołączone żadne metody. Jest to łatwe przy użyciu operatora warunkowego null, w połączeniu `Delegate.Invoke()` z metodą:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Operator warunkowy`?.`null ( ) zwarcia,`WriteMessage` gdy lewy operand (w tym przypadku) jest null, co oznacza, że nie jest podejmowano próby rejestrowania wiadomości.

Nie znajdziesz metody wymienionej `Invoke()` w dokumentacji `System.Delegate` dla `System.MulticastDelegate`lub . Kompilator generuje metodę `Invoke` bezpiecznego typu dla dowolnego zadeklarowanego typu delegata. W tym przykładzie `Invoke` oznacza to, że ma pojedynczy `string` argument i ma typ zwracania void.

## <a name="summary-of-practices"></a>Podsumowanie praktyk

Widzieliście początki składnika dziennika, który można rozszerzyć o inne moduły zapisujące i inne funkcje. Za pomocą delegatów w projekcie te różne składniki są bardzo luźno sprzęgo. Zapewnia to kilka zalet. Bardzo łatwo jest stworzyć nowe mechanizmy wyjściowe i dołączyć je do systemu. Te inne mechanizmy potrzebują tylko jednej metody: metody, która zapisuje komunikat dziennika. Jest to projekt, który jest bardzo odporny, gdy dodawane są nowe funkcje. Kontrakt wymagany dla każdego modułu zapisującego jest zaimplementowanie jednej metody. Ta metoda może być metodą statyczną lub instancji. Może to być publiczny, prywatny lub inny dostęp prawny.

Logger Klasy można wprowadzić dowolną liczbę ulepszeń lub zmian bez wprowadzania wprowadzania zmian. Podobnie jak każda klasa, nie można zmodyfikować publicznego interfejsu API bez ryzyka zerwania zmian. Ale ponieważ sprzężenie między rejestratora i aparatów wyjściowych jest tylko za pośrednictwem delegata, nie inne typy (jak interfejsy lub klasy podstawowe) są zaangażowane. Sprzęgło jest tak małe, jak to możliwe.

[Dalej](events-overview.md)
