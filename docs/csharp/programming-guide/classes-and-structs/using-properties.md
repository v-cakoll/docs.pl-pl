---
title: "Używanie właściwości (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aae36195f4a6eb2ab49ec27e1e07debff7289b37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-properties-c-programming-guide"></a>Używanie właściwości (Przewodnik programowania w języku C#)
Właściwości łączyć aspekty pól i metod. Użytkownikowi obiektu właściwości wydaje się być polem, uzyskiwanie dostępu do właściwości wymaga takiej samej składni. Realizator klasę, właściwości jest jeden lub dwa bloki kodu, reprezentujący [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu i/lub [ustawić](../../../csharp/language-reference/keywords/set.md) metody dostępu. Blok kodu dla `get` metody dostępu jest wykonywany podczas odczytywania właściwości; zablokować kod `set` metody dostępu jest wykonywane, gdy właściwość jest przypisywana nowa wartość. Właściwość bez `set` metody dostępu jest traktowane jako tylko do odczytu. Właściwość bez `get` metody dostępu jest traktowane jako tylko do zapisu. Właściwość, która ma obu metod dostępu jest do odczytu / zapisu.  
  
 W przeciwieństwie do pola właściwości nie są sklasyfikowane jako zmienne. W związku z tym nie można przekazać właściwości jako [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametru.  
  
 Właściwości mają wiele zastosowań: one sprawdzanie poprawności danych przed zezwoleniem na zmianę; przezroczysty mogą uwidaczniać danych dla klasy, których dane faktycznie jest pobierana z innego źródła, na przykład w bazie danych; Po zmianie danych, takich jak wywoływanie zdarzeń lub zmiana wartości innych pól potencjalnie akcji.  
  
 Właściwości są zadeklarowane w bloku klasy, określając poziom dostępu do pola, następuje typ właściwości następuje nazwa właściwości i następuje blok kodu, który deklaruje `get`-metody dostępu i/lub `set` dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 W tym przykładzie `Month` jest zadeklarowany jako właściwość tak że `set` akcesor można upewnij się, że `Month` wartość od 1 do 12. `Month` Właściwość używa prywatnego pola do śledzenia rzeczywistej wartości. Rzeczywista lokalizacja danych właściwości jest często określany jako wartość właściwości "magazynu zapasowego." Bardzo często właściwości do użycia jako magazynu zapasowego pól prywatnych. Pole jest oznaczony jako prywatny, aby mieć pewność, że jego można zmienić tylko po wywołaniu właściwości. Aby uzyskać więcej informacji na temat ograniczeń dostępu publicznego i prywatnego, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Właściwości zaimplementowane automatycznie Podaj składni uproszczoną deklaracje właściwości prostej. Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Metody dostępu get  
 Treść `get` akcesor podobny, które metody. Aplikacja musi zwracać wartość typu właściwości. Wykonywanie `get` metody dostępu jest odpowiednikiem odczytywania wartości pola. Na przykład podczas zwracania zmiennej prywatnej z `get` metody dostępu i optymalizację, które są włączone, można wywołać `get` metodę dostępu jest umieszczona w tekście przez kompilator, więc nie ma całkowitej wywołania metody. Jednak wirtualnej `get` metodę dostępu nie można wbudować elementu, ponieważ kompilator nie wie, w czasie kompilacji, która metoda faktycznie może zostać wywołana w czasie wykonywania. Poniżej przedstawiono `get` akcesor zwracającej wartość pola prywatne `name`:  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Podając odniesienie właściwości, z wyjątkiem jako elementem docelowym przypisania, `get` metody dostępu jest wywoływane w celu odczytu wartości właściwości. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 `get` Akcesora musi kończyć się [zwracać](../../../csharp/language-reference/keywords/return.md) lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji i kontroli przepływu nie można wyłączyć treści metody dostępu.  
  
 Jest zła styl programowania zmiany stanu obiektu przy użyciu `get` metody dostępu. Na przykład następujące metody dostępu tworzy ubocznym zmiany stanu obiektu za każdym razem, który `number` uzyskiwania dostępu do pola.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 `get` Metody dostępu może służyć do zwrócenia wartości pola lub na potrzeby obliczania go i przywrócić go. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 W poprzednich segment kodu, jeśli wartość nie należy przypisywać `Name` właściwości, zwróci wartość NA.  
  
## <a name="the-set-accessor"></a>Zestaw metody dostępu  
 `set` Akcesor podobny metody, których typem zwracanym jest [void](../../../csharp/language-reference/keywords/void.md). Niejawny parametr o nazwie `value`, którego typem jest typ właściwości. W poniższym przykładzie `set` metody dostępu jest dodawany do `Name` właściwości:  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Podczas przypisywania wartości do właściwości, `set` metody dostępu jest wywoływana przy użyciu argumentu, który udostępnia nową wartość. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 Błąd do używania nazwy parametru niejawne `value`, dla deklaracji zmiennej lokalnej w `set` metody dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości może być oznaczony jako `public`, `private`, `protected`, `internal`, `protected internal` lub `private protected`. Te modyfikatorów dostępu zdefiniuj, jak użytkownicy klasy mogą uzyskiwać dostęp do właściwości. `get` i `set` metody dostępu dla tej właściwości może mieć modyfikatorów dostępu do innego. Na przykład `get` może być `public` się zezwolić na dostęp tylko do odczytu z zewnątrz typu i `set` może być `private` lub `protected`. Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Można zadeklarować właściwości jako właściwość statyczna przy użyciu `static` — słowo kluczowe. To udostępnienie właściwości wywołań w dowolnym momencie, nawet jeśli nie ma wystąpień klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Właściwość może być oznaczony jako właściwość wirtualnego przy użyciu [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe. Dzięki temu klasy pochodne zastąpić zachowanie właściwości przy użyciu [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe. Aby uzyskać więcej informacji o tych opcjach, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Można także właściwością zastępowania wirtualnego właściwości [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), określania, czy dla klas pochodnych nie jest już wirtualny. Ponadto można zadeklarować jako właściwości [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md). Oznacza to, że nie żadnej implementacji klasy, i klasy pochodne napisać własne implementacji. Aby uzyskać więcej informacji o tych opcjach, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Jest błędem [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md), lub [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator na akcesor [statycznych](../../../csharp/language-reference/keywords/static.md) właściwości.  
  
## <a name="example"></a>Przykład  
 W przykładzie pokazano właściwości wystąpienia, statyczne i tylko do odczytu. Przyjmuje nazwę pracowników z klawiatury, zwiększa `NumberOfEmployees` 1 i wyświetla pracownik Określanie nazwy i numer.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób dostępu do właściwości w klasie podstawowej, który jest ukryty przez inną właściwość, która ma taką samą nazwę w klasie pochodnej.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Poniżej przedstawiono ważne punktów w poprzednim przykładzie:  
  
-   Właściwość `Name` w klasie pochodnej ukrywa właściwość `Name` w klasie podstawowej. W takim przypadku `new` modyfikator jest używany w deklaracji właściwości w klasie pochodnej:  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   Rzutowanie `(Employee)` służy do dostępu do ukrytych właściwości w klasie podstawowej:  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Aby uzyskać więcej informacji na składniki ukrywanie informacje, zobacz [new — modyfikator](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dwie klasy `Cube` i `Square`, zaimplementować klasę abstrakcyjną `Shape`i zastąp jego abstrakcyjny `Area` właściwości. Zwróć uwagę na użycie [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator we właściwościach. Program akceptuje po stronie jako dane wejściowe i oblicza obszarów kwadratowych i modułu. Również akceptuje obszaru jako dane wejściowe i oblicza odpowiednie po stronie kwadratowych i modułu.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
 [Właściwości zaimplementowane automatycznie](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
