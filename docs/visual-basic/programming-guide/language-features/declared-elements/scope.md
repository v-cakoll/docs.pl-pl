---
title: Zakres w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 38dd9d6d40780c25f06a35cf1ffbe4743b7da4a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537250"
---
# <a name="scope-in-visual-basic"></a>Zakres w Visual Basic
*Zakres* zadeklarowanych elementów to zbiór cały kod, który może odwoływać się do niego bez kwalifikowania nazwy i udostępniając je za pośrednictwem [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Element może mieć zakresu w jednej z następujących poziomach:  
  
|Poziom|Opis|  
|-----------|-----------------|  
|Zakres bloku|Dostępne tylko w kodzie blok w którym jest zadeklarowana|  
|Zakres procedury|Dostępne dla całego kodu w ramach procedury, w której jest zadeklarowana|  
|Zakres modułu|Dostępne dla całego kodu w module, klasa lub struktura, w której jest zadeklarowana|  
|Zakres Namespace|Dostępne dla całego kodu w przestrzeni nazw, w której jest zadeklarowana|  
  
 Te poziomy postępu zakres od najwęższego (Blokuj) do najszerszego (przestrzeni nazw), gdzie *najwęższego zakresu* oznacza, że najmniejszy zestaw kod, który może odwoływać się do elementu bez kwalifikacji. Aby uzyskać więcej informacji zobacz "Poziomy Scope" na tej stronie.  
  
## <a name="specifying-scope-and-defining-variables"></a>Określanie zakresu i definiowanie zmiennych  
 W przypadku deklarowania należy określić zakres elementu. Zakres może zależeć od następujących czynników:  
  
-   Region (bloku, procedury, modułu, klasy lub struktury), w którym można zadeklarować elementu  
  
-   Przestrzeń nazw zawiera deklaracji elementu  
  
-   Poziom dostępu, który deklaruje dla elementu  
  
 Należy dopilnować, podczas definiowania zmiennych o tej samej nazwie, ale inny zakres, ponieważ w ten sposób może prowadzić do nieoczekiwanych wyników. Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Poziomy zakresu  
 Element programowania jest dostępna w całym regionie, w którym trzeba je zadeklarować. Cały kod w tym samym regionie mogą odwoływać się do elementu bez kwalifikowania nazwy.  
  
### <a name="block-scope"></a>Zasięg bloku  
 Blok to zbiór instrukcji ujętych w ramach inicjowanie i kończenie instrukcji deklaracji, takie jak następujące:  
  
-   `Do` i `Loop`  
  
-   `For` [`Each`] i `Next`  
  
-   `If` i `End If`  
  
-   `Select` i `End Select`  
  
-   `SyncLock` i `End SyncLock`  
  
-   `Try` i `End Try`  
  
-   `While` i `End While`  
  
-   `With` i `End With`  
  
 Jeśli deklarowaniu zmiennej w bloku, możesz użyć go tylko w ramach tego bloku. W poniższym przykładzie zakres zmiennej liczby całkowitej `cube` to blok między `If` i `End If`, i nie mogą odwoływać się do `cube` podczas wykonywania przekazuje poza blokiem.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Nawet jeśli zakres zmiennej jest ograniczony do bloku, jego okres istnienia jest nadal całej procedury. Po wprowadzeniu bloku w więcej niż jeden raz podczas wykonywania procedury każdej zmiennej w bloku zachowuje poprzedniej wartości. Aby uniknąć nieoczekiwanych wyników, w takim przypadku, dobrze jest zainicjować zmienne bloku na początku bloku.  
  
### <a name="procedure-scope"></a>Zakres procedury  
 Element zadeklarowany w procedurze nie jest dostępna spoza tej procedury. Procedury zawierający tę deklarację, można go użyć. Zmienne na tym poziomie są również nazywane *zmienne lokalne*. Możesz zadeklarować je z [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), z lub bez [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) — słowo kluczowe.  
  
 Zakres procedury i bloku są ściśle powiązane. Jeśli zadeklarujesz zmienną wewnątrz procedury, ale poza bloku w ramach tej procedury można traktować zmiennej jako posiadające blok zakresu, gdzie bloku jest przez cały czas.  
  
> [!NOTE]
>  Wszystkie elementy lokalne, nawet jeśli są one `Static` zmienne, są prywatne dla procedury, w jakiej są wyświetlane. Nie można zadeklarować za pomocą dowolnego elementu [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w procedurze.  
  
### <a name="module-scope"></a>Zakres modułu  
 Dla wygody pojedynczego terminu *poziom modułu* stosuje się jednakowo do modułów, klas i struktur. Można zadeklarować elementy na tym poziomie, umieszczając instrukcji deklaracji poza jakąkolwiek procedurę lub blok, ale w obrębie modułu, klasy lub struktury.  
  
 Po wprowadzeniu deklaracji na poziomie modułu, poziomu dostępu, który wybierzesz określa zakres. Przestrzeń nazw zawierająca modułu, klasy lub struktury wpływa również na zakresie.  
  
 Elementy, dla których możesz deklarować [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) poziom dostępu są dostępne, do każdej procedury w tym module, ale nie na wszelki kod w oddzielnym modułem. `Dim` Poufności na poziomie modułu wartość domyślna to `Private` Jeśli używasz dowolnego słowa kluczowe do poziomu dostępu. Jednak można tworzyć poziomu zakresu i dostęp do bardziej oczywiste, przy użyciu `Private` — słowo kluczowe w `Dim` instrukcji.  
  
 W poniższym przykładzie wszystkie procedury zdefiniowane w module mogą odwoływać się do zmiennej ciągu `strMsg`. Druga procedura jest wywoływana, wyświetla zawartość zmiennej ciągu `strMsg` w oknie dialogowym.  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Zakres Namespace  
 Jeśli deklaruje element w poziomie przy użyciu modułu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe, staje się dostępna dla wszystkich procedur w całej przestrzeni nazw, w którym zadeklarowany jest element. Z następującą modyfikacją do poprzedniego przykładu, zmiennej ciągu `strMsg` mogą być przywoływane przez kod w dowolnym miejscu w przestrzeni nazw w jego deklaracji.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Zakres Namespace zawiera zagnieżdżone przestrzenie nazw. Element dostępne w przestrzeni nazw jest również dostępne z poziomu dowolnego obszaru nazw, zagnieżdżone wewnątrz tego obszaru nazw.  
  
 Jeśli projekt nie zawiera żadnych [Namespace, instrukcja](../../../../visual-basic/language-reference/statements/namespace-statement.md), wszystko w projekcie jest w tej samej przestrzeni nazw. W takim zakresie przestrzeni nazw można traktować jako zakres projektu. `Public` elementy w module, klasy lub struktury są również dostępne dla każdego projektu, który odwołuje się do swojego projektu.  
  
## <a name="choice-of-scope"></a>Wybór zakresu  
 Kiedy Deklarujesz zmienną, możesz należy mieć na uwadze następujące kwestie przy wyborze jego zakres.  
  
### <a name="advantages-of-local-variables"></a>Korzyści wynikające z zmiennych lokalnych  
 Zmienne lokalne są dobrym wyborem dla dowolnych obliczeń tymczasowe z następujących powodów:  
  
-   **Unikanie konfliktu nazw.** Nazwy zmiennych lokalnych nie są podatne na konflikt. Na przykład można utworzyć kilka różnych procedur zawierającego zmienną o nazwie `intTemp`. Tak długo, jak każdy `intTemp` jest zadeklarowana jako zmienna lokalna każdej procedury rozpoznaje tylko własną wersję programu `intTemp`. Wszelkie jednej procedury można zmienić wartość w swojej lokalnej `intTemp` bez wywierania wpływu na `intTemp` zmiennych w innych procedur.  
  
-   **Zużycie pamięci.** Zmienne lokalne wykorzystywać pamięć tylko w przypadku, gdy ich procedura jest uruchomiona. Ich pamięci jest zwalniany, gdy procedura zwraca do wywołującego kodu. Z drugiej strony [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) i [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) zmienne zużywają zasoby pamięci, dopóki aplikacja przestaje działać, więc używane tylko wtedy, gdy jest to konieczne. *Zmienne wystąpienia* używa pamięci nadal istnieje, ich wystąpienia, co sprawia, że ich mniej wydajne niż zmiennych lokalnych, ale potencjalnie bardziej efektywne niż `Shared` lub `Static` zmiennych.  
  
### <a name="minimizing-scope"></a>Minimalizując zakres  
 Ogólnie rzecz biorąc, deklarując dowolną zmienną lub stałą ona dobrą praktyką programowania jest zapewnienie zakres jak to możliwe (zakres bloku jest najmniejsza). To pomaga zachować pamięci i minimalizuje ryzyko swój kod, błędnie odwołujące się do niewłaściwej zmiennej. Podobnie, należy zadeklarować zmienną [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) tylko kiedy jest niezbędne w celu zachowania jego wartość z zakresu od wywołania procedur.  
  
## <a name="see-also"></a>Zobacz także
- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Instrukcje: Kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
