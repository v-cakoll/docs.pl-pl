---
title: Korzystanie z właściwości — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: d873f626b660bb6bd94710add4543e21e11823d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77452022"
---
# <a name="using-properties-c-programming-guide"></a>Używanie właściwości (Przewodnik programowania w języku C#)

Właściwości łączą aspekty zarówno pól, jak i metod. Dla użytkownika obiektu właściwość wydaje się być polem, dostęp do właściwości wymaga tej samej składni. Do realizatora klasy właściwość jest jeden lub dwa bloki kodu, [reprezentujących get](../../language-reference/keywords/get.md) akcesor i/lub [set](../../language-reference/keywords/set.md) akcesor. Blok kodu dla `get` akcesora jest wykonywany, gdy właściwość jest odczytywana; blok kodu dla `set` akcesora jest wykonywany, gdy właściwość jest przypisana nowa wartość. Właściwość bez `set` akcesora jest uważana za tylko do odczytu. Właściwość bez `get` akcesora jest uważany tylko do zapisu. Właściwość, która ma zarówno akcesorów jest odczytu i zapisu.

W przeciwieństwie do pól właściwości nie są klasyfikowane jako zmienne. W związku z tym nie można przekazać właściwość jako [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) parametru.

Właściwości mają wiele zastosowań: mogą sprawdzać poprawność danych przed zezwoleniem na zmianę; mogą one w sposób przejrzysty uwidaczniać dane w klasie, w której dane te są faktycznie pobierane z innego źródła, takiego jak baza danych; mogą podjąć akcję po zmianie danych, na przykład podniesienie zdarzenia lub zmianę wartości innych pól.

Właściwości są deklarowane w bloku klasy, określając poziom dostępu pola, a następnie typ właściwości, a następnie nazwę właściwości, a następnie `get`blok kodu, który `set` deklaruje -akcesor i/lub akcesor. Przykład:

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

W tym `Month` przykładzie jest zadeklarowany jako `set` właściwość, dzięki czemu `Month` akcesor może upewnić się, że wartość jest ustawiona między 1 i 12. Właściwość `Month` używa pola prywatnego do śledzenia rzeczywistej wartości. Rzeczywista lokalizacja danych właściwości jest często określana jako "magazyn zapasowy" właściwości. Jest wspólne dla właściwości do używania pól prywatnych jako magazynu zapasowego. Pole jest oznaczone jako prywatne, aby upewnić się, że można je zmienić tylko przez wywołanie właściwości. Aby uzyskać więcej informacji na temat ograniczeń dostępu publicznego i prywatnego, zobacz [Modyfikatory dostępu](./access-modifiers.md).

Właściwości implementowane automatycznie zapewniają uproszczoną składnię dla deklaracji właściwości prostych. Aby uzyskać więcej informacji, zobacz [Właściwości implementowane automatycznie](auto-implemented-properties.md).

## <a name="the-get-accessor"></a>Get Accessor (Pobierz akcesor)

Treść metody `get` akcesora przypomina metodę. Musi zwrócić wartość typu właściwości. Wykonanie akcesorjest `get` odpowiednikiem odczytu wartości pola. Na przykład podczas zwracania zmiennej prywatnej `get` z akcesora i optymalizacje są włączone, wywołanie metody `get` akcesorjest inlined przez kompilator, więc nie ma żadnych metody wywołania narzutów. Jednak metoda `get` wirtualnego akcesora nie może być wbudowane, ponieważ kompilator nie wie w czasie kompilacji, która metoda może faktycznie być wywoływana w czasie wykonywania. Poniżej znajduje `get` się akcesor, który `_name`zwraca wartość pola prywatnego:

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

Podczas odwoływania się do właściwości, z wyjątkiem `get` jako miejsce docelowe przypisania, akcesor jest wywoływany do odczytu wartości właściwości. Przykład:

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

Akcesor `get` musi kończyć się return [lub](../../language-reference/keywords/return.md) [throw](../../language-reference/keywords/throw.md) instrukcji i kontroli nie może spływać z treści akcesora.

Jest to zły styl programowania, aby zmienić stan `get` obiektu za pomocą akcesora. Na przykład następujący akcesor tworzy efekt uboczny zmiany stanu `_number` obiektu za każdym razem, gdy pole jest dostępne.

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

Akcesor `get` może służyć do zwracania wartości pola lub do obliczania go i zwracania go. Przykład:

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

W poprzednim segmencie kodu, jeśli wartość nie `Name` zostanie przypisana `NA`do właściwości, zwróci wartość .

## <a name="the-set-accessor"></a>Zestaw Akcesor

Akcesor `set` przypomina metodę, której typ zwracany jest [nieważny](../../language-reference/builtin-types/void.md). Używa niejawnego `value`parametru o nazwie , którego typ jest typem właściwości. W poniższym `set` przykładzie akcesor `Name` jest dodawany do właściwości:

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

Po przypisaniu wartości do `set` właściwości, akcesor jest wywoływany przy użyciu argumentu, który zapewnia nową wartość. Przykład:

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

Jest to błąd, aby użyć `value`nazwy parametru niejawnego, dla deklaracji zmiennej lokalnej w akcesorze. `set`

## <a name="remarks"></a>Uwagi

Właściwości mogą być `public`oznaczone `private` `protected`jako `internal` `protected internal` , `private protected`, , lub . Te modyfikatory dostępu definiują, w jaki sposób użytkownicy klasy mogą uzyskać dostęp do właściwości. Akcesory `get` dla `set` tej samej właściwości mogą mieć różne modyfikatory dostępu. Na przykład `get` może `public` być, aby umożliwić dostęp tylko do `set` odczytu `private` `protected`z zewnątrz typu, a może być lub . Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).

Właściwość może być zadeklarowana jako właściwość `static` statyczna przy użyciu słowa kluczowego. Dzięki temu właściwość jest dostępna dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).

Właściwość może być oznaczona jako właściwość wirtualna przy użyciu [wirtualnego](../../language-reference/keywords/virtual.md) słowa kluczowego. Dzięki temu klasy pochodne zastąpić zachowanie właściwości przy użyciu [przesłoń](../../language-reference/keywords/override.md) słowa kluczowego. Aby uzyskać więcej informacji na temat tych opcji, zobacz [Dziedziczenie](inheritance.md).

Właściwość zastępująca właściwość wirtualną może być również [zapieczętowana,](../../language-reference/keywords/sealed.md)określając, że dla klas pochodnych nie jest już wirtualny. Wreszcie właściwość można zadeklarować [abstrakcyjne](../../language-reference/keywords/abstract.md). Oznacza to, że nie ma implementacji w klasie i klasy pochodne należy napisać własną implementację. Aby uzyskać więcej informacji na temat tych opcji, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Członkowie klasy](abstract-and-sealed-classes-and-class-members.md).
  
> [!NOTE]
> Jest to błąd, aby użyć [wirtualnego,](../../language-reference/keywords/virtual.md) [abstrakcyjne](../../language-reference/keywords/abstract.md)lub [zastąpić](../../language-reference/keywords/override.md) modyfikator akcesor właściwości [statycznej.](../../language-reference/keywords/static.md)

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono właściwości wystąpienia, statyczne i tylko do odczytu. Akceptuje nazwisko pracownika z klawiatury, zwiększa o `NumberOfEmployees` 1 i wyświetla imię i nazwisko pracownika oraz numer.

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak uzyskać dostęp do właściwości w klasie podstawowej, która jest ukryta przez inną właściwość, która ma taką samą nazwę w klasie pochodnej:

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

Poniżej przedstawiono ważne punkty w poprzednim przykładzie:

- Właściwość `Name` w klasie pochodnej ukrywa `Name` właściwość w klasie podstawowej. W takim przypadku `new` modyfikator jest używany w deklaracji właściwości w klasie pochodnej:

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- Rzutowany `(Employee)` służy do uzyskiwania dostępu do ukrytej właściwości w klasie podstawowej:

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     Aby uzyskać więcej informacji na temat ukrywania elementów członkowskich, zobacz [nowy modyfikator](../../language-reference/keywords/new-modifier.md).

## <a name="example"></a>Przykład

W tym przykładzie dwie `Cube` `Square`klasy i , `Shape`implementuj klasę `Area` abstrakcyjną i zastępują jej właściwość abstrakcyjną. Należy zwrócić uwagę na użycie modyfikatora [zastępowania](../../language-reference/keywords/override.md) we właściwościach. Program akceptuje stronę jako dane wejściowe i oblicza obszary kwadratu i sześcianu. Akceptuje również obszar jako dane wejściowe i oblicza odpowiednią stronę kwadratu i sześcianu.

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Właściwości](properties.md)
- [Właściwości interfejsu](interface-properties.md)
- [Właściwości zaimplementowane automatycznie](auto-implemented-properties.md)
