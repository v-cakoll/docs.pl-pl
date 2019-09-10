---
title: AttributesC#
description: Dowiedz się, jak C#działają atrybuty.
author: mgroves
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 0037e8b2c5f50d1b8d0a950743f6eeb9145df414
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851002"
---
# <a name="using-attributes-in-c"></a>Używanie atrybutów w C\#

Atrybuty umożliwiają kojarzenie informacji z kodem w sposób deklaratywny. Mogą również dostarczyć element wielokrotnego użytku, który można zastosować do różnych elementów docelowych.

Weź pod uwagę atrybut. `[Obsolete]` Może być stosowana do klas, struktur, metod, konstruktorów i innych. _Deklaruje_ , że element jest przestarzały. Następnie do C# kompilatora, aby wyszukać ten atrybut, i wykonaj pewne działania w odpowiedzi.

W tym samouczku dowiesz się, jak dodawać atrybuty do kodu, jak tworzyć i używać własnych atrybutów oraz jak używać niektórych atrybutów wbudowanych w platformę .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne
Musisz skonfigurować maszynę do uruchamiania programu .NET Core. Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) .
Możesz uruchomić tę aplikację w systemie Windows, Ubuntu Linux, macOS lub w kontenerze platformy Docker. Musisz zainstalować swój ulubiony Edytor kodu. Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/) , czyli edytor Międzyplatformowy. Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.

## <a name="create-the-application"></a>Tworzenie aplikacji

Teraz, po zainstalowaniu wszystkich narzędzi, Utwórz nową aplikację platformy .NET Core. Aby użyć generatora wiersza polecenia, wykonaj następujące polecenie w ulubionym powłoce:

`dotnet new console`

To polecenie spowoduje utworzenie plików projektu programu podstawowe .NET Core. Należy wykonać `dotnet restore` , aby przywrócić zależności wymagane do skompilowania projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Aby wykonać program, użyj `dotnet run`. Do konsoli powinny być widoczne dane wyjściowe "Hello, World".

## <a name="how-to-add-attributes-to-code"></a>Jak dodać atrybuty do kodu

W C#programie atrybuty są klasy dziedziczące z `Attribute` klasy bazowej. Każda klasa, która dziedziczy `Attribute` z, może być używana jako "tag" w innych fragmentach kodu.
Na przykład istnieje atrybut o nazwie `ObsoleteAttribute`. Jest to używane do sygnalizowania, że kod jest przestarzały i nie powinien już być używany. Ten atrybut można umieścić w klasie, na przykład za pomocą nawiasów kwadratowych.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Należy pamiętać, że `ObsoleteAttribute` `[Obsolete]` w przypadku wywołania klasy jest to konieczne tylko w kodzie. Jest to Konwencja C# następująca.
Jeśli wybierzesz, możesz użyć `[ObsoleteAttribute]` pełnej nazwy.

Gdy oznaczasz przestarzałą klasę, dobrym pomysłem jest podanie pewnych informacji, *dlaczego* są przestarzałe i/lub *czego* można użyć zamiast tego. W tym celu należy przekazać parametr ciągu do przestarzałego atrybutu.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Ciąg jest przesyłany jako argument do `ObsoleteAttribute` konstruktora, podobnie jak w przypadku pisania. `var attr = new ObsoleteAttribute("some string")`

Parametry konstruktora atrybutu są ograniczone do typów prostych/literałów: `bool, int, double, string, Type, enums, etc` i tablic tych typów.
Nie można użyć wyrażenia ani zmiennej. Możesz korzystać z parametrów pozycyjnych lub nazwanych.

## <a name="how-to-create-your-own-attribute"></a>Jak utworzyć własny atrybut

Tworzenie atrybutu jest tak proste jak dziedziczenie z `Attribute` klasy podstawowej.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Korzystając z powyższych, można teraz używać `[MySpecial]` (lub `[MySpecialAttribute]`) jako atrybutu w innym miejscu w bazie kodu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atrybuty w bibliotece klas bazowych .NET, `ObsoleteAttribute` takie jak wyzwalanie niektórych zachowań w kompilatorze. Jednak każdy utworzony atrybut działa tylko jako metadane i nie powoduje żadnego kodu w ramach wykonywanej klasy atrybutu. Jest to konieczne do działania na tych metadanych w innym miejscu w kodzie (więcej informacji na ten temat znajduje się w dalszej części tego samouczka).

Tutaj znajdziesz "Gotcha". Jak wspomniano powyżej, tylko niektóre typy mogą być przekazane jako argumenty przy użyciu atrybutów. Jednak podczas tworzenia typu atrybutu C# kompilator nie zatrzymuje tworzenia tych parametrów. W poniższym przykładzie został utworzony atrybut z konstruktorem, który kompiluje się w prawidłowy sposób.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Nie będzie jednak można używać tego konstruktora z składnią atrybutu.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Powyższe spowoduje wystąpienie błędu kompilatora`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak ograniczyć użycie atrybutów

Atrybuty mogą być używane dla wielu elementów "targets". Powyższe przykłady pokazują je na klasach, ale mogą być również używane w:

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

Podczas tworzenia klasy atrybutu domyślnie, C# będzie można używać tego atrybutu na dowolnym możliwym celu atrybutu. Jeśli chcesz ograniczyć atrybut do określonych elementów docelowych, możesz to zrobić za pomocą `AttributeUsageAttribute` klasy na klasie atrybutów. To prawo, atrybut atrybutu!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Jeśli spróbujesz umieścić powyższy atrybut w elemencie, który nie jest klasą lub strukturą, zostanie wyświetlony błąd kompilatora, taki jak`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak używać atrybutów dołączonych do elementu kodu

Atrybuty pełnią rolę metadanych. Bez żadnej siły biernej nie będą w rzeczywistości same.

Aby znaleźć i korzystać z atrybutów, [odbicie](../programming-guide/concepts/reflection.md) jest zwykle konieczne. W tym samouczku nie są pokryte szczegółowe dane dotyczące odbicia, ale podstawowym pomysłem jest to, że odbicie C# umożliwia pisanie kodu w programie, który sprawdza inny kod.

Na przykład możesz użyć odbicia, aby uzyskać informacje o klasie (Dodaj `using System.Reflection;` na początku kodu): 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Zostanie wydrukowany następujący element:`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Gdy masz `TypeInfo` obiekt ( `MemberInfo`lub, `FieldInfo`itp.), możesz użyć `GetCustomAttributes` metody. Spowoduje to zwrócenie kolekcji `Attribute` obiektów.
Można również użyć `GetCustomAttribute` i określić typ atrybutu.

Oto `GetCustomAttributes` przykład użycia `MemberInfo` w przypadku wystąpienia dla `MyClass` (które zostało `[Obsolete]` wcześniej umieszczone we wcześniejszej części atrybutu).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Drukowanie do konsoli programu: `Attribute on MyClass: ObsoleteAttribute`. Spróbuj dodać inne atrybuty do `MyClass`.

Należy pamiętać, że te `Attribute` obiekty są tworzone w opóźnieniem. Oznacza to, że nie będą one tworzone do momentu `GetCustomAttribute` użycia `GetCustomAttributes`lub.
Są one również tworzone za każdym razem. Dwukrotne wywołanie `GetCustomAttributes` w wierszu zwróci dwa różne `ObsoleteAttribute`wystąpienia.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Typowe atrybuty w bibliotece klas bazowych (BCL)

Atrybuty są używane przez wiele narzędzi i platform. NUnit używa atrybutów takich `[Test]` jak `[TestFixture]` i, które są używane przez moduł uruchamiający testy NUnit. ASP.NET MVC używa atrybutów, `[Authorize]` takich jak i, udostępnia strukturę filtru akcji, aby wykonywać problemy z wycinaniem w ramach akcji MVC. [PostSharp](https://www.postsharp.net) używa składni atrybutów, aby umożliwić programowanie zorientowane na podstawie aspektów w programie C#.

Oto kilka istotnych atrybutów wbudowanych w podstawowe biblioteki klas platformy .NET Core:

* `[Obsolete]`. Ta nazwa została użyta w powyższych przykładach i znajduje `System` się w przestrzeni nazw. Przydatne jest dostarczanie deklaratywnej dokumentacji dotyczącej zmiany bazy kodu. Komunikat można podać w postaci ciągu i można użyć innego parametru Boolean do eskalacji z ostrzeżenia kompilatora do błędu kompilatora.

* `[Conditional]`. Ten atrybut znajduje się w `System.Diagnostics` przestrzeni nazw. Ten atrybut może być stosowany do metod (lub klas atrybutów). Należy przekazać ciąg do konstruktora.
Jeśli ten ciąg nie pasuje `#define` do dyrektywy, wówczas wszystkie wywołania tej metody (ale nie sama metoda) zostaną usunięte przez C# kompilator. Zwykle jest to używane na potrzeby debugowania (Diagnostyka).

* `[CallerMemberName]`. Tego atrybutu można używać w parametrach i w `System.Runtime.CompilerServices` przestrzeni nazw. Jest to atrybut, który jest używany do wstrzykiwania nazwy metody wywołującej inną metodę. Jest to zwykle używane w celu wyeliminowania "magicznych ciągów" podczas implementowania INotifyPropertyChanged w różnych strukturach interfejsu użytkownika. Na przykład:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

W powyższym kodzie nie trzeba mieć ciągu literału `"Name"` . Może to ułatwić zapobieganie błędom związanym z literówkami oraz płynne Refaktoryzacja/zmiana nazwy.

## <a name="summary"></a>Podsumowanie

Atrybuty zapewniają deklaratywną moc C#, ale są one formą metadanych kodu i nie działają samodzielnie.
