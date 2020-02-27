---
title: Typy — C# Przewodnik programowania
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
ms.openlocfilehash: ade2cba857a1a32039f8fd07881f13f63f0dbe1a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628140"
---
# <a name="types-c-programming-guide"></a>Typy (Przewodnik programowania w języku C#)

## <a name="types-variables-and-values"></a>Typy, zmienne i wartości

C#jest językiem o jednoznacznie określonym typie. Każda zmienna i stała ma typ, tak jak każde wyrażenie, którego wynikiem jest wartość. Każdy podpis metody Określa typ dla każdego parametru wejściowego i dla zwracanej wartości. Biblioteka klas .NET definiuje zestaw wbudowanych typów liczbowych, a także bardziej złożonych typów, które reprezentują szeroką gamę konstrukcji logicznych, takich jak system plików, połączenia sieciowe, kolekcje i tablice obiektów oraz daty. Typowy C# program używa typów z biblioteki klas, a także typów zdefiniowanych przez użytkownika, które umożliwiają modelowanie koncepcji specyficznych dla domeny problemu programu.

Informacje przechowywane w typie mogą obejmować następujące elementy:

- Miejsce do magazynowania, którego wymagana jest zmienna typu.

- Wartości maksymalne i minimalne, które może reprezentować.

- Elementy członkowskie (metody, pola, zdarzenia itd.), które zawiera.

- Typ podstawowy, z którego dziedziczy.

- Lokalizacja, w której zostanie przypisana pamięć dla zmiennych w czasie wykonywania.

- Rodzaje operacji, które są dozwolone.

Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje wykonywane w kodzie są *bezpieczne*. Na przykład jeśli deklarujesz zmienną typu [int](../../language-reference/builtin-types/integral-numeric-types.md), kompilator pozwala używać zmiennej w operacjach dodawania i odejmowania. Jeśli spróbujesz wykonać te same operacje na zmiennej typu [bool](../../language-reference/builtin-types/bool.md), kompilator generuje błąd, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> C i C++ deweloperzy, Zauważ, że C#w, [bool](../../language-reference/builtin-types/bool.md) nie jest konwertowany na [int](../../language-reference/builtin-types/integral-numeric-types.md).

Kompilator osadza informacje o typie pliku wykonywalnego jako metadane. Środowisko uruchomieniowe języka wspólnego (CLR) używa tych metadanych w czasie wykonywania, aby zapewnić bezpieczeństwo typów podczas przydzielania i odzyskania pamięci.

### <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych

W przypadku deklarowania zmiennej lub stałej w programie należy określić jej typ lub użyć słowa kluczowego [var](../../language-reference/keywords/var.md) , aby zezwolić kompilatorowi na wnioskowanie typu. W poniższym przykładzie przedstawiono niektóre deklaracje zmiennych, które używają wbudowanych typów liczbowych i złożonych typów zdefiniowanych przez użytkownika:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Typy parametrów metod i zwracanych wartości są określone w podpisie metody. Następujący podpis przedstawia metodę, która wymaga [int](../../language-reference/builtin-types/integral-numeric-types.md) jako argumentu wejściowego i zwraca ciąg:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Po zadeklarowaniu zmiennej nie można jej ponownie zadeklarować przy użyciu nowego typu i nie można przypisać do niej wartości, która nie jest zgodna z zadeklarowanym typem. Na przykład nie można zadeklarować [int](../../language-reference/builtin-types/integral-numeric-types.md) , a następnie przypisać mu wartości logicznej `true`. Jednak wartości mogą być konwertowane na inne typy, na przykład wtedy, gdy są przypisane do nowych zmiennych lub przekazane jako argumenty metody. *Konwersja typu* , która nie powoduje utraty danych, jest wykonywana automatycznie przez kompilator. Konwersja, która może spowodować utratę danych, wymaga *rzutowania* w kodzie źródłowym.

Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Typy wbudowane

C#zawiera standardowy zestaw wbudowanych typów liczbowych reprezentujących liczby całkowite, wartości zmiennoprzecinkowe, wyrażenia logiczne, znaki tekstowe, wartości dziesiętne i inne typy danych. Istnieją również wbudowane typy `string` i `object`. Są one dostępne do użycia w dowolnym C# programie. Aby zapoznać się z pełną listą typów wbudowanych, zobacz [typy wbudowane](../../language-reference/builtin-types/built-in-types.md).

## <a name="custom-types"></a>Typy niestandardowe

Do tworzenia własnych typów niestandardowych służy konstrukcja [struct](../../language-reference/builtin-types/struct.md), [Class](../../language-reference/keywords/class.md), [Interface](../../language-reference/keywords/interface.md)i [enum](../../language-reference/builtin-types/enum.md) . Sama Biblioteka klas .NET jest kolekcją typów niestandardowych dostarczanych przez firmę Microsoft, których można używać w własnych aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w dowolnym C# programie. Inne stają się dostępne tylko wtedy, gdy jawnie dodasz odwołanie do projektu do zestawu, w którym są zdefiniowane. Gdy kompilator ma odwołanie do zestawu, można zadeklarować zmienne (i stałe) typów zadeklarowanych w tym zestawie w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [Biblioteka klas .NET](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Wspólny system typów

Ważne jest, aby zrozumieć dwa podstawowe punkty o systemie typów w programie .NET:

- Obsługuje zasady dziedziczenia. Typy mogą pochodzić od innych typów, nazywanych *typami podstawowymi*. Typ pochodny dziedziczy (z pewnymi ograniczeniami) metody, właściwości i inne elementy członkowskie typu podstawowego. Typ podstawowy może być pochodny od innego typu, w tym przypadku typ pochodny dziedziczy elementy członkowskie obu typów podstawowych w hierarchii dziedziczenia. Wszystkie typy, w tym wbudowane typy liczbowe, takie jak <xref:System.Int32?displayProperty=nameWithType> (C# słowo kluczowe: [int](../../language-reference/builtin-types/integral-numeric-types.md)), pochodzą ostatecznie od pojedynczego typu podstawowego, który jest <xref:System.Object?displayProperty=nameWithType> (C# słowo kluczowe: [Object](../../language-reference/builtin-types/reference-types.md)). Ta ujednolicona hierarchia typów jest nazywana [systemem common Type System](../../../standard/base-types/common-type-system.md) (CTS). Aby uzyskać więcej informacji na temat C#dziedziczenia w programie, zobacz [dziedziczenie](../classes-and-structs/inheritance.md).

- Każdy typ w CTS jest zdefiniowany jako *Typ wartości* lub *typ referencyjny*. Obejmuje to wszystkie niestandardowe typy w bibliotece klas .NET, a także własne typy zdefiniowane przez użytkownika. Typy zdefiniowane za pomocą słowa kluczowego [struct](../../language-reference/builtin-types/struct.md) są typami wartości; wszystkie wbudowane typy liczbowe są `structs`. Typy zdefiniowane za pomocą słowa kluczowego [Class](../../language-reference/keywords/class.md) to typy odwołań. Typy odwołań i typy wartości mają różne reguły czasu kompilacji i inne zachowanie w czasie wykonywania.

Na poniższej ilustracji przedstawiono relacje między typami wartości i typami odwołań w CTS.

Na poniższej ilustracji przedstawiono typy wartości i typy odwołań w CTS:

![Zrzut ekranu pokazujący typy wartości i typy odwołań CTS.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Można zobaczyć, że najczęściej używane typy są zorganizowane w przestrzeni nazw <xref:System>. Jednak przestrzeń nazw, w której znajduje się typ, nie ma żadnego powiązania z tym, czy jest typem wartości czy typem referencyjnym.

### <a name="value-types"></a>Typy wartości

Typy wartości pochodne od <xref:System.ValueType?displayProperty=nameWithType>, które pochodzą z <xref:System.Object?displayProperty=nameWithType>. Typy, które pochodzą od <xref:System.ValueType?displayProperty=nameWithType> mają specjalne zachowanie w środowisku CLR. Zmienne typu wartości bezpośrednio zawierają swoje wartości, co oznacza, że pamięć jest alokowana w dowolnym kontekście, w którym jest zadeklarowana zmienna. Nie ma oddzielnego przydziału sterty lub wyrzucania elementów bezużytecznych dla zmiennych typu wartości.

Istnieją dwie kategorie typów wartości: [struct](../../language-reference/builtin-types/struct.md) i [enum](../../language-reference/builtin-types/enum.md).

Wbudowane typy liczbowe to struktury i mają właściwości i metody, do których można uzyskać dostęp:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ale deklaruję i przypisujesz wartości do nich, tak jakby były to proste typy nieagregujące:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Typy wartości są *zapieczętowane*, co oznacza, że na przykład nie można utworzyć typu z <xref:System.Int32?displayProperty=nameWithType>i nie można zdefiniować struktury dziedziczonej z żadnej klasy lub struktury zdefiniowanej przez użytkownika, ponieważ struktura może dziedziczyć tylko po <xref:System.ValueType?displayProperty=nameWithType>. Jednak struktura może zaimplementować jeden lub więcej interfejsów. Typ struktury można rzutować na dowolny typ interfejsu, który implementuje; powoduje *to, że operacja opakowywania* otacza strukturę wewnątrz obiektu typu odwołania na zarządzanym stosie. Operacje pakowania są wykonywane w przypadku przekazania typu wartości do metody, która przyjmuje <xref:System.Object?displayProperty=nameWithType> lub dowolny typ interfejsu jako parametr wejściowy. Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](./boxing-and-unboxing.md).

Za pomocą słowa kluczowego [struct](../../language-reference/builtin-types/struct.md) można tworzyć własne niestandardowe typy wartości. Zazwyczaj struktura jest używana jako kontener dla małego zestawu powiązanych zmiennych, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Aby uzyskać więcej informacji na temat struktur, zobacz [struktury](../classes-and-structs/structs.md). Aby uzyskać więcej informacji na temat typów wartości, zobacz [typy wartości](../../language-reference/builtin-types/value-types.md).

Druga kategoria typów wartości to [enum](../../language-reference/builtin-types/enum.md). Wyliczenie definiuje zestaw nazwanych stałych całkowitych. Na przykład Wyliczenie <xref:System.IO.FileMode?displayProperty=nameWithType> w bibliotece klas .NET zawiera zestaw nazwanych stałych liczb całkowitych, które określają, jak plik powinien być otwarty. Jest on zdefiniowany, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

Stała `System.IO.FileMode.Create` ma wartość 2. Jednak nazwa jest znacznie bardziej zrozumiała dla ludzi odczytujących kod źródłowy. z tego powodu lepiej jest używać wyliczeń zamiast stałych liczb literałów. Aby uzyskać więcej informacji, zobacz <xref:System.IO.FileMode?displayProperty=nameWithType>.

Wszystkie wyliczenia dziedziczą z <xref:System.Enum?displayProperty=nameWithType>, który dziedziczy z <xref:System.ValueType?displayProperty=nameWithType>. Wszystkie reguły, które mają zastosowanie do struktur, mają zastosowanie również do typów wyliczeniowych. Aby uzyskać więcej informacji na temat typów wyliczeniowych, zobacz [typy](../../language-reference/builtin-types/enum.md)wyliczeniowe.

### <a name="reference-types"></a>Typy odwołań

Typ, który jest zdefiniowany jako [Klasa](../../language-reference/keywords/class.md), [Delegat](../../language-reference/builtin-types/reference-types.md), tablica lub [interfejs](../../language-reference/keywords/interface.md) , jest *typem referencyjnym*. W czasie wykonywania, gdy deklarujesz zmienną typu referencyjnego, zmienna zawiera wartość [null](../../language-reference/keywords/null.md) do momentu jawnego utworzenia obiektu za pomocą operatora [New](../../language-reference/operators/new-operator.md) lub przypisania go do obiektu, który został utworzony w innym miejscu przy użyciu `new`, jak pokazano w następującym przykładzie:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Interfejs musi być zainicjowany razem z obiektem klasy, który implementuje go. Jeśli `MyClass` implementuje `IMyInterface`, utworzysz wystąpienie `IMyInterface`, jak pokazano w następującym przykładzie:

```csharp
IMyInterface iface = new MyClass();
```

Po utworzeniu obiektu pamięć jest przydzielana na zarządzanym stosie, a zmienna zawiera tylko odwołanie do lokalizacji obiektu. Typy na stercie zarządzanej wymagają narzutu podczas przydzielania i kiedy są odzyskiwane przez funkcję automatycznego zarządzania pamięcią środowiska CLR, która jest znana jako *wyrzucanie elementów bezużytecznych*. Jednak wyrzucanie elementów bezużytecznych jest również wysoce zoptymalizowane i w większości scenariuszy nie tworzy problemu z wydajnością. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [Automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md).

Wszystkie tablice są typami odwołań, nawet jeśli ich elementy są typami wartości. Tablice niejawnie pochodzą od klasy <xref:System.Array?displayProperty=nameWithType>, ale deklarują i używają ich przy użyciu uproszczonej składni dostarczonej przez C#, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Typy odwołań w pełni obsługują dziedziczenie. Podczas tworzenia klasy można dziedziczyć z dowolnego innego interfejsu lub klasy, która nie jest zdefiniowana jako [Sealed](../../language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć z klasy i zastępować metody wirtualne. Aby uzyskać więcej informacji na temat tworzenia własnych klas, zobacz [klasy i struktury](../classes-and-structs/index.md). Aby uzyskać więcej informacji na temat dziedziczenia i metod wirtualnych, zobacz [dziedziczenie](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Typy wartości literału

W C#programie wartości literałów otrzymują typ z kompilatora. Możesz określić sposób wpisywania literału liczbowego, dołączając literę do końca liczby. Na przykład, aby określić, że wartość 4,56 powinna być traktowana jako zmiennoprzecinkowa, należy dołączyć "f" lub "F" po liczbie: `4.56f`. Jeśli nie zostanie dołączona żadna litera, kompilator wykryje typ dla literału. Aby uzyskać więcej informacji na temat typów, które można określić za pomocą sufiksów liter, zobacz [całkowite typy liczbowe](../../language-reference/builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe typy liczbowe](../../language-reference/builtin-types/floating-point-numeric-types.md).

Ponieważ wpisywane są literały, a wszystkie typy są ostatecznie z <xref:System.Object?displayProperty=nameWithType>, można napisać i skompilować kod, taki jak następujące:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Typy ogólne

Typ może być zadeklarowany z co najmniej jednym *parametrem typu* , który służy jako symbol zastępczy dla rzeczywistego typu ( *konkretny typ*), który będzie używany przez kod klienta podczas tworzenia wystąpienia typu. Takie typy są nazywane *typami ogólnymi*. Na przykład typ .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma jeden parametr typu, który według Konwencji ma nazwę *t*. Podczas tworzenia wystąpienia typu należy określić typ obiektów, które będzie zawierać lista, na przykład ciąg:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Użycie parametru typu umożliwia ponowne użycie tej samej klasy do przechowywania dowolnego typu elementu, bez konieczności konwertowania każdego elementu na [obiekt](../../language-reference/builtin-types/reference-types.md). Klasy kolekcji generycznej są nazywane *kolekcjami z jednoznacznie* określonymi typami, ponieważ kompilator wie określony typ elementów kolekcji i może zgłosić błąd w czasie kompilacji, jeśli na przykład próbujesz dodać liczbę całkowitą do obiektu `stringList` w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Typy niejawne, typy anonimowe i typy wartości null

Jak wspomniano wcześniej, można niejawnie wpisać zmienną lokalną (ale nie składową klasy) za pomocą słowa kluczowego [var](../../language-reference/keywords/var.md) . Zmienna nadal otrzymuje typ w czasie kompilacji, ale typ jest dostarczany przez kompilator. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../classes-and-structs/implicitly-typed-local-variables.md).

W niektórych przypadkach nie jest wygodne tworzenie nazwanego typu dla prostych zestawów powiązanych wartości, które nie mają być przechowywane ani przekazywane poza granicami metod. W tym celu można utworzyć *Typy anonimowe* . Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../classes-and-structs/anonymous-types.md).

Typy wartości zwykłych nie mogą mieć wartości [null](../../language-reference/keywords/null.md). Można jednak utworzyć typy wartości null, umieszczając `?` po typie. Na przykład `int?` jest typem `int`, który może mieć również wartość [null](../../language-reference/keywords/null.md). Typy wartości null są wystąpieniami typu struktury generycznej <xref:System.Nullable%601?displayProperty=nameWithType>. Typy wartości null są szczególnie przydatne podczas przekazywania danych do i z baz danych, w których wartości liczbowe mogą mieć wartość null. Aby uzyskać więcej informacji, zobacz [typy wartości null](../../language-reference/builtin-types/nullable-value-types.md).

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

- [C#Odwoła](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Konwersja typów danych XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Typy całkowite](../../language-reference/builtin-types/integral-numeric-types.md)
