---
title: Za pomocą właściwości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: 6aabdf9956365548d3f0cdf0cd046343d8129f04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560748"
---
# <a name="using-properties-c-programming-guide"></a>Używanie właściwości (Przewodnik programowania w języku C#)
Właściwości łączenia aspektów pola i metody. Do użytkownika obiektu Właściwość wydaje się być pola, uzyskanie dostępu do właściwości wymaga takiej samej składni. Właściwość implementujący klasę, jest co najmniej dwóch bloków kodu, reprezentujący [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu i/lub [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu. Blok kodu dla `get` metody dostępu jest wykonywany, gdy właściwość jest do odczytu; kod zablokować na `set` metody dostępu jest wykonywany, gdy właściwość jest przypisywana nowa wartość. Właściwość bez `set` metody dostępu jest traktowane jako tylko do odczytu. Właściwość bez `get` metody dostępu jest traktowane jako tylko do zapisu. Właściwość, która ma obu metod dostępu jest do odczytu i zapisu.  
  
 W przeciwieństwie do pola właściwości nie są klasyfikowane jako zmienne. W związku z tym, nie można przekazać właściwość jako [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru.  
  
 Właściwości mają wiele zastosowań: sprawdzają poprawność danych przed zezwoleniem na zmianę; sposób niewidoczny dla użytkownika mogą uwidaczniać dane dla klasy, gdzie te dane faktycznie jest pobierana z innego źródła, takich jak bazy danych. wykonywanie akcji po zmianie danych, takich jak wywoływanie zdarzenia lub zmiany wartości w pozostałych polach.  
  
 Właściwości są zadeklarowane w bloku klasy, określając poziom dostępu do pola, następuje typu właściwości, następuje nazwa właściwości i następuje blok kodu, który deklaruje `get`— metody dostępu i/lub `set` metody dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 W tym przykładzie `Month` jest zadeklarowana jako właściwość tak, `set` dostępu można upewnij się, że `Month` wartość od 1 do 12. `Month` Właściwość używa prywatnego pola do śledzenia wartości rzeczywistej. Rzeczywista lokalizacja danych właściwości jest często określana jako wartość właściwości "magazyn zapasowy." Jest to typowe dla właściwości, aby używać pól prywatnych jako magazyn zapasowy. Pole jest oznaczony prywatnych, aby upewnić się, że tylko można ją zmienić, wywołując właściwości. Aby uzyskać więcej informacji na temat ograniczeń dostępu publicznego i prywatnego, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Właściwości zaimplementowane automatycznie zapewnia uproszczoną składnię dla właściwości prostej deklaracji. Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Metody dostępu get  
 Treść `get` akcesor przypomina metody. Aplikacja musi zwracać wartość typu właściwości. Wykonanie `get` metody dostępu jest odpowiednikiem odczytywania wartości pola. Na przykład, gdy przekazujących zmiennej prywatnej z `get` metody dostępu i optymalizacje są włączone, wywołanie `get` metody dostępu jest śródwierszowa przez kompilator, więc nie ma żadnych obciążenie wywołania metody. Jednak wirtualnej `get` metody dostępu nie może być śródwierszowa, ponieważ kompilator nie zna w czasie kompilacji, która metoda może faktycznie wywołana w czasie wykonywania. Poniżej przedstawiono `get` metodę dostępu, która zwraca wartość pola prywatnego `name`:  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Gdy odwołujesz się właściwości, z wyjątkiem jako element docelowy przypisania `get` metody dostępu jest wywoływany ma zostać odczytana wartość właściwości. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 `get` Dostępu może kończyć się [zwracają](../../../csharp/language-reference/keywords/return.md) lub [throw](../../../csharp/language-reference/keywords/throw.md) poufności i kontroli, nie można wykonać przepływu off treści metody dostępu.  
  
 To zły stylu programowania, aby zmienić stan obiektu przy użyciu `get` metody dostępu. Na przykład, następujące metody dostępu daje efekt uboczny zmiany stanu obiektu za każdym razem, gdy który `number` uzyskiwania dostępu do pola.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 `get` Dostępu może służyć do zwrócenia wartości pola lub do obliczenia, go i przywrócić go. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 W poprzednich segment kodu, jeśli wartość nie należy przypisywać `Name` właściwości zwróci wartość, nie dotyczy.  
  
## <a name="the-set-accessor"></a>Zestaw metody dostępu  
 `set` Akcesor podobne metody, którego typem zwracanym jest [void](../../../csharp/language-reference/keywords/void.md). Niejawny parametr o nazwie `value`, którego typem jest typ właściwości. W poniższym przykładzie `set` metody dostępu jest dodawany do `Name` właściwości:  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Podczas przypisywania wartości do właściwości `set` metody dostępu jest wywoływany przy użyciu argumentu, który zawiera nową wartość. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 Jest to błąd, aby użyć nazwy parametru niejawne `value`, dla deklaracji zmiennej lokalnej w `set` metody dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości może być oznaczona jako `public`, `private`, `protected`, `internal`, `protected internal` lub `private protected`. Następujące modyfikatory dostępu Określ, jak użytkownicy klasy można uzyskiwać dostęp do właściwości. `get` i `set` metody dostępu dla tej właściwości może mieć modyfikatorów dostępu innego. Na przykład `get` może być `public` Aby zezwolić na dostęp tylko do odczytu z zewnątrz typu i `set` może być `private` lub `protected`. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
 Właściwości mogą być deklarowane jako właściwość statyczna za pomocą `static` — słowo kluczowe. To udostępnienie właściwości dotyczące obiektów wywołujących w dowolnym momencie, nawet jeśli istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Właściwość może być oznaczony jako właściwość wirtualną przy użyciu [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe. Dzięki temu klasy pochodne, aby zastąpić zachowanie właściwości za pomocą [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe. Aby uzyskać więcej informacji o tych opcjach, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Właściwości zastępowania wirtualnego właściwości może być również [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), określając, że dla klas pochodnych nie jest już wirtualny. Ponadto można zadeklarować właściwości [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md). Oznacza to, że nie ma żadnej implementacji w klasie, i musi być zapisana zapewniali własną implementację klasy pochodne. Aby uzyskać więcej informacji o tych opcjach, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Jest to błąd, aby użyć [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md), lub [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator na akcesor [statyczne](../../../csharp/language-reference/keywords/static.md) właściwości.  
  
## <a name="example"></a>Przykład  
 W przykładzie pokazano właściwości wystąpienia statyczne i tylko do odczytu. Przyjmuje nazwę pracowników z klawiatury, zwiększa `NumberOfEmployees` 1, a pracownik Wyświetla nazwę i numer.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób dostępu do właściwości w klasie bazowej, które zostały ukryte przez inną właściwość, która ma taką samą nazwę w klasie pochodnej.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Poniżej przedstawiono ważne punkty w poprzednim przykładzie:  
  
-   Właściwość `Name` w klasie pochodnej ukrywa właściwość `Name` w klasie bazowej. W takim przypadku `new` modyfikator jest używany w deklaracji właściwości w klasie pochodnej:  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   Rzutowanie `(Employee)` służy do dostępu do ukrytych właściwości w klasie bazowej:  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Aby uzyskać więcej informacji na temat elementów członkowskich ukrywanie zobacz [new — modyfikator](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dwie klasy `Cube` i `Square`, implementowanie klasy abstrakcyjnej `Shape`i zastąp jego abstrakcyjny `Area` właściwości. Zwróć uwagę na użycie [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator we właściwościach. Program akceptuje po stronie jako dane wejściowe i oblicza obszarów kwadratowych i modułów. Również akceptuje obszaru jako dane wejściowe i oblicza odpowiedniego po stronie kwadratowych i modułów.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)
- [Właściwości zaimplementowane automatycznie](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
