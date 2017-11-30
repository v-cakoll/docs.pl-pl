---
title: "Semantykę odwołania z typami wartości"
description: "Zrozumieć funkcje językowe, co minimalizuje bezpiecznie kopiowania struktury"
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 0c6e44a3e1a1458f4211b66b6d1ef5b4b30cd7c1
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="reference-semantics-with-value-types"></a>Semantykę odwołania z typami wartości

Zaletą używania typów wartości jest, aby uniknąć często Alokacje sterty.
Odpowiednie Wada polega na tym, że są one kopiowane wartości. Ta zależnościami utrudnia zoptymalizować algorytmy, które pracują w dużych ilości danych. Nowe funkcje języka C# 7.2 zapewniają mechanizmy, które Włącz semantykę przekazywany przez odwołanie z typami wartości. Rozsądny sposób używania tych funkcji można zminimalizować zarówno alokacji i operacje kopiowania. Ten artykuł opisuje te nowe funkcje.

Większość przykładowy kod w tym artykule przedstawiono funkcje dodane w języku C# 7.2. Aby można było używać tych funkcji, należy skonfigurować projekt do używania języka C# 7,2 lub nowszej w projekcie. Visual Studio można użyć, aby go wybrać. Dla każdego projektu, zaznacz **projektu** z menu, następnie **właściwości**. Wybierz **kompilacji** i kliknij polecenie **zaawansowane**. Z tego miejsca możesz skonfigurować wersji językowej. Wybierz opcję "7.2" lub "najnowszej".  W razie potrzeby można edytować *csproj* plik i dodać następującego węzła:

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

Można użyć "7,2" lub "najnowszej" dla wartości.

## <a name="specifying-in-parameters"></a>Określanie `in` parametrów

C# 7.2 dodaje `in` — słowo kluczowe, aby mogła uzupełniać istniejące `ref` i `out` słów kluczowych podczas pisania metodę, która przekazuje argumenty przez odwołanie. `in` — Słowo kluczowe Określa, że parametr jest przekazywany przez odwołanie, i wywołana metoda nie modyfikuje wartość przekazana do niej. 

To dodawanie zapewnia pełne słownictwa Express z celem projektu. Typy wartości są kopiowane, gdy przekazywany do metody wywoływane, gdy nie określaj żadnego z następujących modyfikatorów. Określ każdy z tych modyfikatory, że typ wartości jest przekazywana przez odwołanie, unikając kopiowania. Każdy modyfikator wyraża innego zamiaru:

- `out`: Ta metoda określa wartość argumentu używany jako parametr.
- `ref`: Ta metoda może ustawić wartość argumentu używany jako parametr.
- `in`: Ta metoda nie modyfikuje wartość argumentu używany jako parametr.

Po dodaniu `in` modyfikator do przekazywania argumentu przez odwołanie, należy zadeklarować z celem projektu jest przekazywać argumentów przez odwołanie, aby uniknąć niepotrzebnych kopiowania. Nie chcesz zmodyfikować obiekt używany jako tego argumentu. Poniższy kod przedstawia przykład metodę, która oblicza odległość między dwoma punktami w przestrzeni 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Argumenty są dwie struktury, że każdy zawiera trzy symulacyjnych. Wartość o podwójnej precyzji jest 8 bajtów, dzięki czemu każdy argument jest 24 bajty. Określając `in` modyfikator, należy przekazać 4-bajtowych lub 8-bajtowych odwołania do tych argumentów, w zależności od architektury komputera. Różnica w rozmiarze jest mały, ale jego można szybko dodać po aplikacji wywołuje tę metodę w pętli ścisłej przy użyciu wielu różnych wartości.
 
`in` Uzupełnia modyfikator `out` i `ref` także inne sposoby. Nie można utworzyć przeciążenia metody, które różnią się jedynie w związku z występowaniem `in`, `out` lub `ref`. Te nowe reguły rozszerzania zawsze ma zdefiniowany dla tego samego zachowania `out` i `ref` parametrów.

`in` Modyfikator mogą być stosowane do dowolnego członka, który przyjmuje parametry: metody, delegatów, wyrażenia lambda, funkcje lokalne, indeksatorów, operatorów.

W odróżnieniu od `ref` i `out` argumenty, można użyć wartości literałów ani stałe dla argumentu `in` parametru. Ponadto, w przeciwieństwie do `ref` lub `out` parametr, nie trzeba zastosować `in` modyfikator w miejsce wywołania. Poniższy kod przedstawia dwa przykłady wywołania metody `CalculateDistance` metody. Pierwszy korzysta z dwóch zmiennych lokalnych przekazywana przez odwołanie. Drugi zawiera zmiennej tymczasowej utworzone jako część wywołania metody. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w których kompilator zapewnia, które tylko do odczytu rodzaj `in` argument jest wymuszana.  Przede wszystkim wywołaną metodę nie można przypisać bezpośrednio do `in` parametru. Bezpośrednio nie można przypisać do dowolnego pola `in` parametru. Ponadto nie można przekazać `in` parametr do dowolnej metody wymagających `ref` lub `out` modyfikator.
Wymusza kompilator, który `in` argument jest zmienną tylko do odczytu. Możesz wywołać dowolnej metody wystąpienia, która używa semantyki przebiegu wartości. W tych przypadkach kopię `in` utworzeniu parametru. Ponieważ kompilator można utworzyć zmiennej tymczasowej dla każdego `in` parametru, można również określić wartości domyślnej dla żadnego `in` parametru. Wykonaj kodu użyty do określenia pochodzenia (punkt 0,0) z wartością domyślną dla drugiego punktu:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

`in` Można również określenie parametru używane z typami odwołanie lub wbudowane wartości liczbowych. Jednak korzyści w obu przypadkach są minimalne, jeśli istnieje.

## <a name="ref-readonly-returns"></a>`ref readonly`Zwraca

Można również zwrócić przez odwołanie typu wartości, ale nie zezwalaj na obiekt wywołujący modyfikowanie tej wartości. Użyj `ref readonly` modyfikator Express celem tego projektu. Czy są zwracane jest odwołanie do istniejących danych, ale nie zezwala na modyfikowanie powiadomi czytników. 

Kompilator wymusza, że obiekt wywołujący nie można zmodyfikować odwołania. Próby bezpośrednio przypisać wartość generuje błąd kompilacji. Jednak kompilator nie wiadomo, jeśli metoda dowolnego elementu członkowskiego modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowany, kompilator tworzy kopię i wywołuje element członkowski odwołań za pomocą tej kopii. Wszystkie modyfikacje są obrony ją. 

Istnieje prawdopodobieństwo, że przy użyciu biblioteki `Point3D` często użyje źródła w całym kodzie. Każde wystąpienie tworzy nowy obiekt na stosie. Może być korzystne utworzyć stałą i zwracać jej przez odwołanie. Jednak jeśli zwraca odwołanie do wewnętrznej pamięci masowej, może zajść potrzeba wymuszenia, że obiekt wywołujący nie można zmodyfikować magazynu, do którego istnieje odwołanie. Poniższy kod definiuje właściwości tylko do odczytu, która zwraca `readonly ref` do `Point3D` , który określa punkt początkowy.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Tworzenie kopii tylko do odczytu ref zwracany jest prosty: tylko przypisz go do zmiennej, nie jest zadeklarowana z `ref readonly` modyfikator. Kompilator generuje kod, aby skopiować obiekt w ramach przypisania. 

Po przypisaniu zmiennej `ref readonly return`, można określić `ref readonly` zmiennej lub kopię przez wartość odwołania tylko do odczytu:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie tworzy kopię `Origin` stała i przypisuje, które skopiować. Drugi przypisuje odwołanie. Zwróć uwagę, że `readonly` modyfikator musi być częścią deklaracja zmiennej. Nie można zmodyfikować odwołania, do którego się odwołuje. Próbuje zrobić spowodować błąd kompilacji.

## <a name="readonly-struct-type"></a>`readonly struct`Typ

Stosowanie `ref readonly` na wykorzystanie dużym natężeniu ruchu struktury mogą być wystarczające.
Innym razem, można utworzyć niezmienialny struktury. Zawsze można następnie przekazać przez odwołanie tylko do odczytu. Czy rozwiązanie usuwa ataku kopiuje tego miejsce, gdy uzyskujesz dostęp do metody struktury używane jako `in` parametru.

Możesz to zrobić, tworząc `readonly struct` typu. Możesz dodać `readonly` modyfikatora w deklaracji struktury. Kompilator wymusza, że wszystkie elementy członkowskie wystąpień struktury są `readonly`; `struct` musi być niezmienialne.

Istnieją inne optymalizacje dla `readonly struct`. Można użyć `in` modyfikator w każdej lokalizacji gdzie `readonly struct` jest argumentem. Ponadto można zwrócić `readonly struct` jako `ref return` po zwróconego obiektu, którego okres istnienia wykracza poza zakres metoda zwraca obiekt.

Na koniec kompilator generuje kod efektywniejsze podczas wywoływania członkami `readonly struct`: `this` odwołania, zamiast kopiowania odbiornika, jest zawsze `in` parametr przekazywany przez odwołanie do elementu członkowskiego. Tego rodzaju optymalizacji zapisuje więcej kopiowania, korzystając z `readonly struct`. `Point3D` Jest doskonałym kandydatem do tej zmiany. Poniższy kod przedstawia zaktualizowaną `ReadonlyPoint3D` struktury:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct`Typ

Inna funkcja języka powiązane jest możliwość zadeklarować typu wartości, który musi znajdować się na stosie. Innymi słowy te typy nigdy nie można utworzyć na stercie członkiem innej klasy. Główną motywacją do tej funkcji został <xref:System.Span%601> i powiązanych struktury. <xref:System.Span%601>może zawierać wskaźnika zarządzane jako jeden z jego elementów członkowskich, inne są długość zakresu. Faktycznie wdrażana jest nieco inaczej ponieważ C# nie obsługuje wskaźników do pamięci zarządzanej poza niebezpiecznym kontekście. Wszelkie zapisu, która zmienia wskaźnika oraz długość nie jest atomic. Oznacza to, że <xref:System.Span%601> będzie podlegać poza zakresem błędy lub innego typu naruszenia bezpieczeństwa zostały nie ograniczone do ramki stosu pojedynczego. Ponadto zwykle umieszczenie wskaźnika zarządzanego na stercie GC ulega awarii podczas JIT.

Może być podobne wymagania dotyczące pracy z pamięci utworzone za pomocą [ `stackalloc` ](language-reference/keywords/stackalloc.md) lub w przypadku używania pamięci z międzyoperacyjnego interfejsów API. Można definiować własnych `ref struct` typy dla tych potrzeb. W tym artykule, zobacz przykłady użycia `Span<T>` dla uproszczenia.

`ref struct` Deklaracji deklaruje, że struktura tego typu musi być na stosie. Reguły języka zapewnienia bezpiecznego korzystania z tych typów. Inne typy zadeklarowane jako `ref struct` obejmują <xref:System.ReadOnlySpan%601>. 

Celem porządkowania `ref struct` typu jako zmienną przydzielony stos wprowadzono kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.

- Nie można polu `ref struct`. Nie można przypisać `ref struct` typ zmiennej typu `object`, `dynamic`, albo typu interfejsu.
- Nie można zadeklarować `ref struct` jako element członkowski klasy lub struktury normalnego.
- Nie można deklarować zmiennych lokalnych, które są `ref struct` typów w metodach asynchronicznych. Można je zadeklarować w metod synchronicznych, które zwracają `Task`, `Task<T>` lub typów zadań.
- Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.
- Nie można przechwycić `ref struct` zmiennych w wyrażeniach lambda lub funkcje lokalne.

Te ograniczenia upewnij się, że przypadkowo nieużywanie `ref struct` w taki sposób, który można podwyższyć sterty zarządzanej.

## <a name="conclusions"></a>Wnioski

Te ulepszenia języka C# są przeznaczone dla algorytmów krytyczne wydajności, których alokacji pamięci może być krytyczne znaczenie dla osiągnięcia niezbędne wydajności. Może się okazać, że nie są często używane te funkcje w kodzie zostanie zapisany. Jednak te ulepszenia zostały przyjęte w wielu lokalizacjach w programie .NET Framework. Jak coraz więcej interfejsów API należy używać tych funkcji, zobaczysz poprawy wydajności własnych aplikacji.
