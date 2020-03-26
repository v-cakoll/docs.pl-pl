---
title: Tworzenie typów mixin przy użyciu domyślnych metod interfejsu
description: Za pomocą domyślnych elementów członkowskich interfejsu można rozszerzyć interfejsy z opcjonalnymi implementacjami domyślnymi dla realizatorów.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: ee0536ef51f9bea3e6851be23cc19fa28cc6916b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134377"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Samouczek: Mieszanie funkcji podczas tworzenia klas przy użyciu interfejsów z domyślnymi metodami interfejsu

Począwszy od języka C# 8.0 w .NET Core 3.0, można zdefiniować implementacji podczas deklarowania członka interfejsu. Ta funkcja zapewnia nowe możliwości, w których można zdefiniować domyślne implementacje dla funkcji zadeklarowanych w interfejsach. Klasy można wybrać, kiedy zastąpić funkcjonalność, kiedy używać funkcji domyślnych, a kiedy nie zadeklarować obsługę dyskretnych funkcji.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Tworzenie interfejsów z implementacjami, które opisują funkcje dyskretne.
> * Tworzenie klas, które używają implementacji domyślnych.
> * Tworzenie klas, które zastępują niektóre lub wszystkie implementacje domyślne.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilatora C# 8.0. Kompilator języka C# 8.0 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowszej.

## <a name="limitations-of-extension-methods"></a>Ograniczenia metod rozszerzenia

Jednym ze sposobów zaimplementowania zachowania, które pojawia się jako część interfejsu jest zdefiniowanie [metod rozszerzenia,](../programming-guide/classes-and-structs/extension-methods.md) które zapewniają zachowanie domyślne. Interfejsy deklarują minimalny zestaw elementów członkowskich, zapewniając jednocześnie większą powierzchnię dla każdej klasy, która implementuje ten interfejs. Na przykład metody rozszerzenia <xref:System.Linq.Enumerable> w dostarczać implementacji dla dowolnej sekwencji być źródłem zapytania LINQ.

Metody rozszerzenia są rozpoznawane w czasie kompilacji, przy użyciu zadeklarowanego typu zmiennej. Klasy, które implementują interfejs może zapewnić lepszą implementację dla każdej metody rozszerzenia. Deklaracje zmiennych muszą być zgodne z typem implementacjącym, aby umożliwić kompilatorowi wybranie tej implementacji. Gdy typ czasu kompilacji pasuje do interfejsu, wywołanie metody rozpoznawania rozpoznawania metody rozszerzenia. Innym problemem z metody rozszerzenia jest, że te metody są dostępne wszędzie tam, gdzie klasa zawierająca metody rozszerzenia jest dostępna. Klasy nie mogą zadeklarować, czy powinny lub nie powinny dostarczać funkcje zadeklarowane w metody rozszerzenia.

Począwszy od języka C# 8.0, można zadeklarować domyślne implementacje jako metody interfejsu. Następnie każda klasa automatycznie używa domyślnej implementacji. Każda klasa, która może zapewnić lepszą implementację można zastąpić definicję metody interfejsu z lepszym algorytmem. W pewnym sensie technika ta brzmi podobnie do tego, jak można użyć [metod rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md).

W tym artykule dowiesz się, jak domyślne implementacje interfejsu włączyć nowe scenariusze.

## <a name="design-the-application"></a>Zaprojektuj aplikację

Należy wziąć pod uwagę aplikację automatyki domowej. Prawdopodobnie masz wiele różnych rodzajów świateł i wskaźników, które mogą być używane w całym domu. Każde światło musi obsługiwać interfejsy API, aby je włączać i wyłączać oraz zgłaszać bieżący stan. Niektóre światła i wskaźniki mogą obsługiwać inne funkcje, takie jak:

- Włącz światło, a następnie wyłącz ją po upływie czasu.
- Migać światło przez pewien czas.

Niektóre z tych rozszerzonych możliwości mogą być emulowane w urządzeniach obsługujących zestaw minimalny. Oznacza to, że zapewnia domyślną implementację. W przypadku tych urządzeń, które mają wbudowane więcej funkcji, oprogramowanie urządzenia będzie korzystać z natywnych funkcji. W przypadku innych świateł mogą zdecydować się na zaimplementowanie interfejsu i użycie implementacji domyślnej.

Domyślne elementy członkowskie interfejsu jest lepszym rozwiązaniem dla tego scenariusza niż metody rozszerzenia. Autorzy klas mogą kontrolować, które interfejsy zdecydują się zaimplementować. Te interfejsy, które wybierają, są dostępne jako metody. Ponadto ponieważ domyślne metody interfejsu są domyślnie wirtualne, wysyłka metody zawsze wybiera implementację w klasie.

Utwórzmy kod, aby zademonstrować te różnice.

## <a name="create-interfaces"></a>Tworzenie interfejsów

Zacznij od utworzenia interfejsu, który definiuje zachowanie dla wszystkich świateł:

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Podstawowe napowietrzne oprawy oświetleniowej może zaimplementować ten interfejs, jak pokazano w poniższym kodzie:

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

W tym samouczku kod nie dysk urządzeń IoT, ale emuluje te działania, pisząc wiadomości do konsoli. Możesz eksplorować kod bez automatyzacji domu.

Następnie zdefiniujmy interfejs dla światła, które może automatycznie wyłączyć po prze skończeniu limitu czasu:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Można dodać podstawową implementację do światła napowietrznego, ale lepszym `virtual` rozwiązaniem jest zmodyfikowanie tej definicji interfejsu w celu zapewnienia domyślnej implementacji:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Dodając tę zmianę, `OverheadLight` klasa może zaimplementować funkcję czasomierza, deklarując obsługę interfejsu:

```csharp
public class OverheadLight : ITimerLight { }
```

Inny typ światła może obsługiwać bardziej zaawansowany protokół. Może zapewnić własną implementację dla `TurnOnFor`, jak pokazano w poniższym kodzie:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

W przeciwieństwie do nadrzędnych metod `TurnOnFor` klasy `HalogenLight` wirtualnej, deklaracja w klasie nie używa słowa kluczowego. `override`

## <a name="mix-and-match-capabilities"></a>Mieszanie i dopasowywki

Zalety domyślnych metod interfejsu stają się jaśniejsze w miarę wprowadzania bardziej zaawansowanych funkcji. Korzystanie z interfejsów umożliwia mieszanie i dopasowywać możliwości. Umożliwia również każdemu autorowi klasy wybór między domyślną implementacją a implementacją niestandardową. Dodajmy interfejs z domyślną implementacją migającej kontrolki:

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Domyślna implementacja umożliwia miganie dowolnej lampki. Kontrolka napowietrzna może dodać zarówno czasomierz, jak i funkcje migania przy użyciu domyślnej implementacji:

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Nowy typ światła, `LEDLight` obsługuje zarówno funkcję timera, jak i funkcję mrugnięcia bezpośrednio. Ten lekki styl implementuje zarówno `ITimerLight` interfejsy, jak i `IBlinkingLight` interfejsy i zastępuje `Blink` metodę:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Może `ExtraFancyLight` obsługiwać funkcje migania i czasomierza bezpośrednio:

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

Utworzony `HalogenLight` wcześniej nie obsługuje migania. Tak, nie należy `IBlinkingLight` dodawać do listy obsługiwanych interfejsów.

## <a name="detect-the-light-types-using-pattern-matching"></a>Wykrywanie typów światła za pomocą dopasowywania wzorców

Następnie napiszmy kod testowy. Można użyć funkcji [dopasowywania wzorca](../pattern-matching.md) języka C#, aby określić możliwości światła, sprawdzając, które interfejsy obsługuje.  Następująca metoda wykonuje obsługiwane możliwości każdego światła:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Poniższy kod `Main` w metodzie tworzy każdy typ światła w sekwencji i testuje to światło:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Jak kompilator określa najlepszą implementację

W tym scenariuszu pokazano interfejs podstawowy bez żadnych implementacji. Dodanie metody do `ILight` interfejsu wprowadza nowe zawiłości. Reguły języka regulujące domyślne metody interfejsu minimalizują wpływ na konkretne klasy, które implementują wiele interfejsów pochodnych. Poprawmy oryginalny interfejs za pomocą nowej metody, aby pokazać, jak to zmienia jego użycie. Każda lampka kontrolna może zgłaszać swój stan zasilania jako wartość wyliczoną:

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

Domyślna implementacja nie przyjmuje żadnych uprawnień:

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Te zmiany skompilować czysto, mimo `ExtraFancyLight` że `ILight` deklaruje obsługę interfejsu i `ITimerLight` `IBlinkingLight`interfejsów pochodnych i . Istnieje tylko jeden "najbliższy" implementacji `ILight` zadeklarowane w interfejsie. Każda klasa, która zadeklarowała zastąpienie stanie się jedyną "najbliższą" implementacją. Pokazano przykłady w poprzednich klasach, które przekroczyły członków innych interfejsów pochodnych.

Należy unikać zastępowania tej samej metody w wielu interfejsach pochodnych. W ten sposób tworzy niejednoznaczne wywołanie metody, gdy klasa implementuje zarówno interfejsów pochodnych. Kompilator nie można wybrać jedną lepszą metodę, więc generuje błąd. Na przykład, jeśli `IBlinkingLight` `ITimerLight` zarówno i zaimplementowane zastąpienie `PowerStatus`, `OverheadLight` musiałby podać bardziej szczegółowe zastąpienie. W przeciwnym razie kompilator nie można wybrać między implementacjami w dwóch interfejsów pochodnych. Zazwyczaj można uniknąć tej sytuacji, utrzymując definicje interfejsu małe i koncentruje się na jednej funkcji. W tym scenariuszu każda funkcja światła jest jego własny interfejs; wiele interfejsów są dziedziczone tylko przez klasy.

W tym przykładzie przedstawiono jeden scenariusz, w którym można zdefiniować dyskretne funkcje, które można mieszać w klasy. Deklarujesz dowolny zestaw obsługiwanych funkcji, deklarując, które interfejsy obsługuje klasa. Użycie wirtualnych metod interfejsu domyślnego umożliwia klasom użycie lub zdefiniowanie innej implementacji dla dowolnej lub wszystkich metod interfejsu. Ta funkcja językowa zapewnia nowe sposoby modelowania systemów rzeczywistych, które budujesz. Domyślne metody interfejsu zapewniają bardziej przejrzysty sposób wyrażania powiązanych klas, które mogą łączyć i łączyć różne funkcje przy użyciu wirtualnych implementacji tych możliwości.
