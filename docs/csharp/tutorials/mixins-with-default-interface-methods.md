---
title: Tworzenie typów domieszki przy użyciu domyślnych metod interfejsu
description: Przy użyciu domyślnych elementów członkowskich interfejsu można rozciągnąć interfejsy z opcjonalnymi implementacjami domyślnymi dla realizatorów.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: 798413f0071159893de39f3e190a9b2693571bb7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039273"
---
# <a name="tutorial-mix-in-functionality-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Samouczek: mieszanie funkcji podczas tworzenia klas przy użyciu interfejsów z domyślnymi metodami interfejsu

Począwszy od C# 8,0 na platformie .net Core 3,0, można zdefiniować implementację w przypadku deklarowania elementu członkowskiego interfejsu. Ta funkcja udostępnia nowe możliwości, w których można definiować domyślne implementacje funkcji zadeklarowanych w interfejsach. Klasy mogą być wybierane podczas przesłonięcia funkcji, kiedy używać funkcji domyślnych i gdy nie należy deklarować obsługi funkcji dyskretnych.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> * Utwórz interfejsy z implementacjami opisującymi funkcje dyskretne.
> * Utwórz klasy, które używają domyślnych implementacji.
> * Utwórz klasy, które zastępują niektóre lub wszystkie domyślne implementacje.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0. Kompilator C# 8,0 jest dostępny od wersji [Visual Studio 2019, 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowszej.

## <a name="limitations-of-extension-methods"></a>Ograniczenia metod rozszerzających

Jednym ze sposobów implementacji zachowania, które pojawia się jako część interfejsu, jest zdefiniowanie [metod rozszerzających](../programming-guide/classes-and-structs/extension-methods.md) , które zapewniają zachowanie domyślne. Interfejsy deklarują minimalny zestaw elementów członkowskich, zapewniając większą powierzchnię dla każdej klasy, która implementuje ten interfejs. Na przykład metody rozszerzające w <xref:System.Linq.Enumerable> zapewniają implementację dowolnej sekwencji jako źródła zapytania LINQ.

Metody rozszerzające są rozwiązane w czasie kompilacji, przy użyciu zadeklarowanego typu zmiennej. Klasy implementujące interfejs mogą zapewnić lepszą implementację dowolnej metody rozszerzenia. Deklaracje zmiennych muszą być zgodne z typem implementującym, aby umożliwić kompilatorowi wybranie tej implementacji. Gdy typ czasu kompilacji jest zgodny z interfejsem, wywołania metody są rozpoznawane jako Metoda rozszerzenia. Innym problemem z metodami rozszerzania jest to, że te metody są dostępne wszędzie tam, gdzie klasy zawierającej metody rozszerzające są dostępne. Klasy nie mogą deklarować, jeśli powinny lub nie muszą dostarczać funkcji zadeklarowanych w metodach rozszerzających.

Począwszy od C# 8,0, można zadeklarować domyślne implementacje jako metody interfejsu. Następnie każda klasa automatycznie używa implementacji domyślnej. Każda klasa, która może zapewnić lepszą implementację, może przesłonić definicję metody interfejsu lepszym algorytmem. W jednym sensie ta technika jest podobna do sposobu używania [metod rozszerzających](../programming-guide/classes-and-structs/extension-methods.md).

W tym artykule dowiesz się, jak domyślne implementacje interfejsu umożliwiają tworzenie nowych scenariuszy.

## <a name="design-the-application"></a>Projektowanie aplikacji

Weź pod uwagę aplikację Automatyzacja domu. Prawdopodobnie masz wiele różnych typów świateł i wskaźników, które mogą być używane w całej firmie. Każde światło musi obsługiwać interfejsy API, aby je włączyć i wyłączyć oraz zgłosić bieżący stan. Niektóre sygnalizatory i wskaźniki mogą obsługiwać inne funkcje, takie jak:

- Włącz światło, a następnie wyłącz je po upłynięciu czasomierza.
- Miganie światła przez pewien czas.

Niektóre z tych rozszerzonych możliwości mogą być emulowane na urządzeniach, które obsługują minimalny zestaw. Wskazuje to na podanie domyślnej implementacji. W przypadku urządzeń, które mają więcej funkcji wbudowanych, oprogramowanie urządzenia może korzystać z natywnych funkcji. W przypadku innych sygnalizatorów mogą oni wybrać implementację interfejsu i użyć domyślnej implementacji.

Domyślnymi elementami członkowskimi interfejsu jest lepszym rozwiązaniem dla tego scenariusza niż metody rozszerzające. Autorzy klasy mogą kontrolować interfejsy, które wybierają do wdrożenia. Wybrane interfejsy są dostępne jako metody. Ponadto, ponieważ domyślne metody interfejsu są domyślnie wirtualne, metoda wysyłania zawsze wybiera implementację w klasie. 

Utwórzmy kod, aby przedstawić te różnice.

## <a name="create-interfaces"></a>Tworzenie interfejsów

Zacznij od utworzenia interfejsu, który definiuje zachowanie dla wszystkich świateł:

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

W przypadku podstawowego narzutu, armatura uproszczona może zaimplementować ten interfejs, jak pokazano w poniższym kodzie:

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

W tym samouczku kod nie obejmuje urządzeń IoT, ale emuluje te działania przez zapisanie komunikatów do konsoli. Możesz eksplorować kod bez automatyzowania domu.

Następnie zdefiniujemy interfejs dla światła, który może być automatycznie wyłączany po upływie limitu czasu:

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Można dodać podstawową implementację do światła narzutowego, ale lepszym rozwiązaniem jest zmodyfikowanie tej definicji interfejsu w celu udostępnienia domyślnej implementacji `virtual`:

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Po dodaniu tej zmiany Klasa `OverheadLight` może zaimplementować funkcję Timer, deklarując obsługę interfejsu:

```csharp
public class OverheadLight : ITimerLight { }
```

Inny typ oświetlenia może obsługiwać bardziej zaawansowany protokół. Może ona zapewnić własną implementację `TurnOnFor`, jak pokazano w poniższym kodzie:

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

W przeciwieństwie do zastępowania metod klasy wirtualnej, deklaracja `TurnOnFor` w klasie `HalogenLight` nie używa słowa kluczowego `override`. 

## <a name="mix-and-match-capabilities"></a>Możliwości mieszania i dopasowywania

Zalety domyślnych metod interfejsu stają się wyraźniejsze, ponieważ wprowadzasz bardziej zaawansowane możliwości. Używanie interfejsów umożliwia mieszanie i dopasowywanie funkcji. Umożliwia również każdemu autorowi klasy wybór między implementacją domyślną a implementacją niestandardową. Dodajmy interfejs z domyślną implementacją dla migających świateł:

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Domyślna implementacja umożliwia migotanie. Światełko narzutu można dodać czasomierz i migające możliwości przy użyciu domyślnej implementacji:

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Nowy typ światła, `LEDLight` obsługuje zarówno funkcję Timer, jak i funkcję Blink. Ten styl jasny implementuje interfejsy `ITimerLight` i `IBlinkingLight` i przesłania metodę `Blink`:

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

`ExtraFancyLight` może obsługiwać jednocześnie funkcje migotania i czasomierza:

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

Utworzony wcześniej `HalogenLight` nie obsługuje migania. Dlatego nie należy dodawać `IBlinkingLight` do listy obsługiwanych interfejsów.

## <a name="detect-the-light-types-using-pattern-matching"></a>Wykrywanie typów świateł przy użyciu dopasowania wzorca

Następnie Napiszmy kod testowy. Możesz użyć C#funkcji [dopasowania do wzorca](../pattern-matching.md) , aby określić możliwości światła, sprawdzając, które interfejsy obsługuje.  Poniższa metoda korzysta z obsługiwanych funkcji poszczególnych świateł:

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Poniższy kod w metodzie `Main` tworzy każdy typ światła w sekwencji i testy, które są jasne:

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Jak kompilator określa najlepszą implementację

W tym scenariuszu przedstawiono interfejs podstawowy bez żadnych implementacji. Dodanie metody do interfejsu `ILight` wprowadza nowe złożoności. Reguły języka rządzące domyślnymi metodami interfejsu minimalizują wpływ konkretnych klas, które implementują wiele interfejsów pochodnych. Zwiększmy oryginalny interfejs za pomocą nowej metody, aby zobaczyć, jak zmienia się jej użycie. Każdy sygnalizator wskaźnika może zgłosić swój stan mocy jako wartość wyliczaną:

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

Domyślna implementacja zakłada zasilanie AC:

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Te zmiany kompilują się w sposób przejrzysty, mimo że `ExtraFancyLight` deklaruje obsługę interfejsu `ILight` i obu interfejsów pochodnych, `ITimerLight` i `IBlinkingLight`. W interfejsie `ILight` jest zadeklarowana tylko jedna implementacja "najbliższy". Każda klasa, która zadeklarowała przesłonięcie, stanie się jedną "najbliższą" implementacją. Przykłady z poprzednich klas, które overrodeą elementy członkowskie innych interfejsów pochodnych.

Unikaj zastępowania tej samej metody w wielu interfejsach pochodnych. Wykonanie tej operacji tworzy niejednoznaczne wywołanie metody za każdym razem, gdy klasa implementuje oba interfejsy pochodne. Kompilator nie może wybrać jednej lepszej metody, aby wystawić błąd. Na przykład jeśli dla `IBlinkingLight` i `ITimerLight` zaimplementowano przesłonięcie `PowerStatus`, `OverheadLight` musi dostarczyć bardziej szczegółowe przesłonięcie. W przeciwnym razie kompilator nie może wybrać między implementacjami w dwóch interfejsach pochodnych. Zazwyczaj można uniknąć tej sytuacji, zachowując definicje interfejsu jako małe i skoncentrowane na jednej funkcji. W tym scenariuszu każda funkcja światła jest własnym interfejsem; wiele interfejsów jest dziedziczonych tylko przez klasy.

Ten przykład pokazuje jeden scenariusz, w którym można zdefiniować osobne funkcje, które mogą być mieszane w klasy. Deklaruje dowolny zestaw obsługiwanych funkcji, deklarując interfejsy obsługiwane przez klasę. Użycie wirtualnych metod interfejsu wirtualnego umożliwia używanie klas lub Definiowanie innej implementacji dla dowolnych lub wszystkich metod interfejsu. Ta funkcja językowa udostępnia nowe sposoby modelowania kompilowanych systemów rzeczywistych. Domyślne metody interfejsu zapewniają wyraźniejszy sposób wyznaczania pokrewnych klas, które mogą mieszać i odpowiadać różnym funkcjom przy użyciu wirtualnych implementacji tych funkcji.
