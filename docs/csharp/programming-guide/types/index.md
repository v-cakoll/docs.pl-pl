---
title: 'Typy — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - 'value types [C#]'
  - 'reference types [C#]'
  - 'types [C#]'
  - 'C# language, data types'
  - 'common type system [C#]'
  - 'data types [C#]'
  - 'C# language, types'
  - 'strong typing [C#]'
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
---
# <a name="types-c-programming-guide"></a>Typy (Przewodnik programowania w języku C#)
## <a name="types-variables-and-values"></a>Typy, zmienne i wartości  
 C# jest językiem jednoznacznym. Każda zmienna i stała ma typ, podobnie jak każde wyrażenie, którego wynikiem jest wartość. Każdy podpis metody Określa typ dla każdego parametru wejściowego oraz wartość zwracaną. Biblioteka klas .NET definiuje zestaw wbudowanych typów liczbowych, jak również bardziej złożonych typów, które reprezentują szeroką gamę konstrukcji logicznych, takich jak system plików, połączenia sieciowe, kolekcje i tablice obiektów i daty. Typowy program C# korzysta z typów z biblioteki klas, a także typy zdefiniowane przez użytkownika, które modelują koncepcje, które są specyficzne dla programu dziedziny problemu.  
  
 Informacje przechowywane w typie mogą być następujące:  
  
-   Wymagającego zmiennej typu miejsca do magazynowania.  
  
-   Wartości maksymalne i minimalne, które może reprezentować.  
  
-   Członkowie (metody, pola, zdarzenia i tak dalej), które zawiera.  
  
-   Typ podstawowy, który dziedziczy.  
  
-   Lokalizacja, w której w czasie wykonywania, w którym będzie można przydzielić pamięci dla zmiennych.  
  
-   Rodzaje operacji, które są dozwolone.  
  
 Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje, które są wykonywane w kodzie są *bezpieczny*. Na przykład, jeśli zadeklarować zmienną typu [int](../../../csharp/language-reference/keywords/int.md), kompilator umożliwi dodatkowo użycia zmiennej operacjach dodawania i odejmowania. Jeśli próbujesz wykonać te same operacje na zmiennej typu [bool](../../../csharp/language-reference/keywords/bool.md), kompilator generuje błąd, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideTypes#42](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  Programiści C i C++, zwróć uwagę, że w języku C# [bool](../../../csharp/language-reference/keywords/bool.md) nie jest konwertowany na [int](../../../csharp/language-reference/keywords/int.md).  
  
 Kompilator osadza informacje o typie pliku wykonywalnego jako metadane. Środowisko uruchomieniowe języka wspólnego (CLR) używa tych metadanych w czasie wykonywania do dalszego gwarantuje bezpieczeństwo typów, gdy przydziela i przejmuje pamięć.  
  
### <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych  
 Kiedy Deklarujesz zmienną lub stałą w programie, należy określić jej typ lub użyć [var](../../../csharp/language-reference/keywords/var.md) — słowo kluczowe, aby umożliwić kompilatorowi wydedukować typ. Poniższy przykład pokazuje kilka deklaracji zmiennych, korzystających z wbudowanych typów liczbowych i złożonych typów zdefiniowanych przez użytkownika:  
  
 [!code-csharp[csProgGuideTypes#36](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_2.cs)]  
  
 Typy parametrów metody i wartości zwracane są określone w oznaczeniu metody. Następująca sygnatura przedstawia metodę, która wymaga [int](../../../csharp/language-reference/keywords/int.md) jako argument wejściowy i zwraca ciąg:  
  
 [!code-csharp[csProgGuideTypes#35](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_3.cs)]  
  
 Po zadeklarowaniu zmiennej nie może być ponownie zadeklarowany z nowym typem i nie można przypisać wartość, która nie jest zgodna z deklarowanym typem. Na przykład nie można zadeklarować [int](../../../csharp/language-reference/keywords/int.md) a następnie przypisać jej wartości logicznej [true](../../../csharp/language-reference/keywords/true-literal.md). Jednakże wartości można przekonwertować do innych typów, na przykład gdy są one przypisane do nowych zmiennych lub przekazywane jako argumenty tej metody. A *konwersja typu* która nie powoduje utraty danych jest realizowane automatycznie przez kompilator. Wymaga konwersji, która może spowodować utratę danych *rzutowania* w kodzie źródłowym.  
  
 Aby uzyskać więcej informacji, zobacz [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).   
  
## <a name="built-in-types"></a>Typy wbudowane  
 C# zawiera standardowy zestaw wbudowanych typów liczbowych do reprezentowania liczb całkowitych, pływające wartości punktów, wyrażenia logiczne, znaki tekstowe, wartości dziesiętne i innych typów danych. Dostępne są również wbudowane `string` i `object` typów. Są one dostępne do użycia w dowolnym programie C#. Aby uzyskać więcej informacji na temat wbudowanych typów, zobacz [tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Niestandardowe typy  
 Możesz użyć [struktury](../../../csharp/language-reference/keywords/struct.md), [klasy](../../../csharp/language-reference/keywords/class.md), [interfejsu](../../../csharp/language-reference/keywords/interface.md), i [wyliczenia](../../../csharp/language-reference/keywords/enum.md) konstrukcji do tworzenia własnych typach niestandardowych. Sama biblioteka klas .NET jest kolekcją typów niestandardowych dostarczonych przez firmę Microsoft, którego można używać we własnych aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w dowolnym programie C#. Inne stają się dostępne tylko wtedy, gdy użytkownik jawnie doda odwołanie do zestawu, w której są zdefiniowane. Gdy kompilator będzie zawierać odwołanie do zestawu, można zadeklarować zmienne (i stałe) typy zadeklarowane w tym Zgromadzeniu w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [Biblioteka klas programu .NET](../../../standard/class-library-overview.md).  
  
## <a name="the-common-type-system"></a>Wspólny System typów  
 Jest to ważne, aby zrozumieć dwa podstawowe punkty o systemie typu na platformie .NET:  
  
-   Obsługuje zasady dziedziczenia. Typy mogą pochodzić od innych typów nazywanych *typy podstawowe*. Typ pochodny dziedziczy (z pewnymi ograniczeniami) metody, właściwości i inne elementy członkowskie typu podstawowego. Typ podstawowy z kolei może pochodzić od innego typu, w którym przypadku typ pochodny dziedziczy członków obu typów podstawowych w hierarchii dziedziczenia. Wszystkie typy, w tym wbudowane typy liczbowe, takie jak <xref:System.Int32?displayProperty=nameWithType> (— słowo kluczowe języka C#: [int](../../../csharp/language-reference/keywords/int.md)), pochodzi ostatecznie z jednego typu podstawowego, który jest <xref:System.Object?displayProperty=nameWithType> (— słowo kluczowe języka C#: [obiektu](../../../csharp/language-reference/keywords/object.md)). Ta ujednolicona hierarchia typu jest nazywany [Wspólny System typów](../../../standard/base-types/common-type-system.md) (CTS). Aby uzyskać więcej informacji dotyczących dziedziczenia w C#, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
-   Każdy typ w CTS jest zdefiniowany jako *typu wartości* lub *odwołania do typu*. Obejmuje to wszystkie niestandardowe typy w bibliotece klas programu .NET, a także typy własne zdefiniowane przez użytkownika. Typy, które są definiowane za pomocą [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe to typy wartości; wszystkie wbudowane typy liczbowe są `structs`. Typy, które są definiowane za pomocą [klasy](../../../csharp/language-reference/keywords/class.md) słów kluczowych to odwołanie do typów. Typy odwołań i typy wartości mają różne zasady czasu kompilacji i różny sposób w czasie wykonywania.  
  
 Poniższa ilustracja przedstawia relację między typami wartości a typami odwołań w CTS.  
  
 ![Typy wartości i odwołań](../../../csharp/programming-guide/types/media/valuetypescts.png "ValueTypesCTS")  
Typy wartości i typy odwołań w CTS  
  
> [!NOTE]
>  Widać, że najczęściej używane typy są zorganizowane w <xref:System> przestrzeni nazw. Jednakże przestrzeń nazw, w którym zawarty jest typ nie ma związku tego, czy jest to wartość typu lub typów referencyjnych.  
  
### <a name="value-types"></a>Typy wartości  
 Typy wartości wywodzą się z <xref:System.ValueType?displayProperty=nameWithType>, która jest pochodną <xref:System.Object?displayProperty=nameWithType>. Typy, które wynikają z <xref:System.ValueType?displayProperty=nameWithType> mają specjalne zachowanie w CLR. Zmienne typu wartości bezpośrednio zawierają swoje wartości, co oznacza, że pamięć jest alokowana wewnątrz niezależnie od kontekstu, ta zmienna została zgłoszona. Nie ma oddzielnej alokacji stosu lub wyrzucania elementów bezużytecznych dla zmiennych typu wartości.  
  
 Istnieją dwie kategorie typów wartości: [struktury](../../../csharp/language-reference/keywords/struct.md) i [wyliczenia](../../../csharp/language-reference/keywords/enum.md).  
  
 Wbudowane typy liczbowe są strukturami i mają właściwości i metody, do których masz dostęp:  
  
```csharp  
// Static method on type Byte.  
byte b = Byte.MaxValue;  
```  
  
 Ale zadeklarować i przypisać do nich wartości, tak jakby były one proste typami-aggregacji:  
  
```csharp  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 Typy wartości są *zapieczętowanego*, oznacza to, na przykład, że nie możesz wywodzić typu z <xref:System.Int32?displayProperty=nameWithType>, i nie możesz definiować dziedziczenia struktury od dowolnego użytkownika klasy lub struktury, ponieważ struktura może dziedziczyć tylko z <xref:System.ValueType?displayProperty=nameWithType> . Jednakże struktura może zaimplementować jeden lub więcej interfejsów. Można rzutować typu struktury dowolny typ interfejsu, który implementuje; Powoduje to, że *pakowania* operację, aby opakować obiekt typu odwołania na stosie zarządzanym. Operacje na polach występują, gdy typ wartości są przekazywane do metody, która przyjmuje <xref:System.Object?displayProperty=nameWithType> lub dowolny typ jako parametr wejściowy interfejsu. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
 Możesz użyć [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe, aby utworzyć własne typy niestandardowych wartości. Typowo, struct jest używany jako kontener dla mniejszego zestawu powiązanych zmiennych, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_4.cs)]  
  
 Aby uzyskać więcej informacji na temat struktur, zobacz [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md). Aby uzyskać więcej informacji na temat typów wartości na platformie .NET, zobacz [typów wartości](../../../csharp/language-reference/keywords/value-types.md).  
  
 Inna Kategoria typu wartości jest [wyliczenia](../../../csharp/language-reference/keywords/enum.md). Wyliczenie definiuje zestaw nazwanych stałych liczbach całkowitych. Na przykład <xref:System.IO.FileMode?displayProperty=nameWithType> wyliczenia w bibliotece klas programu .NET zawiera zestaw nazwanych stałych liczb całkowitych, które określają, jak można otworzyć pliku. Jest on zdefiniowany jak pokazano w poniższym przykładzie:  
 
 [!code-csharp[csProgGuideTypes#44](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_5.cs)]  
  
 `System.IO.FileMode.Create` Stała ma wartość 2. Jednak nazwa jest bardziej istotna dla ludzi czytających kod źródłowy i tego powodu lepiej jest używać wyliczenia zamiast stałej liczby literału. Aby uzyskać więcej informacji, zobacz <xref:System.IO.FileMode?displayProperty=nameWithType>.  
  
 Wszystkie typy wyliczeniowe dziedziczą z <xref:System.Enum?displayProperty=nameWithType>, który dziedziczy z <xref:System.ValueType?displayProperty=nameWithType>. Wszystkie reguły, które dotyczą struktur stosuje się także do wyliczenia. Aby uzyskać więcej informacji na temat typów wyliczeń, zobacz [Typy wyliczeniowe](../../../csharp/programming-guide/enumeration-types.md).  
  
### <a name="reference-types"></a>Typy odwołań  
 Typ, który jest zdefiniowany jako [klasy](../../../csharp/language-reference/keywords/class.md), [delegować](../../../csharp/language-reference/keywords/delegate.md), tablicy, lub [interfejsu](../../../csharp/language-reference/keywords/interface.md) jest *odwołania do typu*. W czasie wykonywania, kiedy Deklarujesz zmienną typu odwołania, zmienna zawiera wartość [null](../../../csharp/language-reference/keywords/null.md) aż jawnie tworzone obiektu za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operatora, lub obiekt, który został gdzie indziej utworzone za pomocą `new`, jak pokazano w poniższym przykładzie:
  
```csharp  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
   Interfejs musi być zainicjowany razem z obiektem klasy, która implementuje go. Jeśli `MyClass` implementuje `IMyInterface`, Utwórz wystąpienie `IMyInterface` jak pokazano w poniższym przykładzie:  
  
```csharp  
IMyInterface iface = new MyClass();  
```  
  
 Po utworzeniu obiektu pamięć jest alokowane na zarządzanym stosie, a zmienna zawiera tylko odwołanie do lokalizacji obiektu. Typy na zarządzanym stosie wymagają narzutu zarówno kiedy są alokowane oraz kiedy są odbierane przez funkcjonalność zarządzania pamięcią automatyczną CLR, który jest znany jako *wyrzucania elementów bezużytecznych*. Jednak wyrzucanie elementów bezużytecznych jest również bardzo dobrze zoptymalizowane i w większości scenariuszy nie powoduje problemów z wydajnością. Aby uzyskać więcej informacji dotyczących wyrzucania elementów bezużytecznych, zobacz [automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md).  
  
 Wszystkie tablice są typami odwołań, nawet jeśli ich elementy są typami wartości. Tablice niejawnie pochodzą od <xref:System.Array?displayProperty=nameWithType> klasy, ale deklarujes zje i używasz ich z uproszczoną skłądnią, która jest dostarczana przez C#, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideTypes#45](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_6.cs)]  
  
 Typy odwołań w pełni obsługują dziedziczenie. Kiedy tworzysz klasę, możesz dziedziczyć od innego interfejsu lub klasy, która nie jest zdefiniowana jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), a inne klasy mogą dziedziczyć od Twojej klasy i zastępować Twoje wirtualne metody. Aby uzyskać więcej informacji na temat tworzenia własnych klas, zobacz [klas i struktur](../../../csharp/programming-guide/classes-and-structs/index.md). Aby uzyskać więcej informacji dotyczących dziedziczenia i metod wirtualnych, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="types-of-literal-values"></a>Typy wartości literałów  
 W języku C# wartości literału otrzymują typ z kompilatora. Możesz określić jak literał liczbowy powinien wpisana przez dołączenie litery na końcu numeru. Na przykład aby określić, że wartość 4,56 powinny być traktowane jako zmiennoprzecinkowa, dołączyć "f" lub "F" po liczbie: `4.56f`. Jeśli żadna litera nie zostanie dołączony, kompilator wywnioskuje typ dla literału. Aby uzyskać więcej informacji na temat tego, jakie typy można określić za pomocą literowych sufiksów, zobacz strony pomocy dla poszczególnych typów w [typów wartości](../../../csharp/language-reference/keywords/value-types.md).  
  
 Ponieważ wpisywane są literały, a wszystkie typy ostatecznie pochodzą z <xref:System.Object?displayProperty=nameWithType>, można pisać i kompilować następujący kod:  
  
 [!code-csharp[csProgGuideTypes#37](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_7.cs)]  
  
## <a name="generic-types"></a>Typy ogólne  
 Typ może być zadeklarowany z co najmniej jeden *parametry typu* obsługujących jako symbolu zastępczego dla rzeczywistego typu ( *konkretne typu*), kod klienta zapewni podczas tworzenia wystąpienia typu. Typy takie są nazywane *typów ogólnych*. Na przykład typ .NET <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma jeden parametr typu, który zgodnie z Konwencją, otrzymuje nazwę *T*. Podczas tworzenia wystąpienia typu, należy określić typ obiektów, które zawierać będzie lista, przykładowo ciąg:  
 
```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```
 Użyj parametru typu sprawia, że można ponownie użyć tej samej klasy do utrzymania jakiegokolwiek typu elementu, bez konieczno ści konwersji każdego elementu na [obiektu](../../../csharp/language-reference/keywords/object.md). Klasy ogólne kolekcji są nazywane *kolekcjami jednoznacznymi* ponieważ kompilator zna określony typ elementów kolekcji i może zgłosić błąd w czasie kompilacji, jeśli, na przykład spróbujesz dodać liczbę całkowitą do `stringList` obiekt w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Typy niejawne, anonimowe i typy dopuszczające wartości zerowe  
 Jak wspomniano wcześniej, można niejawnie wpisać zmienną lokalną (ale nie elementy klas) za pomocą [var](../../../csharp/language-reference/keywords/var.md) — słowo kluczowe. Zmienna wciąż otrzymuje typ w czasie kompilacji, ale typ jest dostarczany przez kompilator. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 W niektórych przypadkach jest wygodne, aby tworzyć nazwany typ dla prostych zestawów powiązanych wartości, które nie będą przechowywane lub przekazywane poza granice metody. Możesz utworzyć *typy anonimowe* do tego celu. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Typy wartości zwykłych nie może mieć wartość [null](../../../csharp/language-reference/keywords/null.md). Można jednak utworzyć typy o wartości zerowalnej przez umieszczenie `?` po typie. Na przykład `int?` jest `int` typu, który może mieć również wartość [null](../../../csharp/language-reference/keywords/null.md). W CTS, typy null są wystąpieniami typu struktury ogólnej <xref:System.Nullable%601?displayProperty=nameWithType>. Typy dopuszczające wartości null są szczególnie przydatne podczas przekazywania danych do i z baz danych, w których wartości liczbowe mogą przyjąć wartości null. Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Konwersja boxing i konwersja unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Konwersja typów danych XML](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)
