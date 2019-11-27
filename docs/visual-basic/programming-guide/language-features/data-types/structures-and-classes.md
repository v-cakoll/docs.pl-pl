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
ms.openlocfilehash: 3353935a74bb77fa4a630e706aa425063c7a610a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346330"
---
# <a name="structures-and-classes-visual-basic"></a>Struktury i klasy (Visual Basic)
Visual Basic łączy składni dla struktur i klas, z wynikiem, że obie jednostki obsługują większość z tych samych funkcji. Istnieją jednak również istotne różnice między strukturami i klasami.  
  
 Klasy mają zalety typów referencyjnych — przekazywanie odwołania jest bardziej wydajne niż przekazywanie zmiennej struktury ze wszystkimi danymi. Z drugiej strony struktury nie wymagają alokacji pamięci na stercie globalnej.  
  
 Ponieważ nie można dziedziczyć z struktury, struktury powinny być używane tylko w przypadku obiektów, które nie muszą być rozszerzane. Używaj struktur, gdy obiekt, który chcesz utworzyć ma niewielki rozmiar wystąpienia, i weź pod uwagę charakterystykę wydajności klas i struktur.  
  
## <a name="similarities"></a>Podobieństwa  
 Struktury i klasy są podobne do następujących:  
  
- Oba są typami *kontenerów* , co oznacza, że zawierają one inne typy jako elementy członkowskie.  
  
- Oba mają składowe, które mogą obejmować konstruktory, metody, właściwości, pola, stałe, wyliczenia, zdarzenia i programy obsługi zdarzeń. Jednakże nie należy mylić tych elementów członkowskich z zadeklarowanymi *elementami* struktury.  
  
- Elementy członkowskie obu tych elementów mogą mieć indywidualne poziomy dostępu. Na przykład jeden element członkowski można zadeklarować `Public` i inne `Private`.  
  
- Oba mogą implementować interfejsy.  
  
- Oba mogą mieć udostępnione konstruktory, z lub bez parametrów.  
  
- Obie mogą uwidaczniać *Właściwość domyślną*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.  
  
- Oba mogą deklarować i wywoływać zdarzenia, a oba mogą deklarować delegatów.  
  
## <a name="differences"></a>Wynikających  
 Struktury i klasy różnią się w następujących tematach:  
  
- Struktury są *typami wartości*; klasy są *typami referencyjnymi*. Zmienna typu struktury zawiera dane struktury, a nie zawiera odwołania do danych jako typ klasy.  
  
- Struktury używają alokacji stosu; klasy używają alokacji sterty.  
  
- Wszystkie elementy struktury są domyślnie `Public`. zmienne klas i stałe są `Private` domyślnie, podczas gdy inne elementy członkowskie klasy są domyślnie `Public`. Takie zachowanie w przypadku elementów członkowskich klasy zapewnia zgodność z systemem Visual Basic 6,0 wartości domyślnych.  
  
- Struktura musi mieć co najmniej jedną nieudostępnioną zmienną lub nieudostępnianą niestandardową pozycję zdarzenia; Klasa może być całkowicie pusta.  
  
- Elementy struktury nie mogą być deklarowane jako `Protected`; elementy członkowskie klasy mogą.  
  
- Procedura struktury może obsługiwać zdarzenia tylko wtedy, gdy jest to [współdzielona](../../../../visual-basic/language-reference/modifiers/shared.md) procedura`Sub` i tylko za pomocą [instrukcji AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); Każda procedura klasy może obsługiwać zdarzenia za pomocą słowa kluczowego [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) lub instrukcji `AddHandler`. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
- Deklaracje zmiennej struktury nie mogą określać inicjatorów ani początkowych rozmiarów dla tablic; deklaracje zmiennej klasy mogą.  
  
- Struktury niejawnie dziedziczą z klasy <xref:System.ValueType?displayProperty=nameWithType> i nie mogą dziedziczyć po żadnym innym typie; klasy mogą dziedziczyć z dowolnej klasy lub klas innych niż <xref:System.ValueType?displayProperty=nameWithType>.  
  
- Struktury nie są dziedziczenia; klasy są.  
  
- Struktury nie są nigdy przerywane, więc środowisko uruchomieniowe języka wspólnego (CLR) nigdy nie wywołuje metody <xref:System.Object.Finalize%2A> w żadnej strukturze; klasy są kończone przez moduł wyrzucania elementów bezużytecznych (GC), który wywołuje <xref:System.Object.Finalize%2A> na klasie, gdy wykryje brak aktywnych odwołań.  
  
- Struktura nie wymaga konstruktora; Klasa.  
  
- Struktury mogą mieć konstruktory nieudostępniane tylko wtedy, gdy przyjmują parametry; klasy mogą mieć parametry z parametrami lub bez nich.  
  
 Każda struktura ma niejawny Konstruktor publiczny bez parametrów. Ten konstruktor inicjuje wszystkie elementy danych struktury do ich wartości domyślnych. Nie można ponownie zdefiniować tego zachowania.  
  
## <a name="instances-and-variables"></a>Wystąpienia i zmienne  
 Ponieważ struktury są typami wartości, Każda zmienna struktury jest trwale związana z konkretnym wystąpieniem struktury. Ale klasy są typami odwołań, a zmienna obiektu może odwoływać się do różnych wystąpień klasy w różnych godzinach. Takie rozróżnienie ma wpływ na użycie struktur i klas w następujący sposób:  
  
- **Zainicjować.** Zmienna struktury niejawnie obejmuje inicjalizację elementów przy użyciu konstruktora bez parametrów struktury. W związku z tym `Dim s As struct1` jest równoznaczny z `Dim s As struct1 = New struct1()`.  
  
- **Przypisywanie zmiennych.** Po przypisaniu jednej zmiennej struktury do innej lub przekazanie wystąpienia struktury do argumentu procedury, bieżące wartości wszystkich elementów zmiennych są kopiowane do nowej struktury. Po przypisaniu jednej zmiennej obiektu do innej lub przekazanie zmiennej obiektu do procedury, tylko wskaźnik odwołania jest kopiowany.  
  
- **Przypisywanie niczego.** Wartość [Nothing](../../../../visual-basic/language-reference/nothing.md) można przypisać do zmiennej struktury, ale wystąpienie jest nadal skojarzone ze zmienną. Nadal można wywołać metody i uzyskać dostęp do jej elementów danych, chociaż elementy zmiennych są ponownie inicjowane przez przypisanie.  
  
     W przeciwieństwie do ustawienia zmiennej obiektu na `Nothing`, można usunąć skojarzenie jej z dowolnego wystąpienia klasy i nie będzie można uzyskać dostępu do żadnych elementów członkowskich za pośrednictwem zmiennej, dopóki nie przypiszesz do niego kolejnego wystąpienia.  
  
- **Wiele wystąpień.** Zmienna obiektu może mieć przypisane inne wystąpienia klasy w różnym czasie, a kilka zmiennych obiektu może odwoływać się do tego samego wystąpienia klasy w tym samym czasie. Zmiany wprowadzane do wartości elementów członkowskich klasy mają wpływ na tych członków, gdy uzyskują dostęp za pomocą innej zmiennej wskazującej na to samo wystąpienie.  
  
     Elementy struktury są jednak izolowane w ich własnym wystąpieniu. Zmiany wartości nie są odzwierciedlone w żadnych innych zmiennych struktury, nawet w innych wystąpieniach tej samej deklaracji `Structure`.  
  
- **Kryteri.** Testy równości dwóch struktur muszą być wykonywane z testem elementu po elemencie. Można porównać dwie zmienne obiektów przy użyciu metody <xref:System.Object.Equals%2A>. <xref:System.Object.Equals%2A> wskazuje, czy dwie zmienne wskazują na to samo wystąpienie.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
