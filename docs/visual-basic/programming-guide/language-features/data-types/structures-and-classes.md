---
title: Struktury i klasy
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: d252d9216a9b825ad0663a5779d7ce7f81fa9011
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393575"
---
# <a name="structures-and-classes-visual-basic"></a>Struktury i klasy (Visual Basic)
Visual Basic łączy składni dla struktur i klas, z wynikiem, że obie jednostki obsługują większość z tych samych funkcji. Istnieją jednak również istotne różnice między strukturami i klasami.  
  
 Klasy mają zalety typów referencyjnych — przekazywanie odwołania jest bardziej wydajne niż przekazywanie zmiennej struktury ze wszystkimi danymi. Z drugiej strony struktury nie wymagają alokacji pamięci na stercie globalnej.  
  
 Ponieważ nie można dziedziczyć z struktury, struktury powinny być używane tylko w przypadku obiektów, które nie muszą być rozszerzane. Używaj struktur, gdy obiekt, który chcesz utworzyć ma niewielki rozmiar wystąpienia, i weź pod uwagę charakterystykę wydajności klas i struktur.  
  
## <a name="similarities"></a>Podobieństwa  
 Struktury i klasy są podobne do następujących:  
  
- Oba są typami *kontenerów* , co oznacza, że zawierają one inne typy jako elementy członkowskie.  
  
- Oba mają składowe, które mogą obejmować konstruktory, metody, właściwości, pola, stałe, wyliczenia, zdarzenia i programy obsługi zdarzeń. Jednakże nie należy mylić tych elementów członkowskich z zadeklarowanymi *elementami* struktury.  
  
- Elementy członkowskie obu tych elementów mogą mieć indywidualne poziomy dostępu. Na przykład jeden element członkowski może być zadeklarowany `Public` i inny `Private` .  
  
- Oba mogą implementować interfejsy.  
  
- Oba mogą mieć udostępnione konstruktory, z lub bez parametrów.  
  
- Obie mogą uwidaczniać *Właściwość domyślną*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.  
  
- Oba mogą deklarować i wywoływać zdarzenia, a oba mogą deklarować delegatów.  
  
## <a name="differences"></a>Różnice  
 Struktury i klasy różnią się w następujących tematach:  
  
- Struktury są *typami wartości*; klasy są *typami referencyjnymi*. Zmienna typu struktury zawiera dane struktury, a nie zawiera odwołania do danych jako typ klasy.  
  
- Struktury używają alokacji stosu; klasy używają alokacji sterty.  
  
- Wszystkie elementy struktury są `Public` Domyślnie, zmienne klasy i stałe są domyślnie `Private` , podczas gdy inne elementy członkowskie klasy są `Public` domyślnie. Takie zachowanie w przypadku elementów członkowskich klasy zapewnia zgodność z systemem Visual Basic 6,0 wartości domyślnych.  
  
- Struktura musi mieć co najmniej jedną nieudostępnioną zmienną lub nieudostępnianą niestandardową pozycję zdarzenia; Klasa może być całkowicie pusta.  
  
- Elementy struktury nie mogą być deklarowane jako `Protected` ; członkowie klasy mogą.  
  
- Procedura struktury może obsługiwać zdarzenia tylko wtedy, gdy jest to procedura [wspólna](../../../language-reference/modifiers/shared.md) `Sub` i tylko za pomocą [instrukcji AddHandler](../../../language-reference/statements/addhandler-statement.md); każda procedura klasy może obsłużyć zdarzenia za pomocą słowa kluczowego [Handles](../../../language-reference/statements/handles-clause.md) lub `AddHandler` instrukcji. Aby uzyskać więcej informacji, zobacz [zdarzenia](../events/index.md).  
  
- Deklaracje zmiennej struktury nie mogą określać inicjatorów ani początkowych rozmiarów dla tablic; deklaracje zmiennej klasy mogą.  
  
- Struktury niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType> klasy i nie mogą dziedziczyć po żadnym innym typie; klasy mogą dziedziczyć z dowolnej klasy lub klas innych niż <xref:System.ValueType?displayProperty=nameWithType> .  
  
- Struktury nie są dziedziczenia; klasy są.  
  
- Struktury nie są nigdy przerywane, więc środowisko uruchomieniowe języka wspólnego (CLR) nigdy nie wywołuje <xref:System.Object.Finalize%2A> metody w żadnej strukturze; klasy są przerywane przez moduł wyrzucania elementów bezużytecznych (GC), które wywołują <xref:System.Object.Finalize%2A> na klasę, gdy wykryje brak aktywnych odwołań.  
  
- Struktura nie wymaga konstruktora; Klasa.  
  
- Struktury mogą mieć konstruktory nieudostępniane tylko wtedy, gdy przyjmują parametry; klasy mogą mieć parametry z parametrami lub bez nich.  
  
 Każda struktura ma niejawny Konstruktor publiczny bez parametrów. Ten konstruktor inicjuje wszystkie elementy danych struktury do ich wartości domyślnych. Nie można ponownie zdefiniować tego zachowania.  
  
## <a name="instances-and-variables"></a>Wystąpienia i zmienne  
 Ponieważ struktury są typami wartości, Każda zmienna struktury jest trwale związana z konkretnym wystąpieniem struktury. Ale klasy są typami odwołań, a zmienna obiektu może odwoływać się do różnych wystąpień klasy w różnych godzinach. Takie rozróżnienie ma wpływ na użycie struktur i klas w następujący sposób:  
  
- **Zainicjować.** Zmienna struktury niejawnie obejmuje inicjalizację elementów przy użyciu konstruktora bez parametrów struktury. W związku `Dim s As struct1` z tym, jest równoważne `Dim s As struct1 = New struct1()` .  
  
- **Przypisywanie zmiennych.** Po przypisaniu jednej zmiennej struktury do innej lub przekazanie wystąpienia struktury do argumentu procedury, bieżące wartości wszystkich elementów zmiennych są kopiowane do nowej struktury. Po przypisaniu jednej zmiennej obiektu do innej lub przekazanie zmiennej obiektu do procedury, tylko wskaźnik odwołania jest kopiowany.  
  
- **Przypisywanie niczego.** Wartość [Nothing](../../../language-reference/nothing.md) można przypisać do zmiennej struktury, ale wystąpienie jest nadal skojarzone ze zmienną. Nadal można wywołać metody i uzyskać dostęp do jej elementów danych, chociaż elementy zmiennych są ponownie inicjowane przez przypisanie.  
  
     Natomiast w przypadku ustawienia zmiennej obiektu na `Nothing` , należy usunąć skojarzenie jej z dowolnego wystąpienia klasy i nie będzie można uzyskać dostępu do żadnych elementów członkowskich za pośrednictwem zmiennej, dopóki nie przypiszesz do niego kolejnego wystąpienia.  
  
- **Wiele wystąpień.** Zmienna obiektu może mieć przypisane inne wystąpienia klasy w różnym czasie, a kilka zmiennych obiektu może odwoływać się do tego samego wystąpienia klasy w tym samym czasie. Zmiany wprowadzane do wartości elementów członkowskich klasy mają wpływ na tych członków, gdy uzyskują dostęp za pomocą innej zmiennej wskazującej na to samo wystąpienie.  
  
     Elementy struktury są jednak izolowane w ich własnym wystąpieniu. Zmiany w ich wartości nie są odzwierciedlone w żadnych innych zmiennych struktury, nawet w innych wystąpieniach tej samej `Structure` deklaracji.  
  
- **Kryteri.** Testy równości dwóch struktur muszą być wykonywane z testem elementu po elemencie. Dwie zmienne obiektów można porównać przy użyciu <xref:System.Object.Equals%2A> metody. <xref:System.Object.Equals%2A>wskazuje, czy dwie zmienne wskazują na to samo wystąpienie.  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Złożone typy danych](composite-data-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Struktury oraz inne elementy programowania](structures-and-other-programming-elements.md)
- [Obiekty i klasy](../objects-and-classes/index.md)
