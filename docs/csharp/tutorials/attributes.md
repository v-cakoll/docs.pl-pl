---
title: Atrybuty — C#
description: Dowiedz się, jak działają atrybutów w języku C#.
author: mgroves
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: db6db50ac59e804225bdc11c435fef3d53fa685e
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258614"
---
# <a name="using-attributes-in-c"></a>Przy użyciu atrybutów w języku C# #

Atrybuty zawierają sposobu kojarzenia informacji o kodzie w sposób deklaratywny. Można również dołączyć element wielokrotnego użytku, który może odnosić się do różnych celów.

Należy wziąć pod uwagę `[Obsolete]` atrybutu. Mogą być stosowane do klasy, struktury, metod i konstruktorów. Jego _deklaruje_ czy element jest przestarzały. Następnie jest kompilator języka C#, aby dla tego atrybutu i czynności w odpowiedzi.

W tym samouczku zostanie wprowadzona sposób dodawania atrybutów do kodu, jak utworzyć i używać własnych atrybutów i sposób używania niektórych atrybutów, które są wbudowane w platformy .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne
Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET core. Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.
Windows, Ubuntu Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację. Musisz zainstalować wybrany edytor kodu. Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

## <a name="create-the-application"></a>Tworzenie aplikacji

Teraz, po zainstalowaniu wszystkich narzędzi, Utwórz nową aplikację platformy .NET Core. Aby użyć generator wiersza polecenia, uruchom następujące polecenie w powłoce Ulubione:

`dotnet new console`

To polecenie spowoduje utworzenie podstawowe pliki projektów programu .NET core. Konieczne będzie wykonanie `dotnet restore` można przywrócić zależności niezbędne do kompilowania projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Do wykonania programu, należy użyć `dotnet run`. Powinieneś zobaczyć "Hello, World" dane wyjściowe do konsoli.

## <a name="how-to-add-attributes-to-code"></a>Jak dodać atrybuty do kodu

W języku C#, atrybuty są klas dziedziczących `Attribute` klasy bazowej. Każda klasa, która dziedziczy z `Attribute` może służyć jako sortowania "tag" na inne fragmentów kodu.
Na przykład istnieje atrybut o nazwie `ObsoleteAttribute`. Służy do sygnalizowania, że kod jest przestarzała i nie powinien być już używany. Ten atrybut w klasie, można umieścić na przykład za pomocą nawiasami kwadratowymi.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Należy pamiętać, że gdy nosi nazwę klasy `ObsoleteAttribute`, jest tylko do użycia `[Obsolete]` w kodzie. Jest to Konwencji, występującego języka C#.
Możesz użyć pełnej nazwy `[ObsoleteAttribute]` wybranie opcji.

Kiedy oznaczanie klasy jest przestarzały, jest dobrym pomysłem jest podanie pewnych informacji, aby *Dlaczego* jest przestarzały, i/lub *co* do użycia zamiast kodu. W tym przez przekazanie jako parametr ciągu atrybutu przestarzały.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Ten ciąg jest przekazywany jako argument do `ObsoleteAttribute` konstruktora, tak jak gdyby były zapisywane `var attr = new ObsoleteAttribute("some string")`.

Parametry Konstruktora atrybutu są ograniczone do prostych typów/literałów: `bool, int, double, string, Type, enums, etc` i tablice z tych typów.
Nie używając wyrażenia lub zmienną. Mogą używać parametry pozycyjne i nazwane.

## <a name="how-to-create-your-own-attribute"></a>Jak utworzyć własnego atrybutu

Tworzenie atrybutu jest tak proste, jak dziedziczenie z `Attribute` klasy bazowej.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Za pomocą powyższego, można teraz używać `[MySpecial]` (lub `[MySpecialAttribute]`) jako atrybut w innym miejscu w bazie kodu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atrybuty w bibliotece klas podstawowych platformy .NET, takich jak `ObsoleteAttribute` wyzwolić pewnymi rodzajami zachowań w ramach kompilator. Jednak każdego atrybutu, który tworzysz działa tylko jako metadane i nie powoduje żadnego kodu w ramach klasy atrybutu wykonywana. To Ty podjęcia odpowiednich działań na tych metadanych w innym miejscu w kodzie (omówiona w dalszej części tego samouczka).

Ma problemy tutaj Zwróć uwagę na. Jak wspomniano powyżej, tylko niektóre typy mogą być przekazywane jako argumenty w przypadku używania atrybutów. Jednak podczas tworzenia typu atrybutu, kompilator języka C# nie zatrzymuje tworzenia tych parametrów. W poniższym przykładzie utworzono atrybutu przy użyciu konstruktora, który kompiluje porządku.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Jednak będzie mogła użyć tego konstruktora przy użyciu składni atrybutów.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Powyższe spowoduje błąd kompilatora, np. `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak ograniczyć użycie atrybutu

Atrybuty może służyć w numerze "celów". W powyższych przykładach je w klasach, ale mogą być również używane na:

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
* returnValue
* Struct

Po utworzeniu klasy atrybutu domyślnie C# pozwala używać tego atrybutu na dowolnym docelowe atrybuty możliwe. Jeśli chcesz ograniczyć atrybut do określonych celów, możesz to zrobić za pomocą `AttributeUsageAttribute` na klasie atrybutu. Który ma kliknij prawym przyciskiem myszy, atrybut dla atrybutu!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Jeśli spróbujesz umieść atrybut powyżej w coś, co nie jest klasą lub strukturą otrzymasz błąd kompilatora, np. `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak używać atrybuty dołączane do elementu kodu

Atrybuty pełnić rolę metadanych. Bez niektóre na zewnątrz życie one faktycznie nie spowoduje żadnego efektu.

Aby znaleźć oraz umożliwia korzystanie z atrybutów, [odbicia](../programming-guide/concepts/reflection.md) ogólnie jest wymagana. Czy mogę nie obejmuje odbicia szczegółowe, w tym samouczku, ale podstawowe chodzi o to, że odbicie umożliwia pisanie kodu w języku C#, który sprawdza, czy inny kod.

Na przykład można użyć odbicia, aby uzyskać informacje na temat klasy: 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Które zostanie wydrukowana mniej więcej tak: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Po utworzeniu `TypeInfo` obiektu (lub `MemberInfo`, `FieldInfo`itp), możesz użyć `GetCustomAttributes` metody. Spowoduje to zwrócenie zbiór `Attribute` obiektów.
Można również użyć `GetCustomAttribute` i określić typ atrybutu.

Poniżej przedstawiono przykład użycia `GetCustomAttributes` na `MemberInfo` wystąpienie `MyClass` (który widzieliśmy wcześniej ma `[Obsolete]` atrybutu na nim).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Która będzie drukować do konsoli: `Attribute on MyClass: ObsoleteAttribute`. Spróbuj dodać inne atrybuty do `MyClass`.

Ważne jest, aby pamiętać, że te `Attribute` opóźnieniem wystąpień obiektów. Oznacza to, że ich nie będzie można utworzyć wystąpienia dopóki nie użyjesz `GetCustomAttribute` lub `GetCustomAttributes`.
Są one również uruchomiony za każdym razem. Wywoływanie `GetCustomAttributes` dwa razy w wierszu zwróci dwa różne wystąpienia `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Atrybuty wspólne w bibliotece klas podstawowych (BCL)

Atrybuty są używane przez wiele narzędzi i platform. Rozszerzenie NUnit używa atrybutów, takich jak `[Test]` i `[TestFixture]` które są używane przez moduł uruchamiający NUnit. ASP.NET MVC korzysta z atrybutów, takich jak `[Authorize]` i zapewnia platformę filtr akcji do wykonania odciąż przekrojowe zagadnienia dotyczące działań platformy MVC. [PostSharp](https://www.postsharp.net) używa składni atrybutu, aby umożliwić zorientowanego na aspekt programowania w języku C#.

Poniżej przedstawiono kilka istotnych atrybuty wbudowanych w platformy .NET Core bibliotek klas bazowych:

* `[Obsolete]`. Ten zestaw został użyty w powyższych przykładach i znajduje się `System` przestrzeni nazw. Jest to przydatne do zapewnienia deklaratywne dokumentacji dotyczące zmieniania bazy kodu. Można podać komunikat w postaci ciągu, a inny parametr logiczny może służyć do podwyższania poziomu z ostrzeżenia kompilatora do błędu kompilatora.

* `[Conditional]`. Ten atrybut jest `System.Diagnostics` przestrzeni nazw. Ten atrybut można stosować do metod (lub klas atrybutów). Ciąg musi być przekazane do konstruktora.
Jeśli ciąg który dopasowuje `#define` dyrektywy, następnie wszelkie wywołania tej metody (ale nie metody) zostaną usunięte przez kompilator języka C#. Zazwyczaj służy do debugowania (Diagnostyka).

* `[CallerMemberName]`. Ten atrybut może być używany na parametry i powiązane z nimi `System.Runtime.CompilerServices` przestrzeni nazw. Jest to atrybut, który jest używany, aby wstawić nazwę metody, która wywołuje inną metodę. To jest zwykle używany jako sposób, aby wyeliminować "Magiczna ciągi" podczas implementowania INotifyPropertyChanged w różnych platform tworzenia interfejsu użytkownika. Na przykład:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

W powyższym kodzie, nie trzeba mieć literału `"Name"` ciągu. To może pomóc w uniknięciu błąd pisowni, powiązane błędy i sprawia, że gładsze refaktoryzacji/zmianę.

## <a name="summary"></a>Podsumowanie

Atrybuty Zapewnij deklaratywne moc C#. Ale są formą kodu jako metadane i nie działają samodzielnie.
