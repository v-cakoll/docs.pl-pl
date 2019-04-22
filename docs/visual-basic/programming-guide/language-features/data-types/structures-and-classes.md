---
title: Struktury i klasy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3635729705520518d4c950f8a79da7d1249285bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841618"
---
# <a name="structures-and-classes-visual-basic"></a>Struktury i klasy (Visual Basic)
Visual Basic ujednolica składnia struktury i klasy z wynikiem, że obie te jednostki obsługuje większość tych samych funkcji. Istnieją również istotne różnice między strukturami i klasami.  
  
 Klasy ma tę zaletę, są typami odwołań — przekazywanie odwołania jest bardziej wydajne niż przekazanie zmiennej struktury, ze swoimi danymi. Z drugiej strony struktury nie wymagają alokacji pamięci na stosie globalnego.  
  
 Ponieważ użytkownik nie może dziedziczyć ze struktury, struktur należy używać tylko w przypadku obiektów, które nie muszą być rozszerzony. Użyj struktury, gdy obiekt, który chcesz utworzyć ma rozmiar wystąpienia małe i wziąć pod uwagę charakterystyki wydajności klas i struktur.  
  
## <a name="similarities"></a>Podobieństwa  
 Klasy i struktury są podobne pod następującymi względami:  
  
-   Oba są *kontenera* typów, co oznacza, że zawierają one innych typów jako elementy członkowskie.  
  
-   Mają elementów członkowskich, które mogą zawierać konstruktorów, metod, właściwości, pola, stałe, wyliczenia, zdarzenia i procedury obsługi zdarzeń. Jednak nie należy mylić te elementy członkowskie z deklarowanym *elementy* struktury.  
  
-   Oba elementy Członkowskie mogą mieć zindywidualizowanych poziomy dostępu. Na przykład, można zadeklarować jednego członka `Public` i innym `Private`.  
  
-   Jednocześnie można implementować interfejsy.  
  
-   Jednocześnie można udostępnionego konstruktorów, z lub bez parametrów.  
  
-   Jednocześnie można uwidocznić *właściwość domyślna*pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.  
  
-   Jednocześnie można zadeklarować i wywoływanie zdarzeń, a jednocześnie można zadeklarować delegatów.  
  
## <a name="differences"></a>Różnice  
 Struktury i klasy różnią się następujące dane:  
  
-   Struktury są *typy wartości*; klasy są *typy odwołań*. Zmienną typu struktury zawiera struktura danych, zamiast zawierająca odwołanie do danych jako typ klasy jest.  
  
-   Alokacja stosu; korzystają struktury klasy użyj alokacji sterty.  
  
-   Wszystkie elementy struktury są `Public` domyślnie klasy zmienne i stałe są `Private` domyślnie, podczas gdy inne elementy członkowskie klasy są `Public` domyślnie. To zachowanie dla składowych klasy zapewnia zgodność z systemem Visual Basic 6.0, domyślnie zostanie ustawiona.  
  
-   Struktura musi mieć co najmniej jeden nieudostępnionych noncustom zmiennej lub nieudostępnionych, element zdarzeń; Klasa może być całkowicie pusty.  
  
-   Elementy struktury nie może być zadeklarowana jako `Protected`; można składowych klasy.  
  
-   Procedura struktury można obsługiwać zdarzenia, tylko wtedy, gdy jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedury i tylko przez klasy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md); każda procedura klasy można obsługiwać zdarzenia, za pomocą obu [ Obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) — słowo kluczowe lub `AddHandler` instrukcji. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Struktura deklaracje zmiennych nie można określić inicjatorów lub początkowe rozmiary tablic; deklaracje zmiennych klasy mogą.  
  
-   Struktury niejawnie dziedziczą z <xref:System.ValueType?displayProperty=nameWithType> klasy i nie może dziedziczyć z innego typu; klasy mogą dziedziczyć z klasy lub klas w innych niż <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Konstrukcje nie są dziedziczone; klasy są.  
  
-   Struktury nigdy nie kończą, dzięki czemu środowisko uruchomieniowe języka wspólnego (CLR) nigdy nie wywołuje <xref:System.Object.Finalize%2A> metody na dowolną strukturę; klas są kończone przez moduł odśmiecania pamięci (GC), która wywołuje <xref:System.Object.Finalize%2A> klasy po wykryciu, że istnieją nie aktywne odwołania pozostałe.  
  
-   Struktura nie wymaga konstruktora; jest klasą.  
  
-   Struktury mogą mieć konstruktorów nieudostępnionych tylko wtedy, gdy przyjmują parametrów; klasy mogą mieć je z lub bez parametrów.  
  
 Co struktura ma niejawne publicznego konstruktora bez parametrów. Ten konstruktor inicjuje wszystkie struktury elementów danych do wartości domyślnych. Nie można przedefiniować to zachowanie.  
  
## <a name="instances-and-variables"></a>Wystąpienia i zmienne  
 Ponieważ struktury są typami wartości, każdej zmiennej struktury jest trwałe związane z wystąpienia poszczególnych struktury. Ale klasy są typami odwołań, a zmienna obiektu może odwoływać się do różnych wystąpień klas w różnym czasie. Wykonywania tego rozróżnienia ma wpływ na użycie struktur i klas w następujący sposób:  
  
-   **Inicjowanie.** Zmiennej struktury, obejmuje inicjowanie elementów przy użyciu struktury konstruktora bez parametrów. W związku z tym `Dim s As struct1` jest odpowiednikiem `Dim s As struct1 = New struct1()`.  
  
-   **Przypisywanie zmiennych.** Podczas przypisywania jednej zmiennej struktury do innego lub przekazać wystąpienia struktury do argumentu procedury bieżące wartości zmiennych elementy są kopiowane do nowej struktury. Przypisz jednej zmiennej obiektu do innego lub przekazywanie zmienną obiektu do procedury, wskaźnik odwołania są kopiowane.  
  
-   **Przypisywanie Nothing.** Można przypisać wartość [nic](../../../../visual-basic/language-reference/nothing.md) do struktury zmienną, ale wystąpienie jest nadal skojarzony ze zmienną. Nadal możesz wywołać jego metody i dostęp do jego elementów danych, mimo że zmiennej elementy są ponownie inicjowane przez przypisanie.  
  
     Natomiast jeśli zostanie ustawiona zmienna obiektu `Nothing`, Usuń skojarzenie jej z dowolnego wystąpienia klasy i nie masz dostępu do żadnych elementów członkowskich za pośrednictwem zmiennej do momentu przypisania inne wystąpienie do niego.  
  
-   **Wiele wystąpień.** Zmienna obiektu może mieć inną klasę wystąpień przypisane do niego w różnym czasie, a kilku zmiennych obiektu może odwoływać się do tego samego wystąpienia klasy, w tym samym czasie. Zmiany wprowadzone do wartości elementów członkowskich klasy wpływa na tych członków, gdy dostępne za pośrednictwem innej zmiennej wskazujące do tego samego wystąpienia.  
  
     Jednak elementy struktury są izolowane w ramach ich własnych wystąpienie. Zmiany wartości nie są uwzględniane w żadnych innych zmiennych struktury, nawet w przypadku innych wystąpień tego samego `Structure` deklaracji.  
  
-   **Równości.** Sprawdzaniem równości dwóch struktur, muszą być wykonywane z testem element po elemencie. Można porównać dwie zmienne do obiektu za pomocą <xref:System.Object.Equals%2A> metody. <xref:System.Object.Equals%2A> Wskazuje, czy dwie zmienne punktu w tym samym wystąpieniu.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
