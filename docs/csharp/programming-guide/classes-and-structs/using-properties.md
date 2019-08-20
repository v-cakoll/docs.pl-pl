---
title: Korzystanie z właściwości C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: ff43fa1d3019af5cd08f86704a05531120201d17
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596022"
---
# <a name="using-properties-c-programming-guide"></a>Używanie właściwości (Przewodnik programowania w języku C#)
Właściwości łączą aspekty obu pól i metod. Dla użytkownika obiektu Właściwość wydaje się być polem, a dostęp do właściwości wymaga tej samej składni. Do realizatora klasy, właściwość to jeden lub dwa bloki kodu reprezentujące akcesor [Get](../../language-reference/keywords/get.md) i/lub [zestaw](../../language-reference/keywords/set.md) metod dostępu. Blok kodu dla `get` metody dostępu jest wykonywany, gdy właściwość jest odczytana; blok kodu `set` dla metody dostępu jest wykonywany, gdy do właściwości zostanie przypisana nowa wartość. Właściwość bez `set` metody dostępu jest traktowana jako tylko do odczytu. Właściwość bez `get` metody dostępu jest traktowana jako tylko do zapisu. Właściwość, która ma obu metod dostępu jest do odczytu i zapisu.  
  
 W przeciwieństwie do pól, właściwości nie są klasyfikowane jako zmienne. W związku z tym nie można przekazać właściwości jako parametru [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) .  
  
 Właściwości mają wiele użycia: mogą sprawdzać poprawność danych przed zezwoleniem na zmianę; mogą w niewidoczny sposób ujawniać dane w klasie, w której dane są pobierane z innych źródeł, takich jak baza danych; mogą oni wykonać akcję, gdy dane są zmieniane, takie jak podnoszenie zdarzenia lub zmiana wartości innych pól.  
  
 Właściwości są deklarowane w bloku klasy przez określenie poziomu dostępu pola, po którym następuje typ właściwości, a po niej nazwa właściwości, a następnie blok kodu, który deklaruje `get`akcesor i/ `set` lub metodę dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]  
  
 W tym przykładzie `Month` jest zadeklarowany jako właściwość, aby `set` metoda dostępu `Month` mogła mieć pewność, że wartość jest ustawiona z zakresu od 1 do 12. `Month` Właściwość używa pola prywatnego do śledzenia wartości rzeczywistej. Rzeczywista lokalizacja danych właściwości jest często określana jako "magazyn zapasowy" właściwości. Jest to typowe dla właściwości, aby używać prywatnych pól jako magazynu zapasowego. Pole jest oznaczone jako prywatne w celu upewnienia się, że można je zmienić tylko przez wywołanie właściwości. Aby uzyskać więcej informacji na temat ograniczeń dostępu publicznego i prywatnego, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Właściwości zaimplementowane przez funkcję autoimplementacji zapewniają uproszczoną składnię dla prostych deklaracji właściwości. Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](./auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Metoda dostępu get  
 Treść `get` metody dostępu przypomina metodę. Musi zwracać wartość typu właściwości. Wykonanie `get` metody dostępu jest równoważne odczytaniu wartości pola. Na przykład, gdy zwracasz zmienną prywatną z `get` metody dostępu i optymalizacje są włączone, wywołanie `get` metody dostępu jest opisane przez kompilator, aby nie było narzutu wywołania metody. Jednak wirtualna `get` metoda dostępu nie może być wbudowana, ponieważ kompilator nie wie w czasie kompilacji, która metoda może być wywoływana w czasie wykonywania. Poniżej znajduje się `get` metoda dostępu zwracająca wartość pola `name`prywatnego:  
  
 [!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]  
  
 W przypadku odwoływania się do właściwości, z wyjątkiem elementu docelowego przypisania, `get` metoda dostępu jest wywoływana w celu odczytania wartości właściwości. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]  
  
 Metoda dostępu musi kończyć się instrukcją Return lub [throw](../../language-reference/keywords/throw.md) , a kontrolka nie może przepływać poza treść metody dostępu. [](../../language-reference/keywords/return.md) `get`  
  
 Jest to zły styl programowania, aby zmienić stan obiektu za pomocą `get` metody dostępu. Na przykład poniższy akcesor tworzy efekt uboczny zmiany stanu obiektu za każdym razem, gdy uzyskuje się dostęp do `number` pola.  
  
 [!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]  
  
 `get` Metody dostępu można użyć do zwrócenia wartości pola lub obliczenia jej i zwrócenia. Przykład:  
  
 [!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]  
  
 W poprzednim segmencie kodu, jeśli nie przypiszesz wartości do `Name` właściwości, zostanie zwrócona wartość na.  
  
## <a name="the-set-accessor"></a>Metoda dostępu set  
 Metoda dostępu jest podobna do metody, której typem zwracanym jest [void.](../../language-reference/keywords/void.md) `set` Używa niejawnego parametru o `value`nazwie, którego typ jest typem właściwości. W poniższym przykładzie `set` metoda dostępu jest dodawana `Name` do właściwości:  
  
 [!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]  
  
 Podczas przypisywania wartości do właściwości `set` metoda dostępu jest wywoływana przy użyciu argumentu, który zapewnia nową wartość. Przykład:  
  
 [!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]  
  
 Wystąpił błąd, aby użyć niejawnej nazwy `value`parametru, dla deklaracji zmiennej lokalnej `set` w metodzie dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości mogą być oznaczone jako `public`, `private`, `protected` `internal` ,,`private protected`lub. `protected internal` Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą uzyskać dostęp do właściwości. Metody dostępu `set` i dla tej samej właściwości mogą mieć różne Modyfikatory dostępu. `get` `get` Na przykład `protected`może być `public` dozwolone Zezwalanie na dostęp tylko do odczytu spoza typu i `set` może być `private` lub. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
 Właściwość może być zadeklarowana jako właściwość statyczna za pomocą `static` słowa kluczowego. Dzięki temu właściwość jest dostępna dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).  
  
 Właściwość może być oznaczona jako właściwość wirtualna za pomocą słowa kluczowego [Virtual](../../language-reference/keywords/virtual.md) . Dzięki temu klasy pochodne zastępują zachowanie właściwości przy użyciu słowa kluczowego [override](../../language-reference/keywords/override.md) . Aby uzyskać więcej informacji na temat tych opcji [](./inheritance.md), zobacz Dziedziczenie.  
  
 Właściwość zastępująca Właściwość wirtualną może być również [zapieczętowana](../../language-reference/keywords/sealed.md), określając, że dla klas pochodnych nie jest już wirtualna. Wreszcie właściwość może być zadeklarowana jako [abstract](../../language-reference/keywords/abstract.md). Oznacza to, że nie ma implementacji w klasie, a klasy pochodne muszą zapisywać własne implementacje. Aby uzyskać więcej informacji na temat tych opcji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](./abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Wystąpił błąd podczas używania modyfikatora [Virtual](../../language-reference/keywords/virtual.md), [abstract](../../language-reference/keywords/abstract.md)lub [override](../../language-reference/keywords/override.md) w metodzie dostępu właściwości statycznej [](../../language-reference/keywords/static.md) .  
  
## <a name="example"></a>Przykład  
 Ten przykład ilustruje właściwości wystąpienia, statyczne i tylko do odczytu. Akceptuje nazwę pracownika z klawiatury, zwiększa `NumberOfEmployees` się o 1 i wyświetla nazwę i numer pracownika.  
  
 [!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak uzyskać dostęp do właściwości w klasie bazowej, która jest ukryta przez inną właściwość, która ma taką samą nazwę w klasie pochodnej.  
  
 [!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]  
  
 Poniżej przedstawiono ważne punkty w poprzednim przykładzie:  
  
- Właściwość `Name` w klasie pochodnej ukrywa właściwość `Name` w klasie bazowej. W takim przypadku `new` modyfikator jest używany w deklaracji właściwości w klasie pochodnej:  
  
     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  
  
- Rzutowanie `(Employee)` jest używane w celu uzyskania dostępu do właściwości Hidden w klasie bazowej:  
  
     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]  
  
     Aby uzyskać więcej informacji na temat ukrywania elementów członkowskich, zobacz [nowy modyfikator](../../language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dwie klasy `Cube` , i `Square`, implementują klasę abstrakcyjną, `Shape`i przesłaniają jej właściwość `Area` abstrakcyjną. Zwróć uwagę na użycie modyfikatora [override](../../language-reference/keywords/override.md) we właściwościach. Program akceptuje stronę jako dane wejściowe i oblicza obszary dla kwadratu i sześcianu. Akceptuje również obszar jako dane wejściowe i oblicza odpowiednią stronę dla kwadratu i sześcianu.  
  
 [!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Właściwości interfejsu](./interface-properties.md)
- [Właściwości zaimplementowane automatycznie](./auto-implemented-properties.md)
