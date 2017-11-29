---
title: "Typy (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "53"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1352d817241ad4dd42747dcd3a6bfbaf71f9cf25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-programming-guide"></a>Typy (Przewodnik programowania w języku C#)
## <a name="types-variables-and-values"></a>Typy, zmiennych i wartości  
 C# to silnie typizowane język. Każdy zmiennej i stałej ma typ, tak jak w przypadku każdego wyrażenie obliczane do wartości. Każdy podpis metody Określa typ każdego parametru wejściowego i dla wartości zwracanej. Biblioteka klas programu .NET Framework definiuje zestaw wbudowane typy liczbowe, a także bardziej złożone typy, które reprezentują szerokiej gamy konstrukcje logicznych, takich jak system plików, połączeń sieciowych, kolekcji i tablic obiektów i daty. Typowy C# program korzysta z typów z biblioteki klas, a także typy zdefiniowane przez użytkownika, które modelu pojęcia, które są specyficzne dla domeny problemu programu.  
  
 Informacje przechowywane w typie mogą być następujące:  
  
-   Miejsce do magazynowania wymaga zmiennej typu.  
  
-   Maksymalne i minimalne wartości reprezentujących przez go.  
  
-   Elementy członkowskie (metody, pola, zdarzeń i tak dalej), które zawiera.  
  
-   Typ podstawowy, w którym on dziedziczy.  
  
-   Lokalizacja, w którym zostaną przydzielone pamięci dla zmiennych w czasie wykonywania.  
  
-   Rodzaje operacji, które są dozwolone.  
  
 Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje, które są wykonywane w kodzie są *safe typu*. Na przykład, jeśli zadeklarować zmiennej typu [int](../../../csharp/language-reference/keywords/int.md), kompilator umożliwia także użyć zmiennej i odejmowania operacji. Próba wykonania tych operacji tego samego na zmienną typu [bool](../../../csharp/language-reference/keywords/bool.md), kompilator generuje błąd, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideTypes#42](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  Deweloperzy C i C++, zwróć uwagę, że w języku C# [bool](../../../csharp/language-reference/keywords/bool.md) nie jest możliwe do przekonwertowania na [int](../../../csharp/language-reference/keywords/int.md).  
  
 Kompilator osadza informacje o typie w pliku wykonywalnego jako metadanych. Środowisko uruchomieniowe języka wspólnego (CLR) używa tych metadanych w czasie wykonywania w celu dalszego zagwarantowania bezpieczeństwa typu przydziela i zwraca pamięci.  
  
### <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych  
 Gdy zadeklarować zmiennej lub stała w programie, należy określić jego typ lub użyj [var](../../../csharp/language-reference/keywords/var.md) — słowo kluczowe, aby umożliwić kompilatora wnioskować o typie. W poniższym przykładzie przedstawiono niektóre deklaracji zmiennych, które używają zarówno wbudowane typy liczbowe, jak i złożone typy danych zdefiniowane przez użytkownika:  
  
 [!code-csharp[csProgGuideTypes#36](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_2.cs)]  
  
 Typy parametrów metod i wartości zwracane są określone w podpisie metody. Następująca sygnatura zawiera metodę, która wymaga [int](../../../csharp/language-reference/keywords/int.md) jako argument wejściowy i zwraca wartość typu ciąg:  
  
 [!code-csharp[csProgGuideTypes#35](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_3.cs)]  
  
 Po zadeklarowaniu zmiennej nie może być ponownie zadeklarowany z nowym typem i nie można przypisać wartość, która jest niezgodna z deklarowanym typem. Na przykład nie można zadeklarować [int](../../../csharp/language-reference/keywords/int.md) , a następnie przypisz jej wartość logiczną [true](../../../csharp/language-reference/keywords/true-literal.md). Jednak można konwertować wartości dla innych typów, na przykład gdy są one przypisane do nowe zmienne lub przekazywane jako argumenty metody. A *konwersja typu* tego ma nie Przyczyna utraty danych jest realizowane automatycznie przez kompilator. Wymaga konwersji, która może spowodować utratę danych *rzutowania* w kodzie źródłowym.  
  
 Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="built-in-types"></a>Typy wbudowane  
 C# zawiera standardowy zestaw wbudowanych typów numerycznych do reprezentowania liczb całkowitych, zmiennoprzecinkowych wartości, wyrażeń logicznych, znaki tekstu, wartości dziesiętnych i innymi typami danych. Istnieją również wbudowane `string` i `object` typów. Są one dostępne do użycia w programach języka C#. Aby uzyskać więcej informacji na temat wbudowanych typów, zobacz [tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Niestandardowe typy  
 Możesz użyć [struktury](../../../csharp/language-reference/keywords/struct.md), [klasy](../../../csharp/language-reference/keywords/class.md), [interfejsu](../../../csharp/language-reference/keywords/interface.md), i [wyliczenia](../../../csharp/language-reference/keywords/enum.md) konstrukcji, aby utworzyć własne niestandardowe typy. Biblioteka klas programu .NET Framework sam jest kolekcją typów niestandardowych dostarczanych przez firmę Microsoft, używanego w aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w programach języka C#. Inne stają się dostępne tylko wtedy, gdy jawnie dodać odwołanie projektu do zestawu, w którym jest zdefiniowany. Po kompilator ma odwołanie do zestawu, mogą zadeklarować zmienne (i stałych) typów zadeklarowany w tym zestawie w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [Biblioteka klas programu .NET Framework](http://go.microsoft.com/fwlink/?LinkID=217856).  
  
## <a name="the-common-type-system"></a>Wspólny System typów  
 Ważne jest, aby zrozumieć dwa punkty podstawowe informacje o systemie typu w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]:  
  
-   Obsługuje zasady dziedziczenia. Typy może pochodzić od innych typów o nazwie *typy podstawowe*. Typ pochodny dziedziczy (z pewnymi ograniczeniami), metody, właściwości i innych elementach członkowskich typu podstawowego. Typ podstawowy z kolei może pochodzić od innego typu, w których przypadku typ pochodny dziedziczy członkami obu typów podstawowych w hierarchii dziedziczenia. Wszystkich typów, w tym wbudowane typy liczbowe, takie jak <xref:System.Int32?displayProperty=nameWithType> (C# — słowo kluczowe: [int](../../../csharp/language-reference/keywords/int.md)), pochodzi ostatecznie z jednego typu podstawowego, który jest <xref:System.Object?displayProperty=nameWithType> (C# — słowo kluczowe: [obiektu](../../../csharp/language-reference/keywords/object.md)). Ta hierarchia ujednoliconego typu jest nazywana [Wspólny System typów](../../../standard/base-types/common-type-system.md) (CTS). Aby uzyskać więcej informacji na temat dziedziczenia w języku C#, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
-   Każdy typ w CTS jest zdefiniowany jako *typu wartości* lub *zawierają odwołania do typu*. W tym wszystkich niestandardowych typów w bibliotece klas programu .NET Framework, a także własnych typów zdefiniowanych przez użytkownika. Typy zdefiniowane przez użytkownika za pomocą [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe są typy wartości; są wbudowane typy liczbowe `structs`. Typy zdefiniowane przez użytkownika za pomocą [klasy](../../../csharp/language-reference/keywords/class.md) — słowo kluczowe są odwołania typów. Typy odwołań i typów wartości mają różne reguły kompilacji, a inaczej w czasie wykonywania.  
  
 Na poniższej ilustracji przedstawiono relacje między typami wartości i typy referencyjne w CTS.  
  
 ![Typy wartości i typy referencyjne](../../../csharp/programming-guide/types/media/valuetypescts.png "ValueTypesCTS")  
Typy wartości i typy w CTS odwołań  
  
> [!NOTE]
>  Widać, że najczęściej używane typy są wszystkie zorganizowane w <xref:System> przestrzeni nazw. Jednak przestrzeni nazw, w którym znajduje się typ nie ma związku Określa, czy jest to wartość typu lub typów referencyjnych.  
  
### <a name="value-types"></a>Typy wartości  
 Typy wartości pochodzi od <xref:System.ValueType?displayProperty=nameWithType>, która jest pochodną <xref:System.Object?displayProperty=nameWithType>. Typy, które pochodzą z <xref:System.ValueType?displayProperty=nameWithType> mają specjalnego zachowania w środowisku CLR. Wartość typu zmienne bezpośrednio zawierać ich wartości, co oznacza, że pamięć jest przydzielona wbudowany w dowolnym kontekście zmienna została zadeklarowana. Nie jest alokacja sterty oddzielne ani odzyskiwanie kolekcji narzut na typ wartości zmiennych.  
  
 Istnieją dwie kategorie typów wartości: [struktury](../../../csharp/language-reference/keywords/struct.md) i [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Mają właściwości i metody, do których masz dostęp, i struktury są wbudowane typy liczbowe:  
  
```csharp  
// Static method on type Byte.  
byte b = Byte.MaxValue;  
```  
  
 Ale deklaruje i przypisać do nich wartości, tak jakby były to proste typy niezagregowanym:  
  
```csharp  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 Typy wartości są *zapieczętowanego*, co oznacza, na przykład, że nie może pochodzić od typu <xref:System.Int32?displayProperty=nameWithType>, i nie może definiować strukturę odziedziczone zdefiniowane przez użytkownika klasy lub struktury, ponieważ struktury może dziedziczyć tylko z <xref:System.ValueType?displayProperty=nameWithType> . Jednak struktury można zaimplementować jeden lub więcej interfejsów. Można rzutować typu struct na typ interfejsu; Powoduje to *boxing* operacji opakowywać struktury wewnątrz obiektu typu odwołania na stercie zarządzanej. OPAKOWYWANIE operacje są wykonywane, gdy typ wartości jest przekazywane do metody pobierającej <xref:System.Object?displayProperty=nameWithType> jako parametr wejściowy. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
 Możesz użyć [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe do tworzenia własnych typów wartości niestandardowych. Zazwyczaj struktury służy jako kontener dla małych zestawu powiązanych zmiennych, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_4.cs)]  
  
 Aby uzyskać więcej informacji na temat struktury, zobacz [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md). Aby uzyskać więcej informacji na temat typów wartości w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], zobacz [Wspólny System typów](../../../standard/base-types/common-type-system.md).  
  
 Kategoria inne typy wartości jest [wyliczenia](../../../csharp/language-reference/keywords/enum.md). Wyliczenie definiuje zestaw o nazwie stałe całkowite. Na przykład <xref:System.IO.FileMode?displayProperty=nameWithType> wyliczenia w bibliotece klas programu .NET Framework zawiera zestaw o nazwie stałej liczb całkowitych, które określają, jak można otworzyć pliku. Jest ona zdefiniowana, jak pokazano w poniższym przykładzie:  
 
 [!code-csharp[csProgGuideTypes#44](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_5.cs)]  
  
 `System.IO.FileMode.Create` Stała ma wartość 2. Jednak nazwa jest znacznie bardziej zrozumiały dla ludzi odczytywania kodu źródłowego i że jego przyczyny jest lepiej jest użyć zamiast stałej liczby literału wyliczenia. Aby uzyskać więcej informacji, zobacz <xref:System.IO.FileMode?displayProperty=nameWithType>.  
  
 Dziedzicz wszystkich wyliczeniach <xref:System.Enum?displayProperty=nameWithType>, który dziedziczy z <xref:System.ValueType?displayProperty=nameWithType>. Wszystkie reguły, które są stosowane do struktury także stosować do wyliczenia. Aby uzyskać więcej informacji na temat wyliczenia, zobacz [Typy wyliczeniowe](../../../csharp/programming-guide/enumeration-types.md).  
  
### <a name="reference-types"></a>Typy odwołań  
 Typ, który jest zdefiniowany jako [klasy](../../../csharp/language-reference/keywords/class.md), [delegować](../../../csharp/language-reference/keywords/delegate.md), tablicy lub [interfejsu](../../../csharp/language-reference/keywords/interface.md) jest *zawierają odwołania do typu*. W czasie wykonywania, gdy można zadeklarować zmiennej typu referencyjnego, zmienna zawiera wartość [null](../../../csharp/language-reference/keywords/null.md) do momentu jawnego tworzenia wystąpienia obiektu przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operatora, lub Przypisz do niego obiekt który został utworzony w innym miejscu przy użyciu `new`, jak pokazano w poniższym przykładzie:
  
```csharp  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
   Interfejs musi zostać zainicjowany wraz z obiektem klasy, który implementuje go. Jeśli `MyClass` implementuje `IMyInterface`, Utwórz wystąpienie `IMyInterface` jak pokazano w poniższym przykładzie:  
  
```csharp  
IMyInterface iface = new MyClass();  
```  
  
 Po utworzeniu obiektu na stercie zarządzanej jest przydzielana pamięć, a zmienna zawiera tylko odwołanie do lokalizacji obiektu. Typy w stercie zarządzanej wymaga obciążenie zarówno podczas są przydzielone i podczas odzyskane przez funkcje zarządzania automatyczne pamięci środowiska CLR, znany jako *wyrzucanie elementów bezużytecznych*. Jednak również stopniu zoptymalizowany wyrzucanie elementów bezużytecznych i w większości przypadków nie jest tworzony problem z wydajnością. Aby uzyskać więcej informacji o pamięci, zobacz [automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md).  
  
 Wszystkie tablice są typów referencyjnych, nawet jeśli ich elementy są typów wartości. Tablice niejawnie pochodzi od <xref:System.Array?displayProperty=nameWithType> klasy, ale deklaruje i używać ich przy użyciu składni uproszczoną zapewnianej przez C#, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideTypes#45](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_6.cs)]  
  
 Typy odwołań w pełni obsługuje dziedziczenia. Podczas tworzenia klasy mogą dziedziczyć z innych interfejs lub klasa, która nie jest zdefiniowany jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), i inne klasy mogą dziedziczyć po klasie i zastąpienie metody wirtualnej. Aby uzyskać więcej informacji na temat tworzenia własnych klas, zobacz [klas i struktur](../../../csharp/programming-guide/classes-and-structs/index.md). Aby uzyskać więcej informacji na temat dziedziczenia i metody wirtualne, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="types-of-literal-values"></a>Wartości literałów  
 W języku C# wartości literałów otrzymywane z kompilatora. Można określić, jak literał liczbowy należy wpisać przez dołączenie list na końcu numeru. Na przykład, aby określić, że wartość 4.56 powinny być traktowane jako wartości zmiennoprzecinkowej, Dołącz "f" lub "F" po wartości: `4.56f`. Jeśli litera nie jest dołączana, kompilator będzie wnioskować o typie dla literału. Aby uzyskać więcej informacji o tym, które można określić typy z sufiksy litera, zobacz strony podręcznika dla poszczególnych typów w [typów wartości](../../../csharp/language-reference/keywords/value-types.md).  
  
 Ponieważ wpisywania literały, a wszystkie typy ostatecznie pochodzi z <xref:System.Object?displayProperty=nameWithType>, możesz zapisać i skompilować kod, takie jak następujące:  
  
 [!code-csharp[csProgGuideTypes#37](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_7.cs)]  
  
## <a name="generic-types"></a>Typy ogólne  
 Typ mogą być deklarowane z co najmniej jednym *parametry typu* obsługujących jako symbol zastępczy rzeczywisty typ ( *specyficzne typu*) czy kod klienta zapewni podczas tworzenia wystąpienia typu. Takie typy są nazywane *typów ogólnych*. Na przykład typ .NET Framework <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma jeden parametr typu, który przez Konwencję o nazwie *T*. Podczas tworzenia wystąpienia typu, należy określić typ obiektu, który będzie zawierać listę, na przykład ciąg:  
 
```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```
 Użyj parametru typu umożliwia ponowne użycie tej samej klasy, aby pomieścić dowolnego typu elementu, bez konieczności Konwertuj każdy element na [obiektu](../../../csharp/language-reference/keywords/object.md). Klasy kolekcji ogólnych są nazywane *kolekcje silnie typizowane* ponieważ kompilator zna określonego typu elementów w kolekcji i może zgłaszać błąd w czasie kompilacji Jeśli, na przykład próby dodania całkowitą do `strings` obiektu w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Niejawne typów, typy anonimowe i typy dopuszczające wartości zerowe  
 Jak wspomniano wcześniej, można niejawnie wpisać zmiennej lokalnej (ale nie elementów członkowskich klasy) przy użyciu [var](../../../csharp/language-reference/keywords/var.md) — słowo kluczowe. Zmienna nadal otrzymuje typu w czasie kompilacji, ale podano typ przez kompilator. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 W niektórych przypadkach jest niewygodne do utworzenia nazwanego typu prostego zestawów powiązanych wartości, które będą przechowywać lub Przekaż poza granice — metoda. Można utworzyć *typy anonimowe* w tym celu. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Typy wartości zwykłej nie może mieć wartości [null](../../../csharp/language-reference/keywords/null.md). Można jednak utworzyć typy dopuszczające wartości zerowe wartości przez umieszczenie `?` po typie. Na przykład `int?` jest `int` typu, który ma także wartość [null](../../../csharp/language-reference/keywords/null.md). W CTS, typy dopuszczające wartości null są wystąpienia typu ogólnego struktury <xref:System.Nullable%601?displayProperty=nameWithType>. Typy dopuszczające wartości null są szczególnie przydatne, gdy są przekazywanie danych do i z baz danych, w których wartości liczbowych może mieć wartości null. Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Konwersja typów danych XML](../../../standard/data/xml/conversion-of-xml-data-types.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)
