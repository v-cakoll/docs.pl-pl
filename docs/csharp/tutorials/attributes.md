---
title: Atrybuty - C#
description: "Dowiedz się, jak działają atrybutów w języku C#."
keywords: ".NET i .NET core C#, atrybutów"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: dad02c64d22fe0f127057202c082680f13261d7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-attributes-in-c"></a>Przy użyciu atrybutów w języku C# #

Atrybuty umożliwiają kojarzenia informacji z kodu w sposób deklaratywnego. Można też podać element wielokrotnego użytku, który może odnosić się do różnych celów.

Należy wziąć pod uwagę `[Obsolete]` atrybutu. Mogą być stosowane do klasy, struktury, metody i konstruktory. On _deklaruje_ czy element jest przestarzały. Następnie jest kompilatora C#, aby dla tego atrybutu i wykonać kilka akcji w odpowiedzi.

W tym samouczku przedstawiono sposób dodawania atrybutów do kodu, tworzenie i używanie własnych atrybutów i sposób użycia niektóre atrybuty, które są wbudowane w oprogramowanie .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne
Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET core. Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.
Można uruchomić tej aplikacji, w systemie Windows, Ubuntu Linux, macOS lub w kontenerze Docker. Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych. Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

## <a name="create-the-application"></a>Tworzenie aplikacji

Teraz, po zainstalowaniu wszystkich narzędzi, należy utworzyć nową aplikację platformy .NET Core. Aby użyć generatora wiersza polecenia, uruchom następujące polecenie w ulubionych powłoki:

`dotnet new console`

To polecenie spowoduje utworzenie podstawowe pliki projektu .NET core. Konieczne będzie wykonanie `dotnet restore` do przywrócenia zależności niezbędne do skompilowania tego projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Do wykonania programu, należy użyć `dotnet run`. Powinien zostać wyświetlony "tekst Hello, World" dane wyjściowe do konsoli.

## <a name="how-to-add-attributes-to-code"></a>Jak dodać atrybuty do kodu

W języku C#, atrybuty klasy, które dziedziczą z `Attribute` klasy podstawowej. Każda klasa, która dziedziczy `Attribute` mogą być używane jako sortowania "tagu" na inne fragmentów kodu.
Na przykład istnieje atrybut o nazwie `ObsoleteAttribute`. Służy to sygnalizuje, że kod jest przestarzały i nie powinien być już używany. Tego atrybutu dla klasy, można umieścić na przykład za pomocą nawiasów kwadratowych.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Należy pamiętać, że podczas tej klasy jest nazywane `ObsoleteAttribute`, jest tylko do użycia `[Obsolete]` w kodzie. Jest to Konwencji, znajdujący się C#.
Można użyć pełnej nazwy `[ObsoleteAttribute]` wybranie opcji.

Oznaczenie klasy jest przestarzały, jest dobrym pomysłem jest dostarczają niektóre informacje, aby *Dlaczego* jest przestarzały, i/lub *co* zamiast tego użyć. W tym przez przekazanie do atrybutu przestarzały parametr typu string.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Ten ciąg jest przekazywany jako argument `ObsoleteAttribute` Konstruktor tak, jakby były zapisywane `var attr = new ObsoleteAttribute("some string")`.

Parametrów konstruktora atrybutu jest ograniczona do typów prostych/literały: `bool, int, double, string, Type, enums, etc` i tablice tych typów.
Nie można wyrażenia lub zmienną. Mogą używać parametrów pozycyjnych lub nazwanego.

## <a name="how-to-create-your-own-attribute"></a>Jak utworzyć własne atrybutu

Tworzenie atrybutu jest tak proste, jak dziedziczenie z `Attribute` klasy podstawowej.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Z powyższych, można teraz używać `[MySpecial]` (lub `[MySpecialAttribute]`) jako atrybut w bazie kodu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atrybuty w bibliotece programu .NET klasy podstawowej, takich jak `ObsoleteAttribute` wyzwolenia niektóre zachowania w ramach kompilatora. Jednak każdego atrybutu, który można utworzyć stanowi tylko metadane i nie powoduje dowolny kod w klasie atrybutu wykonywana. To należy do działania na tych metadanych w kodzie (omówiona w dalszej części tego samouczka).

Brak gotcha tutaj aby Zwróć uwagę na. Jak wspomniano powyżej, tylko niektóre typy mogą być przekazywane jako argumenty, gdy przy użyciu atrybutów. Jednak podczas tworzenia typu atrybutu, kompilator języka C# nie uniemożliwić tworzenie tych parametrów. W poniższym przykładzie utworzono atrybutu przy użyciu konstruktora, który kompiluje się tylko poprawnie.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Jednak nie można używać tego konstruktora z Składnia atrybutu.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Powyższe spowoduje błąd kompilatora, takich jak`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak ograniczyć użycie atrybutu

Atrybuty mogą być używane na liczbie "cele". W powyższym przykładzie pokazano je na klasy, ale może być również używany na:

* Zestaw
* Class
* Konstruktor
* Delegate
* Wyliczenie
* Zdarzenie
* Pole
* GenericParameter
* Interface
* Metoda
* Moduł
* Parametr
* Właściwość
* ReturnValue
* Struct

Po utworzeniu klasy atrybutu domyślnie C# umożliwi można użyć tego atrybutu na dowolnym docelowe atrybuty możliwe. Jeśli chcesz ograniczyć atrybut do niektórych obiektów docelowych, możesz to zrobić za pomocą `AttributeUsageAttribute` w klasie atrybutu. Który ma prawym przyciskiem myszy, atrybut dla atrybutu!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Przy próbie zawiesić powyżej atrybut element, który nie jest klasą lub strukturą, wystąpi błąd kompilatora, takich jak`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak używać atrybuty dołączane do elementu kodu

Atrybuty działają jak metadanych. Bez niektóre na zewnątrz Wymuś ich nie będzie faktycznie żadne dodatkowe czynności.

Aby znaleźć i korzystania z atrybutów, [odbicia](../programming-guide/concepts/reflection.md) jest zwykle potrzebne. I nie będzie obejmować odbicia szczegółowe w tym samouczku, ale jest podstawową koncepcją że odbicia umożliwia pisanie kodu w języku C# badający innego kodu.

Można na przykład użyć odbicia, aby uzyskać informacje o klasie: 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Który będzie wydrukować wyglądać mniej więcej tak:`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Po utworzeniu `TypeInfo` obiektu (lub `MemberInfo`, `FieldInfo`itp), można użyć `GetCustomAttributes` metody. Spowoduje to zwrócenie Kolekcja `Attribute` obiektów.
Można również użyć `GetCustomAttribute` i określ typu atrybutu.

Oto przykład użycia `GetCustomAttributes` na `MemberInfo` wystąpienie `MyClass` (który wcześniej widzieliśmy ma `[Obsolete]` atrybutu na nim).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Drukujący do konsoli: `Attribute on MyClass: ObsoleteAttribute`. Spróbuj dodać inne atrybuty do `MyClass`.

Należy zauważyć, że te `Attribute` są one tworzone opóźnieniem. Oznacza to, że ich nie można utworzyć wystąpienia dopóki nie użyjesz `GetCustomAttribute` lub `GetCustomAttributes`.
Są one również utworzone zawsze. Wywoływanie `GetCustomAttributes` dwa razy pod rząd zwróci dwa różne wystąpienia `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Atrybuty wspólne biblioteki klasy podstawowej (BCL)

Atrybuty są używane przez wiele narzędzi i platform. NUnit używa atrybutów, takich jak `[Test]` i `[TestFixture]` używanych przez moduł uruchamiający NUnit. ASP.NET MVC używa atrybutów, takich jak `[Authorize]` i zapewnia framework filtr akcji do wykonania dotyczy kompleksowymi akcjami MVC. [PostSharp](https://www.postsharp.net) używa składni atrybutu aby umożliwić aspekt zorientowane programowania w języku C#.

Poniżej przedstawiono kilka istotnych atrybuty wbudowane w oprogramowanie .NET Core biblioteki klasy podstawowej:

* `[Obsolete]`. Ten zestaw został użyty w powyższych przykładach i znajduje się `System` przestrzeni nazw. Warto zapewniają deklaratywne dokumentację dotyczącą zmieniania bazy kodu. Można podać komunikat w postaci ciągu i inny parametr logiczna może służyć do eskalować z ostrzeżenie kompilatora błąd kompilatora.

* `[Conditional]`. Ten atrybut jest w `System.Diagnostics` przestrzeni nazw. Ten atrybut można stosować do metody (lub klas atrybutów). Należy podać ciąg do konstruktora.
Jeśli ciąg który dopasowań `#define` dyrektywy, następnie wszelkie wywołania tej metody (ale nie metody) zostaną usunięte przez kompilator języka C#. Zazwyczaj jest to używany do debugowania (Diagnostyka).

* `[CallerMemberName]`. Ten atrybut może być używany na parametry i życie w `System.Runtime.CompilerServices` przestrzeni nazw. Jest to atrybut, który jest używany do dodania nazwy metody, która jest wywołaniem innej metody. Zazwyczaj używany jako sposobu wyeliminowania "Magiczna ciągów" podczas implementowania interfejsu INotifyPropertyChanged w różnych platform interfejsu użytkownika. Na przykład:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

W powyższym kodzie, nie trzeba mieć literału `"Name"` ciągu. To ułatwia zapobieganie błędów związanych z Literówka i powoduje płynniejszy refaktoryzacji/zmianę.

## <a name="summary"></a>Podsumowanie

Atrybuty Przełącz deklaratywne zasilania C#. Ale są formą kodu jako metadane i nie działać samodzielnie.
