---
title: Typy — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
ms.openlocfilehash: 2fec7b5c36173bf4a99b35cc2bf9e3ca26354a11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399743"
---
# <a name="types-c-programming-guide"></a>Typy (Przewodnik programowania w języku C#)

## <a name="types-variables-and-values"></a>Typy, zmienne i wartości

C# jest językiem silnie typizowany. Każda zmienna i stała ma typ, podobnie jak każde wyrażenie, które oblicza wartość. Każdy podpis metody określa typ dla każdego parametru wejściowego i dla wartości zwracanej. Biblioteka klas .NET definiuje zestaw wbudowanych typów numerycznych, a także bardziej złożonych typów reprezentujących szeroką gamę konstrukcji logicznych, takich jak system plików, połączenia sieciowe, kolekcje i tablice obiektów i dat. Typowy program C# używa typów z biblioteki klas, a także typów zdefiniowanych przez użytkownika, które modelują pojęcia specyficzne dla domeny problemowej programu.

Informacje przechowywane w typie mogą zawierać następujące elementy:

- Miejsce do magazynowania, które wymaga zmiennej typu.

- Wartości maksymalne i minimalne, które może reprezentować.

- Elementy członkowskie (metody, pola, zdarzenia itd.), które zawiera.

- Typ podstawowy, z który dziedziczy.

- Lokalizacja, w której pamięć dla zmiennych zostanie przydzielona w czasie wykonywania.

- Rodzaje operacji, które są dozwolone.

Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje, które są wykonywane w kodzie są *bezpieczne typu*. Na przykład jeśli zadeklarować zmienną typu [int](../../language-reference/builtin-types/integral-numeric-types.md), kompilator umożliwia użycie zmiennej w dodatkowo i operacji odejmowania. Jeśli spróbujesz wykonać te same operacje na zmiennej [typu bool](../../language-reference/builtin-types/bool.md), kompilator generuje błąd, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> Deweloperzy C i C++ należy zauważyć, że w języku C#, [bool](../../language-reference/builtin-types/bool.md) nie jest konwertowalny na [int](../../language-reference/builtin-types/integral-numeric-types.md).

Kompilator osadza informacje o typie w pliku wykonywalnym jako metadane. Czas wykonywania języka wspólnego (CLR) używa tych metadanych w czasie wykonywania do dalszego zagwarantowania bezpieczeństwa typów, gdy przydziela i odzyskuje pamięć.

### <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych

Podczas deklarowania zmiennej lub stałej w programie, należy określić jego typ lub użyć [var](../../language-reference/keywords/var.md) słowa kluczowego, aby umożliwić kompilatorowi wywnioskować typ. W poniższym przykładzie przedstawiono niektóre deklaracje zmiennych, które używają zarówno wbudowanych typów numerycznych, jak i złożonych typów zdefiniowanych przez użytkownika:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Typy parametrów metody i wartości zwracane są określone w podpisie metody. Następujący podpis pokazuje metodę, która wymaga [int](../../language-reference/builtin-types/integral-numeric-types.md) jako argument wejściowy i zwraca ciąg:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Po zadeklarowaniu zmiennej nie można jej ponownie zadeklarować przy nowym typie i nie można jej przypisać wartości, która nie jest zgodna z jej zadeklarowanym typem. Na przykład nie można zadeklarować [int,](../../language-reference/builtin-types/integral-numeric-types.md) a następnie `true`przypisać mu wartość logiczną . Jednak wartości mogą być konwertowane na inne typy, na przykład, gdy są one przypisane do nowych zmiennych lub przekazywane jako argumenty metody. *Konwersja typu,* która nie powoduje utraty danych jest wykonywana automatycznie przez kompilator. Konwersja, która może spowodować utratę danych wymaga *rzutowania* w kodzie źródłowym.

Aby uzyskać więcej informacji, zobacz [Konwersje rzutowania i typu](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Typy wbudowane

C# zawiera standardowy zestaw wbudowanych typów liczbowych do reprezentowania liczb całkowitych, wartości zmiennoprzecinkowych, wyrażeń logicznych, znaków tekstowych, wartości dziesiętnych i innych typów danych. Istnieją również wbudowane `string` i `object` typy. Są one dostępne do użycia w dowolnym programie C#. Aby uzyskać pełną listę wbudowanych typów, zobacz [Typy wbudowane](../../language-reference/builtin-types/built-in-types.md).

## <a name="custom-types"></a>Typy niestandardowe

Do tworzenia własnych typów niestandardowych należy użyć konstrukcji [struct](../../language-reference/builtin-types/struct.md), [class](../../language-reference/keywords/class.md), [interface](../../language-reference/keywords/interface.md)i [enum.](../../language-reference/builtin-types/enum.md) Biblioteka klas .NET sama w sobie jest kolekcją typów niestandardowych dostarczonych przez firmę Microsoft, których można używać we własnych aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w dowolnym programie C#. Inne stają się dostępne tylko wtedy, gdy jawnie dodać odwołanie do projektu do zestawu, w którym są zdefiniowane. Po kompilator ma odwołanie do zestawu, można zadeklarować zmienne (i stałe) typów zadeklarowanych w tym zestawie w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [.NET Class Library](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Wspólny system typów

Ważne jest, aby zrozumieć dwa podstawowe punkty dotyczące systemu typów w .NET:

- Popiera zasadę dziedziczenia. Typy mogą pochodzić od innych typów, *zwanych typami podstawowymi*. Typ pochodny dziedziczy (z pewnymi ograniczeniami) metody, właściwości i inne elementy członkowskie typu podstawowego. Typ podstawowy może z kolei pochodzić z innego typu, w którym to przypadku typu pochodnego dziedziczy elementy członkowskie obu typów podstawowych w hierarchii dziedziczenia. Wszystkie typy, w tym wbudowane typy <xref:System.Int32?displayProperty=nameWithType> liczbowe, takie jak (C# keyword: [int](../../language-reference/builtin-types/integral-numeric-types.md) <xref:System.Object?displayProperty=nameWithType> ), pochodzą ostatecznie z jednego typu podstawowego, który jest (C# słowo kluczowe: [obiekt).](../../language-reference/builtin-types/reference-types.md) Ta ujednolicona hierarchia typów nosi nazwę [Common Type System](../../../standard/base-types/common-type-system.md) (CTS). Aby uzyskać więcej informacji na temat dziedziczenia w języku C#, zobacz [Dziedziczenie](../classes-and-structs/inheritance.md).

- Każdy typ w CTS jest zdefiniowany jako *typ wartości* lub *typ odwołania*. Obejmuje to wszystkie typy niestandardowe w bibliotece klas .NET, a także własne typy zdefiniowane przez użytkownika. Typy zdefiniowane przy użyciu słowa kluczowego [struct](../../language-reference/builtin-types/struct.md) są typami wartości; wszystkie wbudowane typy liczbowe `structs`są . Typy zdefiniowane przy użyciu słowa kluczowego [klasy](../../language-reference/keywords/class.md) są typami odwołań. Typy odwołań i typy wartości mają różne reguły czasu kompilacji i różne zachowanie w czasie wykonywania.

Na poniższej ilustracji przedstawiono relację między typami wartości a typami odwołań w cts.

Na poniższej ilustracji przedstawiono typy wartości i typy odwołań w cts:

![Zrzut ekranu przedstawiający typy wartości CTS i typy odwołań.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Widać, że najczęściej używane typy są zorganizowane <xref:System> w przestrzeni nazw. Jednak obszar nazw, w którym typ jest zawarty, nie ma związku z tym, czy jest typem wartości, czy typem odwołania.

### <a name="value-types"></a>Typy wartości

Typy wartości pochodzą <xref:System.ValueType?displayProperty=nameWithType>z , <xref:System.Object?displayProperty=nameWithType>który pochodzi od . Typy, które <xref:System.ValueType?displayProperty=nameWithType> pochodzą z mają specjalne zachowanie w CLR. Zmienne typu wartości bezpośrednio zawierają ich wartości, co oznacza, że pamięć jest przydzielana w linii w dowolnym kontekście zadeklarowana zmienna. Nie ma oddzielnej alokacji sterty lub obciążenia wyrzucania elementów bezużytecznych dla zmiennych typu wartości.

Istnieją dwie kategorie typów wartości: [struct](../../language-reference/builtin-types/struct.md) i [wyliczenie](../../language-reference/builtin-types/enum.md).

Wbudowane typy liczbowe są struktury i mają właściwości i metody, które można uzyskać dostęp:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ale deklarujesz i przypisujesz do nich wartości tak, jakby były prostymi typami nieagregowanymi:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Typy wartości są *zapieczętowane,* co oznacza, na przykład, <xref:System.Int32?displayProperty=nameWithType>że nie można wyprowadzić typu z , i nie można zdefiniować struktury dziedziczyć z dowolnej klasy zdefiniowanej przez użytkownika lub struktury, ponieważ struktura może dziedziczyć tylko z <xref:System.ValueType?displayProperty=nameWithType>. Jednak struktura może zaimplementować jeden lub więcej interfejsów. Można rzutować typ struktury do dowolnego typu interfejsu, który implementuje; powoduje to, że operacja *bokserska* zawijać strukturę wewnątrz obiektu typu odwołania na zarządzanym stosie. Operacje bokserskie występują po przekazaniu typu <xref:System.Object?displayProperty=nameWithType> wartości do metody, która przyjmuje lub dowolny typ interfejsu jako parametr wejściowy. Aby uzyskać więcej informacji, zobacz [Boks i Unboxing](./boxing-and-unboxing.md).

Słowo kluczowe [struct](../../language-reference/builtin-types/struct.md) służy do tworzenia własnych typów wartości niestandardowych. Zazwyczaj struktura jest używana jako kontener dla małego zestawu powiązanych zmiennych, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Aby uzyskać więcej informacji na temat struktur, zobacz [Typy struktury](../../language-reference/builtin-types/struct.md). Aby uzyskać więcej informacji na temat typów wartości, zobacz [Typy wartości](../../language-reference/builtin-types/value-types.md).

Inną kategorią typów wartości jest [wyliczenie](../../language-reference/builtin-types/enum.md). Wyliczenie definiuje zestaw nazwanych stałych całkowitych. Na przykład <xref:System.IO.FileMode?displayProperty=nameWithType> wyliczenie w bibliotece klas .NET zawiera zestaw nazwanych stałych liczb całkowitych, które określają sposób otwierania pliku. Jest on zdefiniowany w sposób pokazany w poniższym przykładzie:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

Stała `System.IO.FileMode.Create` ma wartość 2. Jednak nazwa jest znacznie bardziej znaczące dla ludzi czytania kodu źródłowego, i z tego powodu lepiej jest używać wyliczenia zamiast stałych liczb literału. Aby uzyskać więcej informacji, zobacz <xref:System.IO.FileMode?displayProperty=nameWithType>.

Wszystkie wyliczenia <xref:System.Enum?displayProperty=nameWithType>dziedziczą <xref:System.ValueType?displayProperty=nameWithType>, który dziedziczy z . Wszystkie reguły, które mają zastosowanie do struktur, mają również zastosowanie do wyliczeń. Aby uzyskać więcej informacji na temat wyliczenia, zobacz [Typy wyliczania](../../language-reference/builtin-types/enum.md).

### <a name="reference-types"></a>Typy odwołań

Typ zdefiniowany jako [klasa,](../../language-reference/keywords/class.md) [delegat,](../../language-reference/builtin-types/reference-types.md)tablica lub [interfejs](../../language-reference/keywords/interface.md) jest *typem odwołania.* W czasie wykonywania, gdy deklarujesz zmienną typu odwołania, zmienna zawiera wartość [null,](../../language-reference/keywords/null.md) dopóki jawnie nie utworzysz obiektu przy `new`użyciu [nowego](../../language-reference/operators/new-operator.md) operatora lub przypiszesz mu obiekt, który został utworzony w innym miejscu za pomocą , jak pokazano w poniższym przykładzie:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Interfejs musi zostać zainicjowany wraz z obiektem klasy, który implementuje go. Jeśli `MyClass` implementuje `IMyInterface`, należy `IMyInterface` utworzyć wystąpienie, jak pokazano w poniższym przykładzie:

```csharp
IMyInterface iface = new MyClass();
```

Po utworzeniu obiektu pamięć jest przydzielana na zarządzanym stosie, a zmienna przechowuje tylko odwołanie do lokalizacji obiektu. Typy na zarządzanym stercie wymagają obciążenie zarówno, gdy są przydzielane i gdy są one odzyskane przez funkcje automatycznego zarządzania pamięcią CLR, który jest znany jako *wyrzucania elementów bezużytecznych*. Jednak wyrzucanie elementów bezużytecznych jest również wysoce zoptymalizowane, a w większości scenariuszy nie tworzy problemu z wydajnością. Aby uzyskać więcej informacji na temat wyrzucania elementów bezużytecznych, zobacz [Automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md).

Wszystkie tablice są typy odwołań, nawet jeśli ich elementy są typy wartości. Tablice niejawnie pochodzą <xref:System.Array?displayProperty=nameWithType> z klasy, ale deklarujesz je i używasz z uproszczoną składnią dostarczoną przez C#, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Typy odwołań w pełni obsługują dziedziczenie. Podczas tworzenia klasy, można dziedziczyć z dowolnego innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowane](../../language-reference/keywords/sealed.md), a inne klasy można dziedziczyć z klasy i zastąpić metody wirtualne. Aby uzyskać więcej informacji na temat tworzenia własnych klas, zobacz [Klasy i struktury](../classes-and-structs/index.md). Aby uzyskać więcej informacji na temat dziedziczenia i metod wirtualnych, zobacz [Dziedziczenie](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Typy wartości literału

W języku C#wartości literału otrzymują typ z kompilatora. Można określić sposób wpisywania literału numerycznego, dołączając literę na końcu numeru. Na przykład, aby określić, że wartość 4,56 powinna być traktowana jako float, dołącz `4.56f`"f" lub "F" po numerze: . Jeśli żadna litera nie zostanie dołączona, kompilator wywnioskuje typ literału. Aby uzyskać więcej informacji o typach, które można określić za pomocą sufiksów liter, zobacz [Typy liczbowe integralne](../../language-reference/builtin-types/integral-numeric-types.md) i [Numeryczne zmiennoprzecinkowe](../../language-reference/builtin-types/floating-point-numeric-types.md).

Ponieważ literały są wpisywane, a <xref:System.Object?displayProperty=nameWithType>wszystkie typy pochodzą ostatecznie z , można napisać i skompilować kod, taki jak:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Typy ogólne

Typ może być zadeklarowany z co najmniej jeden *parametr typu,* które służą jako symbol zastępczy dla rzeczywistego typu *(typ betonu),* który kod klienta zapewni podczas tworzenia wystąpienia typu. Takie typy są nazywane *typami rodzajowymi*. Na przykład typ <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .NET ma jeden parametr typu, który zgodnie z konwencją otrzymuje nazwę *T*. Podczas tworzenia wystąpienia typu należy określić typ obiektów, które będzie zawierać na przykład ciąg:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Użycie parametru type umożliwia ponowne użycie tej samej klasy do przechowywania dowolnego typu elementu, bez konieczności konwertowania każdego elementu na [obiekt.](../../language-reference/builtin-types/reference-types.md) Ogólne klasy kolekcji są nazywane *kolekcje silnie typizowane,* ponieważ kompilator zna określony typ elementów kolekcji i może wywołać błąd w `stringList` czasie kompilacji, jeśli na przykład spróbujesz dodać liczbę całkowitą do obiektu w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [Generyk .](../generics/index.md)

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Typy niejawne, typy anonimowe i wartości nullable

Jak wspomniano wcześniej, można niejawnie wpisywać zmienną lokalną (ale nie członków klasy) za pomocą [var](../../language-reference/keywords/var.md) słowa kluczowego. Zmienna nadal odbiera typ w czasie kompilacji, ale typ jest dostarczany przez kompilator. Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../classes-and-structs/implicitly-typed-local-variables.md).

W niektórych przypadkach jest niewygodne, aby utworzyć nazwany typ dla prostych zestawów powiązanych wartości, które nie mają zamiaru przechowywać lub przekazać poza granicami metody. W tym celu można utworzyć *typy anonimowe.* Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../classes-and-structs/anonymous-types.md).

Zwykłe typy wartości nie mogą mieć wartości [null](../../language-reference/keywords/null.md). Można jednak utworzyć typy wartości nullable `?` przez umieszczenie po typie. Na przykład `int?` jest `int` typem, który może mieć wartość [null](../../language-reference/keywords/null.md). Typy wartości null są wystąpieniami ogólnego <xref:System.Nullable%601?displayProperty=nameWithType>typu struktury . Typy wartości null są szczególnie przydatne podczas przekazywania danych do i z baz danych, w których wartości liczbowe mogą być null. Aby uzyskać więcej informacji, zobacz [Typy wartości nullable](../../language-reference/builtin-types/nullable-value-types.md).

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Rzutowanie i konwersje typów](./casting-and-type-conversions.md)

- [Konwersja boxing i konwersja unboxing](./boxing-and-unboxing.md)

- [Używanie typu dynamicznego](./using-type-dynamic.md)

- [Typy wartości](../../language-reference/builtin-types/value-types.md)

- [Typy odwołań](../../language-reference/keywords/reference-types.md)

- [Klasy i struktury](../classes-and-structs/index.md)

- [Typy anonimowe](../classes-and-structs/anonymous-types.md)

- [Typy ogólne](../generics/index.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../index.md)
- [Konwersja typów danych XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Typy całonowe](../../language-reference/builtin-types/integral-numeric-types.md)
