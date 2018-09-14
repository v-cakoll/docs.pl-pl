---
title: Semantyka odwołań z typami wartości
description: Omówienie funkcji języka, które bezpiecznie zminimalizować kopiowania struktury
ms.date: 11/10/2017
ms.custom: mvc
ms.openlocfilehash: f241219994d7a03192a4aea69b912bf1ac5ed29c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592156"
---
# <a name="reference-semantics-with-value-types"></a>Semantyka odwołań z typami wartości

Zaletą używania typów wartości jest, aby uniknąć często alokacji sterty.
Wadą jest to, że są one kopiowane przez wartość. To kosztem utrudnienie Optymalizowanie algorytmów, które działają na dużych ilości danych. Nowe funkcje języka w języku C# 7.2 zapewniają mechanizmy, które umożliwiają semantyki przekazywany przez odwołanie z typami wartości. Należy uważnie używać tych funkcji do minimum zarówno alokacji i operacje kopiowania. W tym artykule przeanalizowano tych nowych funkcji.

Duża część przykładowego kodu w tym artykule przedstawiono funkcje dodane w języku C# 7.2. Aby można było używać tych funkcji, należy skonfigurować projekt do języka C# 7.2 lub nowsza. Aby uzyskać więcej informacji na temat ustawiania wersji języka zobacz [skonfigurować wersję językową](language-reference/configure-language-version.md).

## <a name="passing-arguments-by-readonly-reference"></a>Przekazywanie argumentów poprzez odwołanie tylko do odczytu

Dodaje w języku C# 7.2 `in` słowa kluczowego jako uzupełnienie istniejących `ref` i `out` słów kluczowych, aby przekazywać argumentów przez odwołanie. `in` — Słowo kluczowe Określa, przekazywanie argumentu przez odwołanie, ale wywoływanej metody nie modyfikuje wartości. 

To dodawanie zapewnia pełną słownictwa wyrażenia zgodną z planem projektu. Typy wartości są kopiowane, gdy przekazywane do metody o nazwie, jeśli nie określisz dowolną z następujących modyfikatorów w podpisie metody. Każda z tych modyfikatorów Określa, że typ wartości jest przekazywany przez odwołanie, unikając kopiowania. Każdy modyfikator wyraża innego zamiaru:

- `out`: Ta metoda ustawia wartość argumentu jako parametr.
- `ref`: Ta metoda może ustawić wartość argumentu jako parametr.
- `in`: Ta metoda nie modyfikuje wartość argumentu jako parametr.

Dodaj `in` modyfikator do przekazywania argumentu przez odwołanie i Zadeklaruj swoje założenia projektowe, aby przekazywać argumentów przez odwołanie, aby uniknąć niepotrzebnego kopiowania. Nie zamierzasz zmodyfikować obiekt używany w roli tego argumentu. Poniższy kod przedstawia przykład metody, które oblicza odległość między dwoma punktami w przestrzeni 3D. 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

Argumenty są dwie struktury, że każdy zawiera trzech liczb typu Double. Wartość o podwójnej precyzji jest 8 bajtów, dzięki czemu każdy argument jest 24 bajty. Określając `in` modyfikatora, należy przekazać odwołanie 4-bajtowych lub 8 bajtów do tych argumentów, w zależności od architektury komputera. Różnica w rozmiarze jest mała, ale jego można szybko dodać gdy Twoja aplikacja wywołuje tę metodę w pętli za pomocą wielu różnych wartości.
 
`in` Uzupełniające modyfikator `out` i `ref` w inny sposób, jak również. Nie można utworzyć przeciążenia metody, które różnią się tylko w obecności właściwości `in`, `out`, lub `ref`. Te nowe reguły rozszerzyć takie samo zachowanie, które zawsze miały zostały zdefiniowane dla `out` i `ref` parametrów.

`in` Modyfikator mogą być stosowane do wszystkich elementów członkowskich, która przyjmuje parametry: metod delegatów, wyrażeń lambda, funkcji lokalnych, indeksatory, operatorów.

W odróżnieniu od `ref` i `out` argumentów, możesz użyć wartości literałów lub stałe dla argumentu dla `in` parametru. Ponadto, w odróżnieniu od `ref` lub `out` parametru, nie trzeba zastosować `in` modyfikator w witrynie wywołania. Poniższy kod pokazuje dwa przykłady wywoływania `CalculateDistance` metody. Pierwszy używa dwóch zmiennych lokalnych, przekazywany przez odwołanie. Drugi zawiera zmienną tymczasową utworzonych jako część wywołania metody. 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w których kompilator zapewnia, które tylko do odczytu rodzaj `in` argument jest wymuszany.  Po pierwsze, wywoływanej metody nie można przypisać bezpośrednio do `in` parametru. Bezpośrednio nie można przypisać do dowolnego pola `in` parametr, gdy ta wartość jest `struct` typu. Ponadto nie można przekazać `in` parametr przy użyciu dowolnej metody `ref` lub `out` modyfikator.
Te reguły mają zastosowanie do dowolnego pola `in` parametru podane, pole jest `struct` typu, a parametr jest również `struct` typu. W rzeczywistości te reguły stosuje się na wiele warstw dostępu do elementu członkowskiego, pod warunkiem typy na wszystkich poziomach dostępu do elementu członkowskiego `structs`. Kompilator wymusza, który `struct` typy przekazane jako `in` argumentów i ich `struct` elementy członkowskie są zmienne tylko do odczytu, gdy jest używana jako argumenty do innych metod.

Korzystanie z `in` parametry pozwala uniknąć potencjalnych kosztów wydajności tworzenia kopii. Nie zmienia semantykę każde wywołanie metody. W związku z tym, nie należy określić `in` modyfikator w witrynie wywołania. Jednakże, pomijając `in` modyfikator w witrynie wywołania informuje kompilator, że może on być kopię argumentu z następujących powodów:

- Istnieje niejawna konwersja, ale nie tożsamość konwersję z typu argumentu z typem parametru.
- Argument jest wyrażeniem, ale nie ma zmienną znanych magazynu.
- Istnieje przeciążenie różni się obecności lub braku `in`. W takim przypadku według wartości przeciążenia ma lepsze dopasowanie.

Reguły te są przydatne w przypadku aktualizowania istniejącego kodu do argumenty odwołania tylko do odczytu. Wewnątrz metody o nazwie możesz wywołać dowolnej metody wystąpienia, która używa parametrów wielowartościowych. W tych przypadkach kopię `in` utworzeniu parametru. Ponieważ kompilator może tworzyć zmiennej tymczasowej dla każdej `in` parametru, można również określić wartości domyślnych dla każdej `in` parametru. Poniższy kod określa pochodzenia (punkt 0,0) jako wartość domyślna dla drugi punkt:

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Aby wymusić na kompilatorze odczytu tylko argument jest przekazywany przez odwołanie, należy określić `in` modifer dla argumentów w witrynie wywołania, jak pokazano w poniższym kodzie:

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#ExplicitInArgument "Specifying an In argument")]

To zachowanie ułatwia przyjęcie `in` parametrów wraz z upływem czasu w dużych bazach kodu, gdzie możliwe są wzrost wydajności. Możesz dodać `in` modyfikatora podpisy metod pierwszy. Następnie należy dodać `in` modyfikator na callsites i utworzyć `readonly struct` typy umożliwiające kompilatorowi unikanie tworzenia kopii obrony `in` parametrów w większej liczby lokalizacji.

`in` Nazwy parametru może również służyć za pomocą typów referencyjnych lub wartości liczbowych. Jednak korzyści w obu przypadkach są minimalne, jeśli istnieje.

## <a name="ref-readonly-returns"></a>`ref readonly` Zwraca

Można również zwrócić przez odwołanie, typ wartości, ale zabronić wywołującego od modyfikowania tej wartości. Użyj `ref readonly` modyfikatora express przeznaczenie tego projektu. Czy są zwracanie odwołania do istniejących danych, ale nie zezwala na modyfikowanie, powiadamia czytników. 

Kompilator wymusza to, że obiekt wywołujący nie można zmodyfikować odwołania. Podejmowana jest próba przypisania wartości bezpośrednio wygenerować błąd kompilacji. Jednak kompilator nie wiadomo, jeśli metoda dowolnego elementu członkowskiego modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowany, kompilator tworzy kopię i wywołuje element członkowski odwołań za pomocą tej kopii. Wszystkie modyfikacje są tym kopia obronna. 

Istnieje prawdopodobieństwo, że przy użyciu biblioteki `Point3D` często użyje źródła w całym kodzie. Każde wystąpienie tworzy nowy obiekt na stosie. Może być korzystne, aby utworzyć stałą i przywrócić go przez odwołanie. Jednak jeśli zwracane odwołanie do pamięci wewnętrznej, możesz chcieć wymusić, że obiekt wywołujący nie można zmodyfikować odwołania magazynu. Poniższy kod definiuje właściwość tylko do odczytu, która zwraca `readonly ref` do `Point3D` , który określa punkt początkowy.

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

Tworzenie kopii tylko do odczytu ref zwracany jest proste: wystarczy przypisać ją do zmiennej nie jest zadeklarowana za pomocą `ref readonly` modyfikator. Kompilator generuje kod, aby skopiować obiekt w ramach przypisania. 

Po przypisaniu zmiennej, aby `ref readonly return`, można określić `ref readonly` zmiennej lub kopię przez wartość odniesienia tylko do odczytu:

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie tworzy kopię `Origin` stałych i przypisuje kopiujących. Drugi przypisuje odwołania. Należy zauważyć, że `readonly` modyfikator musi być częścią deklaracja zmiennej. Nie można zmodyfikować odwołania, do którego się odwołuje. Próba wykonania tej czynności powoduje błąd kompilacji.

## <a name="readonly-struct-type"></a>`readonly struct` Typ

Stosowanie `ref readonly` do zastosowań o dużym natężeniu ruchu struktury mogą być wystarczające.
W innych sytuacjach można utworzyć niemodyfikowalny struktury. Zawsze można następnie przekazać według odwołania tylko do odczytu. Czy rozwiązanie usuwa ataku kopiuje tego miejsce, gdy uzyskujesz dostęp do metod struktury, używane jako `in` parametru.

Możesz to zrobić, tworząc `readonly struct` typu. Możesz dodać `readonly` modyfikatora deklaracji struktury. Kompilator wymusza na to, że wszystkie składowe wystąpienia struktury są `readonly`; `struct` musi być niezmienialne.

Istnieją inne optymalizacje dla `readonly struct`. Możesz użyć `in` modyfikator w każdym miejscu gdzie `readonly struct` jest argumentem. Ponadto, można zwrócić `readonly struct` jako `ref return` kiedy jest zwracany obiekt, którego okres istnienia wykracza poza zakres metoda zwraca obiekt.

Na koniec, kompilator generuje kod bardziej efektywne, gdy wywołujesz członkowie `readonly struct`: `this` odwołanie, zamiast kopii receiver, jest zawsze `in` parametr przekazywany przez odwołanie do elementu członkowskiego. Tego rodzaju optymalizacji zapisuje więcej kopiowanie, gdy używasz `readonly struct`. `Point3D` Jest doskonałym kandydatem do tej zmiany. Poniższy kod przedstawia zaktualizowaną `ReadonlyPoint3D` strukturę:

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` Typ

Kolejną funkcją języka powiązane jest zdolność do deklarowania typu wartości, która musi być na stosie. Innymi słowy te typy nigdy nie można utworzyć na stosie jest członkiem innej klasy. Główną motywacją do tej funkcji został <xref:System.Span%601> i pokrewne struktury. <xref:System.Span%601> może zawierać wskaźnika zarządzanych jako jeden z jej członków, inne są długość zakresu. Wdrażana jest nieco inaczej ponieważ języka C# nie obsługuje wskaźników do pamięci zarządzanej poza niebezpieczny kontekst. Wszelkie zapisu, która zmienia się wskaźnik i długość nie jest atomic. Oznacza to, że <xref:System.Span%601> byłoby podlegają poza zakresem błędy lub inne naruszenia bezpieczeństwa typu nie, nie jest ona ograniczona do ramki stosu. Ponadto umieszczenie wskaźnika zarządzanych na stercie GC zazwyczaj kończy się niepowodzeniem w momencie JIT.

Masz podobnych wymaganiach dotyczących pracy z pamięcią utworzone za pomocą [ `stackalloc` ](language-reference/keywords/stackalloc.md) lub w przypadku używania pamięci za pomocą międzyoperacyjnych interfejsów API. Definiowanie swoich własnych `ref struct` typy dla tych wymagań. W tym artykule, zobacz przykłady użycia `Span<T>` dla uproszczenia.

`ref struct` Deklaracji deklaruje strukturę tego typu muszą znajdować się na stosie. Reguły języka zapewnienia bezpiecznego korzystania z tych typów. Inne typy zadeklarowane jako `ref struct` obejmują <xref:System.ReadOnlySpan%601>. 

Celem zachowywaniu `ref struct` wpisz zmienną przydzielanych ze stosów wprowadza kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.

- Nie można polu `ref struct`. Nie można przypisać `ref struct` typ do zmiennej typu `object`, `dynamic`, lub dowolny typ interfejsu.
- Nie można zadeklarować `ref struct` jako członek klasy lub struktury normalny.
- Nie można zadeklarować zmienne lokalne, które są `ref struct` typów w metodach asynchronicznych. Można zadeklarować je metod synchronicznych, które zwracają `Task`, `Task<T>` lub typu przypominającego zadanie.
- Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.
- Nie można dokonać przechwytu `ref struct` zmiennych w wyrażeniach lambda lub funkcji lokalnych.

Te ograniczenia, upewnij się, nie używasz przypadkowo `ref struct` w taki sposób, który można podwyższyć poziom do zarządzanej sterty.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Typ

Deklarowanie struktury jako `readonly ref` łączy korzyści i ograniczeń dotyczących `ref struct` i `readonly struct` deklaracji. 

W poniższym przykładzie pokazano deklaracji `readonly ref struct`.

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    public ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>Wnioski

Te ulepszenia języka C# są przeznaczone dla algorytmów krytyczne wydajności, gdzie alokacji pamięci może być mają kluczowe znaczenie dla osiągnięcia niezbędne wydajności. Może się okazać, że nie są często używane funkcje te w kodzie, którą piszesz. Jednak te ulepszenia zostały przyjęte w wielu lokalizacjach w programie .NET Framework. Ponieważ coraz więcej interfejsy API korzystać z tych funkcji, zobaczysz wydajności własnych aplikacji, zwiększyć.
