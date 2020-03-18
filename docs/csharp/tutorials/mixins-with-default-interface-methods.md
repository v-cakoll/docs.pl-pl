---
title: Tworzenie typów mixin przy użyciu domyślnych metod interfejsu
description: Za pomocą domyślnych elementów członkowskich interfejsu można rozszerzyć interfejsy z opcjonalnych implementacji domyślnych dla realizatorów.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: aaf8d34e27c9c56d95560656eb7a7b24b152c053
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240109"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Samouczek: Mieszaj funkcje podczas tworzenia klas przy użyciu interfejsów z domyślnymi metodami interfejsu

Począwszy od języka C# 8.0 w platformie .NET Core 3.0, można zdefiniować implementację podczas deklarowania członka interfejsu. Ta funkcja zapewnia nowe możliwości, w których można zdefiniować implementacje domyślne dla funkcji zadeklarowanych w interfejsach. Klasy można wybrać, kiedy zastąpić funkcje, kiedy używać funkcji domyślnych i kiedy nie zadeklarować obsługę funkcji dyskretnych.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> * Tworzenie interfejsów z implementacjami, które opisują funkcje dyskretne.
> * Tworzenie klas, które używają implementacji domyślnych.
> * Tworzenie klas, które zastępują niektóre lub wszystkie implementacje domyślne.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0. Kompilator Języka C# 8.0 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [sdk .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core) lub nowszy.

## <a name="limitations-of-extension-methods"></a>Ograniczenia metod rozszerzenia

Jednym ze sposobów zaimplementowania zachowania, które pojawia się jako część interfejsu jest zdefiniowanie [metod rozszerzenia,](../programming-guide/classes-and-structs/extension-methods.md) które zapewniają zachowanie domyślne. Interfejsy deklarują minimalny zestaw elementów członkowskich, zapewniając jednocześnie większą powierzchnię dla każdej klasy, która implementuje ten interfejs. Na przykład metody rozszerzenia <xref:System.Linq.Enumerable> w podać implementację dla dowolnej sekwencji, które mają być źródłem kwerendy LINQ.

Metody rozszerzenia są rozpoznawane w czasie kompilacji przy użyciu zadeklarowanego typu zmiennej. Klasy implementują interfejs może zapewnić lepszą implementację dla każdej metody rozszerzenia. Deklaracje zmiennych muszą być zgodne z typem implementacji, aby umożliwić kompilatorowi wybranie tej implementacji. Gdy typ czasu kompilacji pasuje do interfejsu, wywołania metody rozpoznać do metody rozszerzenia. Innym problemem z metod rozszerzenia jest, że metody te są dostępne wszędzie tam, gdzie klasa zawierająca metody rozszerzenia jest dostępna. Klasy nie mogą zadeklarować, czy powinny lub nie powinny one zawierać funkcje zadeklarowane w metodach rozszerzenia.

Począwszy od języka C# 8.0, można zadeklarować implementacje domyślne jako metody interfejsu. Następnie każda klasa automatycznie używa domyślnej implementacji. Każda klasa, która może zapewnić lepszą implementację można zastąpić definicji metody interfejsu z lepszym algorytmem. W pewnym sensie ta technika brzmi podobnie do tego, jak można użyć [metod rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md).

W tym artykule dowiesz się, jak domyślne implementacje interfejsu włączyć nowe scenariusze.

## <a name="design-the-application"></a>Projektowanie aplikacji

Należy wziąć pod uwagę aplikację automatyki domowej. Prawdopodobnie masz wiele różnych rodzajów świateł i wskaźników, które mogą być używane w całym domu. Każde światło musi obsługiwać interfejsy API, aby je włączyć i wyłączyć oraz zgłosić bieżący stan. Niektóre światła i wskaźniki mogą obsługiwać inne funkcje, takie jak:

- Wyłącz światło, a następnie wyłącz ją po upływie timera.
- Mrugaj światłem przez pewien czas.

Niektóre z tych rozszerzonych możliwości mogą być emulowane w urządzeniach obsługujących minimalny zestaw. Oznacza to, że dostarczanie domyślnej implementacji. W przypadku tych urządzeń, które mają więcej wbudowanych możliwości, oprogramowanie urządzenia będzie korzystać z możliwości natywnych. W przypadku innych świateł mogą zdecydować się na zaimplementowanie interfejsu i użycie domyślnej implementacji.

Domyślne elementy członkowskie interfejsu jest lepszym rozwiązaniem dla tego scenariusza niż metody rozszerzenia. Autorzy klas mogą kontrolować, które interfejsy zdecydują się zaimplementować. Te interfejsy, które wybierają, są dostępne jako metody. Ponadto ponieważ domyślne metody interfejsu są domyślnie wirtualne, wywołanie metody zawsze wybiera implementację w klasie.

Utwórzmy kod, aby zademonstrować te różnice.

## <a name="create-interfaces"></a>Tworzenie interfejsów

Zacznij od utworzenia interfejsu, który definiuje zachowanie dla wszystkich świateł:

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Podstawowe narzutowe oprawy oświetleniowe może zaimplementować ten interfejs, jak pokazano w następującym kodzie:

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

W tym samouczku kod nie dysk urządzeń IoT, ale emuluje te działania, pisząc wiadomości do konsoli. Możesz eksplorować kod bez automatyzowania domu.

Następnie zdefiniujmy interfejs dla światła, które można automatycznie wyłączyć po upływie czasu:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Można dodać podstawową implementację do światła narzutowego, ale lepszym rozwiązaniem `virtual` jest zmodyfikowanie tej definicji interfejsu w celu zapewnienia domyślnej implementacji:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Dodając tę zmianę, `OverheadLight` klasa może zaimplementować funkcję czasoatora, deklarując obsługę interfejsu:

```csharp
public class OverheadLight : ITimerLight { }
```

Inny typ światła może obsługiwać bardziej zaawansowany protokół. Może zapewnić własną `TurnOnFor`implementację dla , jak pokazano w poniższym kodzie:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

W przeciwieństwie do zastępowania metod `TurnOnFor` klasy `HalogenLight` wirtualnej, `override` deklaracja w klasie nie używa słowa kluczowego.

## <a name="mix-and-match-capabilities"></a>Mieszanie i dopasowywanie możliwości

Zalety domyślnych metod interfejsu stają się wyraźniejsze, gdy wprowadzasz bardziej zaawansowane możliwości. Korzystanie z interfejsów umożliwia mieszanie i dopasowywanie możliwości. Umożliwia również każdemu autorowi klasy wybór między implementacją domyślną a implementacją niestandardową. Dodajmy interfejs z domyślną implementacją migającego światła:

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Domyślna implementacja umożliwia miganie dowolnego światła. Kontrolka narzutowa może dodać funkcje czasownika i migania przy użyciu domyślnej implementacji:

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Nowy typ światła, `LEDLight` obsługuje zarówno funkcję timera, jak i funkcję migania bezpośrednio. Ten lekki styl implementuje zarówno `ITimerLight` interfejsy, jak i `IBlinkingLight` interfejsy i zastępuje `Blink` metodę:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Może `ExtraFancyLight` obsługiwać zarówno funkcje blink i timer bezpośrednio:

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

`HalogenLight` Utworzony wcześniej nie obsługuje migania. Tak więc nie dodawaj `IBlinkingLight` do listy obsługiwanych interfejsów.

## <a name="detect-the-light-types-using-pattern-matching"></a>Wykrywanie typów świateł przy użyciu dopasowywania wzorców

Następnie napiszmy kod testu. Można użyć funkcji [dopasowywania wzorców](../pattern-matching.md) języka C#, aby określić możliwości światła, sprawdzając, które interfejsy obsługuje.  Następująca metoda korzysta z obsługiwanych możliwości każdego światła:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Następujący kod w `Main` metodzie tworzy każdy typ światła w sekwencji i testów, które światło:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Jak kompilator określa najlepszą implementację

W tym scenariuszu przedstawiono interfejs podstawowy bez żadnych implementacji. Dodawanie metody do `ILight` interfejsu wprowadza nowe złożoności. Reguły języka regulujące domyślne metody interfejsu minimalizują wpływ na konkretne klasy implementujące wiele interfejsów pochodnych. Dodajmy oryginalny interfejs o nową metodę, aby pokazać, jak to zmienia jego użycie. Każda lampka kontrolna może zgłosić swój stan zasilania jako wyliczoną wartość:

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

Domyślna implementacja zakłada zasilanie prądem przemiennym:

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Te zmiany skompilują `ExtraFancyLight` się czysto, mimo że deklaruje `ILight` `ITimerLight` obsługę interfejsu i obu interfejsów pochodnych i `IBlinkingLight`. Istnieje tylko jedna "najbliższa" implementacja `ILight` zadeklarowana w interfejsie. Każda klasa, która zadeklarowała zastąpienie stanie się jedną "najbliższą" implementacją. Zobaczysz przykłady w poprzednich klasach, które overrode członków innych interfejsów pochodnych.

Należy unikać zastępowania tej samej metody w wielu interfejsów pochodnych. W ten sposób tworzy niejednoznaczne wywołanie metody, gdy klasa implementuje oba interfejsy pochodne. Kompilator nie może wybrać jedną lepszą metodę, więc wystawia błąd. Na przykład jeśli `IBlinkingLight` zarówno `ITimerLight` i zaimplementowane `PowerStatus`zastąpienie `OverheadLight` , należy podać bardziej szczegółowe zastąpienia. W przeciwnym razie kompilator nie można wybrać między implementacjami w dwóch interfejsów pochodnych. Zazwyczaj można uniknąć tej sytuacji, utrzymując definicje interfejsu małe i koncentruje się na jednej funkcji. W tym scenariuszu każda możliwość światła jest jego własny interfejs; wiele interfejsów są dziedziczone tylko przez klasy.

W tym przykładzie przedstawiono jeden scenariusz, w którym można zdefiniować funkcje dyskretne, które można mieszać z klasami. Deklarujesz dowolny zestaw obsługiwanych funkcji, deklarując, które interfejsy obsługuje klasa. Użycie wirtualnych metod interfejsu domyślnego umożliwia klasom używanie lub definiowanie innej implementacji dla dowolnej lub wszystkich metod interfejsu. Ta funkcja języka zapewnia nowe sposoby modelowania systemów rzeczywistych, które budujesz. Domyślne metody interfejsu zapewniają jaśniejszy sposób wyrażania powiązanych klas, które mogą mieszać i dopasowywać różne funkcje przy użyciu wirtualnych implementacji tych możliwości.
