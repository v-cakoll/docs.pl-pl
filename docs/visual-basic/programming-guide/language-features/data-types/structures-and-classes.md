---
title: Struktury i klasy (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08e31481feac7a6184c6b29269d193c749f440ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="structures-and-classes-visual-basic"></a>Struktury i klasy (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]łączy składnia struktury i klasy, z wynikami, że obie te jednostki obsługuje większość tej samej funkcji. Istnieją również istotne różnice między struktury i klasy.  
  
 Klasy mają prowadzoną typy referencyjne — przekazywaniem odwołań do jest skuteczniejsza niż przekazywanie zmiennej struktury z jego dane. Z drugiej strony struktur nie wymagają alokacji pamięci sterty globalnej.  
  
 Ponieważ nie może dziedziczyć struktury, tylko dla obiektów, które nie muszą być rozszerzony, należy używać struktury. Używają struktury, gdy obiekt, który chcesz utworzyć ma rozmiar małych wystąpienia, a wziąć pod uwagę charakterystykę wydajności klasy lub struktury.  
  
## <a name="similarities"></a>Podobieństwa  
 Klasy i struktury są podobne w następujących aspektach:  
  
-   Oba są *kontenera* typów, co oznacza, że zawierają one innych typów jako elementy członkowskie.  
  
-   Mają elementy członkowskie, które mogą zawierać konstruktorów, metod, właściwości, pola, stałe, wyliczenia, zdarzeń i procedury obsługi zdarzeń. Jednak nie należy mylić tych elementów członkowskich z deklarowanym *elementy* struktury.  
  
-   Oba elementy Członkowskie mogą mieć zindywidualizowanych poziomy dostępu. Na przykład, jeden element członkowski mogą być deklarowane `Public` i innym `Private`.  
  
-   Jednocześnie można implementować interfejsów.  
  
-   Jednocześnie można udostępnionego konstruktorów, z lub bez parametrów.  
  
-   Jednocześnie mogą uwidaczniać *domyślna właściwość*, pod warunkiem, że właściwość przyjmuje co najmniej jeden parametr.  
  
-   Jednocześnie można deklarowanie i wywoływanie zdarzeń i zarówno zadeklarować delegatów.  
  
## <a name="differences"></a>Różnice  
 Struktury i klasy różnią się następujące informacje:  
  
-   Struktury są *typów wartości*; klasy są *typy referencyjne*. Zmienna typu Struktura zawiera struktury danych, a nie zawierające odwołania do danych jako typ klasy jest.  
  
-   Alokacja stosu; Użyj struktury klasy używaj alokacji sterty.  
  
-   Wszystkie elementy struktury są `Public` domyślnie; klasa zmienne i stałe są `Private` domyślnie, gdy są inne elementy członkowskie klasy `Public` domyślnie. To zachowanie dla członków klasy zapewnia zgodność z wartości domyślnych systemu Visual Basic 6.0.  
  
-   Struktura musi mieć co najmniej jeden udostępniana noncustom zmiennej lub udostępniana, element zdarzeń; Klasa może być pusty.  
  
-   Elementy struktury nie można zadeklarować jako `Protected`; można elementów członkowskich klasy.  
  
-   Procedury struktury może obsłużyć zdarzenia tylko wtedy, gdy jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedury i tylko za pomocą klasy [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md); dowolnej klasy procedury może obsłużyć zdarzenia, przy użyciu albo [ Obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) — słowo kluczowe lub `AddHandler` instrukcji. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Struktura deklaracji zmiennych nie można określić inicjatory lub początkowe rozmiary tablic; deklaracje zmiennej klasy można.  
  
-   Dziedzicz niejawnie struktury <xref:System.ValueType?displayProperty=nameWithType> klasy i nie może dziedziczyć z żadnym innym typem; klasy mogą dziedziczyć klasy lub klas innych niż <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Struktury nie są dziedziczone; występują następujące klasy.  
  
-   Struktury nigdy nie kończą, więc środowisko uruchomieniowe języka wspólnego (CLR) nigdy nie wywołuje <xref:System.Object.Finalize%2A> metody w dowolnej struktury; klasy kończą się przez moduł garbage collector (GC), która wywołuje <xref:System.Object.Finalize%2A> dla klasy, po wykryciu istnieją żadnych aktywnych odwołań pozostałe.  
  
-   Struktury nie wymaga konstruktora; jest klasą.  
  
-   Struktury mogą mieć konstruktorów udostępniana tylko wtedy, gdy ich wejściem parametrów; klasy mogą mieć je z lub bez parametrów.  
  
 Struktura co ma niejawne publicznego konstruktora bez parametrów. Ten konstruktor inicjuje wszystkie struktury elementy danych do wartości domyślnych. Nie można ponownie zdefiniować to zachowanie.  
  
## <a name="instances-and-variables"></a>Wystąpienia i zmienne  
 Ponieważ struktury są typy wartości, każdej zmiennej struktury trwale jest powiązany z wystąpieniem poszczególnych struktury. Jednak klasy są typy referencyjne i zmienna obiektu mogą odwoływać się do różnych wystąpień klasy w różnym czasie. Różnica w tej wpływa na użycie struktur i klas w następujący sposób:  
  
-   **Inicjowanie.** Zmienna struktury obejmuje inicjowania elementów przy użyciu konstruktora struktury. W związku z tym `Dim s As struct1` jest odpowiednikiem `Dim s As struct1 = New struct1()`.  
  
-   **Przypisywanie zmiennych.** Podczas przypisać jedną zmienną struktury lub przekaż wystąpienie struktury do argumentu procedury bieżące wartości zmiennych elementy są kopiowane do nowej struktury. Przypisać jedną zmienna obiektu lub przekazywanie zmiennej obiektu do procedury wskaźnik odwołania są kopiowane.  
  
-   **Przypisywanie Nothing.** Można przypisać wartość [nic](../../../../visual-basic/language-reference/nothing.md) struktury zmiennej, ale wystąpienie jest nadal skojarzony ze zmienną. Nadal można wywołać metody i dostęp do jego elementów danych, mimo że zmiennej elementy są ponownie inicjowane przez przypisanie.  
  
     Natomiast jeśli ustawiono zmienną obiektu `Nothing`skojarzenie go z dowolnego wystąpienia klasy i nie masz dostępu do żadnych elementów członkowskich za pośrednictwem zmiennej do momentu przypisania do niej inne wystąpienie.  
  
-   **Wiele wystąpień.** Zmienna obiektu może mieć przypisane do niego w różnym czasie wystąpienia inną klasę, a kilku zmiennych obiektu mogą odwoływać się do tego samego wystąpienia klasy, w tym samym czasie. Zmiany wprowadzone do wartości elementów członkowskich klasy mają wpływ na tych członków, gdy dostępne za pośrednictwem innej zmiennej wskazanie w tym samym wystąpieniu.  
  
     Elementy struktury, jednak są odizolowane w własne wystąpienie. Zmiany wartości nie są widoczne w wszelkie inne zmienne struktury, nawet w przypadku innych wystąpień tego samego `Structure` deklaracji.  
  
-   **Równości.** Dwa struktur sprawdzaniem równości można wykonać z testem element po elemencie. Dwie zmienne obiektu można porównać przy użyciu <xref:System.Object.Equals%2A> metody. <xref:System.Object.Equals%2A>Wskazuje, czy dwie zmienne punktu w tym samym wystąpieniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Rozwiązywanie problemów z typów danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
