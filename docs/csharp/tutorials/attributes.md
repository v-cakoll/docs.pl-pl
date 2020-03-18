---
title: 'Samouczek: Używanie atrybutów - C #'
description: Dowiedz się, jak działają atrybuty w języku C#.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 24cb7d35a89fda78511dc4ba725b69c5d601a008
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937468"
---
# <a name="use-attributes-in-c"></a>Używanie atrybutów w C\#

Atrybuty umożliwiają kojarzenie informacji z kodem w sposób deklaratywny. Mogą również zapewnić element wielokrotnego użytku, który można zastosować do różnych celów.

Należy `[Obsolete]` wziąć pod uwagę atrybut. Może być stosowany do klas, struktur, metod, konstruktorów i innych. _Deklaruje,_ że element jest przestarzały. Następnie do kompilatora C# szukać tego atrybutu i wykonać niektóre działania w odpowiedzi.

W tym samouczku zostanie wprowadzony sposób dodawania atrybutów do kodu, jak tworzyć i używać własnych atrybutów i jak używać niektórych atrybutów, które są wbudowane w .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne
Musisz skonfigurować komputer do uruchamiania rdzenia .NET. Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download)
Możesz uruchomić tę aplikację na Windows, Ubuntu Linux, macOS lub w kontenerze Platformy Docker.
Musisz zainstalować swój ulubiony edytor kodu. Poniższe opisy używają [kodu Programu Visual Studio,](https://code.visualstudio.com/) który jest edytorem open source, między platformami. Możesz jednak użyć dowolnych narzędzi, które Ci się podobają.

## <a name="create-the-application"></a>Tworzenie aplikacji

Po zainstalowaniu wszystkich narzędzi utwórz nową aplikację .NET Core. Aby użyć generatora wiersza polecenia, wykonaj następujące polecenie w ulubionej skorupie:

`dotnet new console`

To polecenie spowoduje utworzenie plików projektu podstawowego .NET. Należy wykonać, `dotnet restore` aby przywrócić zależności potrzebne do skompilowania tego projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Aby wykonać program, `dotnet run`należy użyć . Powinieneś zobaczyć wyjście "Hello, World" do konsoli.

## <a name="how-to-add-attributes-to-code"></a>Jak dodać atrybuty do kodu

W języku C#atrybuty są `Attribute` klasy, które dziedziczą z klasy podstawowej. Każda klasa, która `Attribute` dziedziczy, może służyć jako rodzaj "tag" na innych fragmentów kodu.
Na przykład istnieje atrybut `ObsoleteAttribute`o nazwie . Służy to do sygnalizowania, że kod jest przestarzały i nie powinien być już używany. Można umieścić ten atrybut na klasie, na przykład za pomocą nawiasów kwadratowych.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Należy zauważyć, że `ObsoleteAttribute`podczas gdy klasa jest `[Obsolete]` wywoływana , jest to konieczne tylko do użycia w kodzie. Jest to konwencja, która c# następuje.
Możesz użyć pełnej `[ObsoleteAttribute]` nazwy, jeśli wybierzesz.

Podczas oznaczania klasy przestarzałe, jest to dobry pomysł, aby podać pewne informacje, *dlaczego* jest przestarzały i / lub *co* użyć zamiast. Wykonaj to, przekazując parametr ciągu do atrybutu Przestarzałe.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Ciąg jest przekazywany jako argument `ObsoleteAttribute` do konstruktora, `var attr = new ObsoleteAttribute("some string")`tak jak byś pisał .

Parametry konstruktora atrybutu są ograniczone do `bool, int, double, string, Type, enums, etc` prostych typów/literałów: i tablic tych typów.
Nie można użyć wyrażenia ani zmiennej. Możesz swobodnie używać parametrów pozycyjnych lub nazwanych.

## <a name="how-to-create-your-own-attribute"></a>Jak utworzyć własny atrybut

Tworzenie atrybutu jest tak proste, `Attribute` jak dziedziczenie z klasy podstawowej.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Z powyższym, mogę `[MySpecial]` teraz `[MySpecialAttribute]`używać (lub ) jako atrybut w innym miejscu w bazie kodu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atrybuty w bibliotece klas `ObsoleteAttribute` podstawowych .NET, takie jak wyzwalanie pewnych zachowań w kompilatorze. Jednak każdy atrybut, który tworzysz działa tylko jako metadane i nie powoduje żadnego kodu w obrębie klasy atrybutu są wykonywane. To do Ciebie, aby działać na tych metadanych w innym miejscu w kodzie (więcej na ten temat w dalszej części samouczka).

Jest tu "gotcha", na który należy uważać. Jak wspomniano powyżej, tylko niektóre typy mogą być przekazywane jako argumenty podczas używania atrybutów. Jednak podczas tworzenia typu atrybutu kompilator Języka C# nie zatrzyma cię przed utworzeniem tych parametrów. W poniższym przykładzie utworzyłem atrybut z konstruktorem, który kompiluje dobrze.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Jednak nie będzie można użyć tego konstruktora ze składnią atrybutu.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Powyższe spowoduje błąd kompilatora, jak`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak ograniczyć użycie atrybutów

Atrybuty mogą być używane na wielu "cele". Powyższe przykłady pokazują je na zajęciach, ale mogą być również używane na:

* Zestaw
* Klasa
* Konstruktor
* Delegate
* Wyliczenie
* Wydarzenie
* Pole
* Parametr ogólny
* Interface
* Metoda
* Moduł
* Parametr
* Właściwość
* Returnvalue
* Struct

Podczas tworzenia klasy atrybutu, domyślnie C# pozwoli Ci użyć tego atrybutu na dowolnym z możliwych obiektów docelowych atrybutów. Jeśli chcesz ograniczyć atrybut do niektórych obiektów docelowych, `AttributeUsageAttribute` możesz to zrobić za pomocą klasy atrybutów. Zgadza się, atrybut na atrybut!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Jeśli spróbujesz umieścić powyższy atrybut na coś, co nie jest klasą lub strukturą, otrzymasz błąd kompilatora, taki jak`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak używać atrybutów dołączonych do elementu kodu

Atrybuty działają jako metadane. Bez jakiejś siły na zewnątrz, w rzeczywistości nic nie zrobią.

Aby znaleźć i działać na atrybuty, [Odbicie](../programming-guide/concepts/reflection.md) jest ogólnie potrzebne. Nie omówię refleksji dogłębnie w tym samouczku, ale podstawową ideą jest to, że Reflection umożliwia pisanie kodu w języku C#, który sprawdza inny kod.

Na przykład można użyć Odbicia, aby uzyskać `using System.Reflection;` informacje o klasie (dodaj na czele kodu):

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

To wydrukuje coś takiego:`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Gdy masz `TypeInfo` obiekt (lub `MemberInfo` `FieldInfo`, , itp.), `GetCustomAttributes` można użyć metody. Spowoduje to zwrócenie `Attribute` kolekcji obiektów.
Można również `GetCustomAttribute` użyć i określić typ atrybutu.

`GetCustomAttributes` Oto przykład użycia na `MemberInfo` wystąpienie `MyClass` (które widzieliśmy wcześniej ma `[Obsolete]` atrybut na nim).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

To będzie drukować `Attribute on MyClass: ObsoleteAttribute`na konsoli: . Spróbuj dodać inne `MyClass`atrybuty do pliku .

Ważne jest, aby pamiętać, że te `Attribute` obiekty są tworzone leniwie. Oznacza to, że nie będą tworzone, dopóki `GetCustomAttribute` nie `GetCustomAttributes`użyjesz lub .
Są one również tworzone za każdym razem. Wywołanie `GetCustomAttributes` dwa razy z rzędu zwróci dwa różne wystąpienia . `ObsoleteAttribute`

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Typowe atrybuty w bibliotece klas podstawowych (BCL)

Atrybuty są używane przez wiele narzędzi i struktur. NUnit używa atrybutów, takich jak `[Test]` i `[TestFixture]` które są używane przez program testowy NUnit. ASP.NET MVC używa `[Authorize]` atrybutów, takich jak i zapewnia struktury filtrowania akcji do wykonywania przekrojowych problemów dotyczących akcji MVC. [PostSharp](https://www.postsharp.net) używa składni atrybutu, aby umożliwić programowanie zorientowane na aspekt w języku C#.

Oto kilka znaczących atrybutów wbudowanych w biblioteki klas podstawowych .NET Core:

* `[Obsolete]`. Ten został użyty w powyższych przykładach i `System` żyje w przestrzeni nazw. Jest to przydatne, aby zapewnić dokumentację deklaratywną dotyczącą zmiany bazy kodu. Komunikat może być dostarczony w postaci ciągu, a inny parametr logiczny może służyć do eskalacji z ostrzeżenia kompilatora do błędu kompilatora.

* `[Conditional]`. Ten atrybut znajduje `System.Diagnostics` się w obszarze nazw. Ten atrybut można zastosować do metod (lub klas atrybutów). Należy przekazać ciąg do konstruktora.
Jeśli ten ciąg nie `#define` pasuje do dyrektywy, a następnie wszystkie wywołania tej metody (ale nie sama metoda) zostaną usunięte przez kompilator C#. Zazwyczaj jest to używane do debugowania (diagnostyki) celów.

* `[CallerMemberName]`. Ten atrybut może służyć do parametrów i `System.Runtime.CompilerServices` mieszka w przestrzeni nazw. Jest to atrybut, który jest używany do wstrzykiwania nazwę metody, która jest wywoływanie innej metody. Jest to zazwyczaj używane jako sposób na wyeliminowanie "magiczne ciągi" podczas implementowania INotifyPropertyChanged w różnych ramach interfejsu użytkownika. Przykład:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

W powyższym kodzie nie trzeba mieć `"Name"` ciąg literału. Może to pomóc w zapobieganiu błędom związanym z literówką, a także zapewnia płynniejsze refaktoryzacji / zmiany nazwy.

## <a name="summary"></a>Podsumowanie

Atrybuty wprowadzają deklaratywne moc do Języka C#, ale są one meta-data formy kodu i nie działają same.
