---
title: Semantykę odwołania z typami wartości
description: Zrozumieć funkcje językowe, co minimalizuje bezpiecznie kopiowania struktury
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 778897dc92f8a94178ebbbed7704c0dfe2397729
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="reference-semantics-with-value-types"></a>Semantykę odwołania z typami wartości

Zaletą używania typów wartości jest, aby uniknąć często Alokacje sterty.
Wadą jest to, że są one kopiowane wartości. Ta zależnościami utrudnia zoptymalizować algorytmy, które pracują w dużych ilości danych. Nowe funkcje języka C# 7.2 zapewniają mechanizmy, które Włącz semantykę przekazywany przez odwołanie z typami wartości. Rozsądny sposób używać tych funkcji, aby zminimalizować zarówno alokacji i operacje kopiowania. Ten artykuł opisuje te nowe funkcje.

Większość przykładowy kod w tym artykule przedstawiono funkcje dodane w języku C# 7.2. Aby można było używać tych funkcji, należy skonfigurować projektu do języka C# 7,2 lub nowszej. Visual Studio można użyć, aby go wybrać. Dla każdego projektu, zaznacz **projektu** z menu, następnie **właściwości**. Wybierz **kompilacji** i kliknij polecenie **zaawansowane**. Z tego miejsca skonfiguruj wersji językowej. Wybierz opcję "7.2" lub "najnowszej".  W razie potrzeby można edytować *csproj* plik i dodać następującego węzła:

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

Można użyć "7,2" lub "najnowszej" dla wartości.

## <a name="passing-arguments-by-readonly-reference"></a>Przekazywanie argumentów poprzez odwołanie tylko do odczytu

C# 7.2 dodaje `in` — słowo kluczowe, aby mogła uzupełniać istniejące `ref` i `out` słowa kluczowe, aby przekazywać argumentów przez odwołanie. `in` — Słowo kluczowe określa przekazywanie argumentów poprzez odwołanie, ale wywołaną metodę nie modyfikuje wartość. 

To dodawanie zapewnia pełne słownictwa Express z celem projektu. Typy wartości są kopiowane, gdy przekazana do metody o nazwie, jeśli nie określisz żadnego z następujących modyfikatorów w podpisie metody. Każdy z tych Modyfikatory Określa, że typ wartości jest przekazywana przez odwołanie, unikając kopiowania. Każdy modyfikator wyraża innego zamiaru:

- `out`: Ta metoda określa wartość argumentu używany jako parametr.
- `ref`: Ta metoda może ustawić wartość argumentu używany jako parametr.
- `in`: Ta metoda nie modyfikuje wartość argumentu używany jako parametr.

Dodaj `in` modyfikator do przekazywania argumentu przez odwołanie ani deklarować zamiaru projektowania przekazywać argumentów przez odwołanie, aby uniknąć niepotrzebnych kopiowania. Nie chcesz zmodyfikować obiekt używany jako tego argumentu. Poniższy kod przedstawia przykład metodę, która oblicza odległość między dwoma punktami w przestrzeni 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Argumenty są dwie struktury, że każdy zawiera trzy symulacyjnych. Wartość o podwójnej precyzji jest 8 bajtów, dzięki czemu każdy argument jest 24 bajty. Określając `in` modyfikator, należy przekazać 4-bajtowych lub 8-bajtowych odwołanie do tych argumentów, w zależności od architektury komputera. Różnica w rozmiarze jest mały, ale jego można szybko dodać po aplikacji wywołuje tę metodę w pętli ścisłej przy użyciu wielu różnych wartości.
 
`in` Uzupełnia modyfikator `out` i `ref` także inne sposoby. Nie można utworzyć przeciążenia metody, które różnią się jedynie w związku z występowaniem `in`, `out`, lub `ref`. Te nowe reguły rozszerzania zawsze ma zdefiniowany dla tego samego zachowania `out` i `ref` parametrów.

`in` Modyfikator mogą być stosowane do dowolnego członka, który przyjmuje parametry: metody, delegatów, wyrażenia lambda, funkcje lokalne, indeksatorów, operatorów.

W odróżnieniu od `ref` i `out` argumenty, można użyć wartości literałów ani stałe dla argumentu `in` parametru. Ponadto, w przeciwieństwie do `ref` lub `out` parametr, nie trzeba zastosować `in` modyfikator w miejsce wywołania. Poniższy kod przedstawia dwa przykłady wywołania metody `CalculateDistance` metody. Pierwszy korzysta z dwóch zmiennych lokalnych przekazywana przez odwołanie. Drugi zawiera zmiennej tymczasowej utworzone jako część wywołania metody. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w których kompilator zapewnia, które tylko do odczytu rodzaj `in` argument jest wymuszana.  Przede wszystkim wywołaną metodę nie można przypisać bezpośrednio do `in` parametru. Bezpośrednio nie można przypisać do dowolnego pola `in` parametru, jeśli ta wartość jest `struct` typu. Ponadto nie można przekazać `in` parametr przy użyciu dowolnej metody `ref` lub `out` modyfikator.
Te reguły dotyczą wszystkie pola z `in` podany parametr pole jest `struct` typu i parametru jest również `struct` typu. W rzeczywistości te reguły mają zastosowanie dla wielu warstw dostępu do elementu członkowskiego podane, są typy na wszystkich poziomach dostęp do elementu członkowskiego `structs`. Wymusza kompilator, który `struct` typów przekazywane jako `in` argumentów i ich `struct` elementy członkowskie są zmienne tylko do odczytu, gdy jest używany jako argumenty do innych metod.

Korzystanie z `in` parametry pozwala uniknąć potencjalne koszty wydajności tworzenia kopii. Nie zmienia semantykę wszystkie wywołania metody. W związku z tym nie należy określić `in` modyfikator w miejsce wywołania. Jednakże, pomijając `in` modyfikator w witrynie wywołania informuje kompilator czy może on być kopię argumentu z następujących powodów:

- Istnieje niejawna konwersja, ale nie tożsamości konwersja z typu argumentu na typ parametru.
- Argument jest wyrażeniem, ale nie ma zmienną znane magazynu.
- Istnieje inna obecności lub braku `in`. W takim przypadku wartość przeciążenia jest lepszym dopasowaniem.

Reguły te są przydatne, jak aktualizacji istniejącego kodu do argumenty odwołania tylko do odczytu. Wewnątrz wywołaną metodę można wywołać dowolnej metody wystąpienia używanego przez wartości parametrów. W tych przypadkach kopię `in` utworzeniu parametru. Ponieważ kompilator można utworzyć zmiennej tymczasowej dla każdego `in` parametru, można również określić wartości domyślnej dla żadnego `in` parametru. Poniższy kod określa punkt początkowy (punkt 0,0) z wartością domyślną dla drugiego punktu:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Aby wymusić kompilatora do odczytu tylko argument jest przekazywany przez odwołanie, określ `in` modifer na argumenty w witrynie wywołanie, jak pokazano w poniższym kodzie:

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#ExplicitInArgument "Specifying an In argument")]

To zachowanie ułatwia przyjęcie `in` parametry z czasem w dużej codebases, gdy wzrost wydajności są możliwe. Możesz dodać `in` modyfikator do metody sygnatur pierwszy. Następnie można dodać `in` modyfikator na callsites i Utwórz `readonly struct` typów, aby włączyć kompilatora uniknąć tworzenia obrony kopie `in` parametrów w więcej lokalizacji.

`in` Parametr oznaczenia można również typy odwołań lub wartości liczbowe. Jednak korzyści w obu przypadkach są minimalne, jeśli istnieje.

## <a name="ref-readonly-returns"></a>`ref readonly` Zwraca

Można również zwrócić przez odwołanie typu wartości, ale nie zezwalaj na obiekt wywołujący modyfikowanie tej wartości. Użyj `ref readonly` modyfikator Express celem tego projektu. Czy są zwracane jest odwołanie do istniejących danych, ale nie zezwala na modyfikowanie powiadomi czytników. 

Kompilator wymusza, że obiekt wywołujący nie można zmodyfikować odwołania. Próby bezpośrednio przypisać wartość generuje błąd kompilacji. Jednak kompilator nie wiadomo, jeśli metoda dowolnego elementu członkowskiego modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowany, kompilator tworzy kopię i wywołuje element członkowski odwołań za pomocą tej kopii. Wszystkie modyfikacje są obrony ją. 

Istnieje prawdopodobieństwo, że przy użyciu biblioteki `Point3D` często użyje źródła w całym kodzie. Każde wystąpienie tworzy nowy obiekt na stosie. Może być korzystne utworzyć stałą i zwracać jej przez odwołanie. Jednak jeśli zwraca odwołanie do wewnętrznej pamięci masowej, może zajść potrzeba wymuszenia, że obiekt wywołujący nie można zmodyfikować magazynu, do którego istnieje odwołanie. Poniższy kod definiuje właściwości tylko do odczytu, która zwraca `readonly ref` do `Point3D` , który określa punkt początkowy.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Tworzenie kopii tylko do odczytu ref zwracany jest prosty: tylko przypisz go do zmiennej, nie jest zadeklarowana z `ref readonly` modyfikator. Kompilator generuje kod, aby skopiować obiekt w ramach przypisania. 

Po przypisaniu zmiennej `ref readonly return`, można określić `ref readonly` zmiennej lub przez wartość kopię tylko do odczytu odwołania:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie tworzy kopię `Origin` stała i przypisuje, które skopiować. Drugi przypisuje odwołanie. Zwróć uwagę, że `readonly` modyfikator musi być częścią deklaracja zmiennej. Nie można zmodyfikować odwołania, do którego się odwołuje. Próbuje zrobić spowodować błąd kompilacji.

## <a name="readonly-struct-type"></a>`readonly struct` Typ

Stosowanie `ref readonly` na wykorzystanie dużym natężeniu ruchu struktury mogą być wystarczające.
Innym razem, można utworzyć niezmienialny struktury. Zawsze można następnie przekazać przez odwołanie tylko do odczytu. Czy rozwiązanie usuwa ataku kopiuje tego miejsce, gdy uzyskujesz dostęp do metody struktury używane jako `in` parametru.

Możesz to zrobić, tworząc `readonly struct` typu. Możesz dodać `readonly` modyfikatora w deklaracji struktury. Kompilator wymusza, że wszystkie elementy członkowskie wystąpień struktury są `readonly`; `struct` musi być niezmienialne.

Istnieją inne optymalizacje dla `readonly struct`. Można użyć `in` modyfikator w każdej lokalizacji gdzie `readonly struct` jest argumentem. Ponadto można zwrócić `readonly struct` jako `ref return` po zwróconego obiektu, którego okres istnienia wykracza poza zakres metoda zwraca obiekt.

Na koniec kompilator generuje kod efektywniejsze podczas wywoływania członkami `readonly struct`: `this` odwołania, zamiast kopiowania odbiornika, jest zawsze `in` parametr przekazywany przez odwołanie do elementu członkowskiego. Tego rodzaju optymalizacji zapisuje więcej kopiowania, korzystając z `readonly struct`. `Point3D` Jest doskonałym kandydatem do tej zmiany. Poniższy kod przedstawia zaktualizowaną `ReadonlyPoint3D` struktury:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` Typ

Inna funkcja języka powiązane jest możliwość zadeklarować typu wartości, który musi znajdować się na stosie. Innymi słowy te typy nigdy nie można utworzyć na stercie członkiem innej klasy. Główną motywacją do tej funkcji został <xref:System.Span%601> i powiązanych struktury. <xref:System.Span%601> może zawierać wskaźnika zarządzane jako jeden z jego elementów członkowskich, inne są długość zakresu. Wdrażana jest nieco inaczej ponieważ C# nie obsługuje wskaźników do pamięci zarządzanej poza niebezpiecznym kontekście. Wszelkie zapisu, która zmienia wskaźnika oraz długość nie jest atomic. Oznacza to, że <xref:System.Span%601> będzie podlegać poza zakresem błędy lub innego typu naruszenia bezpieczeństwa zostały nie ograniczone do ramki stosu pojedynczego. Ponadto zwykle umieszczenie wskaźnika zarządzanego na stercie GC ulega awarii podczas JIT.

Może być podobne wymagania dotyczące pracy z pamięci utworzone za pomocą [ `stackalloc` ](language-reference/keywords/stackalloc.md) lub w przypadku używania pamięci z międzyoperacyjnego interfejsów API. Można definiować własnych `ref struct` typy dla tych potrzeb. W tym artykule, zobacz przykłady użycia `Span<T>` dla uproszczenia.

`ref struct` Deklaracji deklaruje struktury tego typu musi być na stosie. Reguły języka zapewnienia bezpiecznego korzystania z tych typów. Inne typy zadeklarowane jako `ref struct` obejmują <xref:System.ReadOnlySpan%601>. 

Celem porządkowania `ref struct` typu jako zmienną przydzielony stos wprowadzono kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.

- Nie można polu `ref struct`. Nie można przypisać `ref struct` typ zmiennej typu `object`, `dynamic`, albo typu interfejsu.
- Nie można zadeklarować `ref struct` jako element członkowski klasy lub struktury normalnego.
- Nie można deklarować zmiennych lokalnych, które są `ref struct` typów w metodach asynchronicznych. Można je zadeklarować w metod synchronicznych, które zwracają `Task`, `Task<T>` lub typów zadań.
- Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.
- Nie można przechwycić `ref struct` zmiennych w wyrażeniach lambda lub funkcje lokalne.

Upewnij się, te ograniczenia nie używasz przypadkowo `ref struct` w taki sposób, który można podwyższyć sterty zarządzanej.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Typ

Deklarowanie struktury jako `readonly ref` łączy korzyści i ograniczeń dotyczących `ref struct` i `readonly struct` delcarations. 

W poniższym przykładzie pokazano deklaracja `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    public ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Wnioski

Te ulepszenia języka C# są przeznaczone dla algorytmów krytyczne wydajności, których alokacji pamięci może być krytyczne znaczenie dla osiągnięcia niezbędne wydajności. Może się okazać, że nie są często używane te funkcje w kodzie zostanie zapisany. Jednak te ulepszenia zostały przyjęte w wielu lokalizacjach w programie .NET Framework. Jak coraz więcej interfejsów API należy używać tych funkcji, zobaczysz poprawy wydajności własnych aplikacji.
