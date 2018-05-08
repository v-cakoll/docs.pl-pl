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
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="scope-in-visual-basic"></a>Zakres w Visual Basic
*Zakres* elementu zadeklarowane to zbiór wszystkich kod, który może odwoływać się do niego bez kwalifikujących się jego nazwę lub udostępnianie przy [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Element może mieć zakresu w jednej z następujących poziomach:  
  
|Poziom|Opis|  
|-----------|-----------------|  
|Zakres bloku|Dostępne tylko w kodzie bloku, w którym zadeklarowano|  
|Zakres procedury|Dostępne dla całego kodu w ramach procedury, w którym jest zadeklarowana|  
|Zakres modułu|Dostępne dla wszystkich kodu w module, klasy lub struktury, w którym jest zadeklarowana|  
|Zakres Namespace|Dostępne dla całego kodu w przestrzeni nazw, w którym jest zadeklarowana|  
  
 Te poziomy postęp zakresu najwęższym (Blokuj) do uzyskiwania (przestrzeni nazw), gdzie *najwęższy zakres* oznacza, że najmniejszy zestaw kod, który może odwoływać się do elementu bez kwalifikacji. Aby uzyskać więcej informacji zobacz "Poziomy zakresu" na tej stronie.  
  
## <a name="specifying-scope-and-defining-variables"></a>Określanie zakresu i definiowanie zmiennych  
 Możesz określić zakres elementu przy deklarowaniu go. Zakres może zależeć od następujących czynników:  
  
-   Region (bloku, procedury, modułu, klasy lub struktury), w którym można zadeklarować elementu  
  
-   Przestrzeń nazw zawierająca deklaracji elementu  
  
-   Poziom dostępu, który został zadeklarowany dla elementu  
  
 Należy dopilnować, podczas definiowania zmiennych o tej samej nazwie, ale inny zakres, ponieważ w ten sposób może prowadzić do nieoczekiwanych wyników. Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="levels-of-scope"></a>Poziomy zakresu  
 Element programowania są dostępne w całej region ją zadeklarować. Cały kod w tym samym regionie mogą odwoływać się do elementu bez kwalifikujących się jego nazwy.  
  
### <a name="block-scope"></a>Zasięg bloku  
 Blok jest zestaw instrukcji ujętą w nawiasy klamrowe inicjowanie i kończenie instrukcji deklaracji, takie jak następujące:  
  
-   `Do` I `Loop`  
  
-   `For` [`Each`] i `Next`  
  
-   `If` I `End If`  
  
-   `Select` I `End Select`  
  
-   `SyncLock` I `End SyncLock`  
  
-   `Try` I `End Try`  
  
-   `While` I `End While`  
  
-   `With` I `End With`  
  
 Jeżeli można zadeklarować zmiennej w bloku, możesz używać go tylko w tym bloku. W poniższym przykładzie zakres zmienna całkowitoliczbowa `cube` bloku między `If` i `End If`, a nie mogą odwoływać się do `cube` podczas wykonywania przekazuje poza blokiem.  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  Nawet jeśli zakresu zmiennej jest ograniczona do bloku, jego okres istnienia jest nadal całej procedury. Po wprowadzeniu bloku w więcej niż raz podczas wykonywania procedury każdej zmiennej w bloku zachowuje jego poprzednią wartość. Aby uniknąć nieoczekiwanych wyników w takim przypadku, jest rozsądnego zainicjować zmienne bloku na początku bloku.  
  
### <a name="procedure-scope"></a>Zakres procedury  
 Element zadeklarowany w obrębie procedury nie jest dostępna spoza tej procedury. Można go używać tylko tej procedury, która zawiera deklarację. Zmienne na tym poziomie są również znane jako *zmiennych lokalnych*. Deklarowanie je za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), z lub bez [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) — słowo kluczowe.  
  
 Zakres procedury i bloku są ściśle powiązane. Jeśli należy zadeklarować zmienną wewnątrz procedury, ale spoza bloku w ramach tej procedury, można traktować jako o zakresie bloku, w którym bloku jest całą procedurę zmiennej.  
  
> [!NOTE]
>  Wszystkie elementy lokalne, nawet jeśli są one `Static` zmienne, są prywatne dla procedury, w jakiej widnieją. Nie można zadeklarować przy użyciu dowolnego elementu [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w procedurze.  
  
### <a name="module-scope"></a>Zakres modułu  
 Dla wygody pojedynczy termin *poziom modułu* dotyczą modułów, klasy i struktury. Elementy na tym poziomie można zadeklarować przez umieszczenie instrukcji deklaracji poza żadnych procedurę lub blok, ale w ramach modułu, klasy lub struktury.  
  
 Po wprowadzeniu deklaracji na poziomie modułu, należy wybrać poziom dostępu określa zakres. Przestrzeń nazw, który zawiera modułu, klasy lub struktury dotyczy również zakres.  
  
 Elementy, dla których należy zadeklarować [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) poziom dostępu są dostępne do każdej procedury w module, ale nie do żadnego kodu w innym module. `Dim` Domyślnie instrukcji na poziomie modułu `Private` Jeśli nie używasz dowolnego słowa kluczowe do poziomu dostępu. Jednak można tworzyć poziom dostępu i zakres bardziej oczywistymi, przy użyciu `Private` — słowo kluczowe w `Dim` instrukcji.  
  
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
 W przypadku elementu w poziomie przy użyciu modułu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe, staje się dostępny dla wszystkich procedur w całej przestrzeni nazw, w którym zadeklarowano ten element. Z następującą modyfikacją jak w poprzednim przykładzie zmienna string `strMsg` mogą być przywoływane przez kod w dowolnym miejscu jego deklaracji przestrzeni nazw.  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Zakres Namespace zawiera zagnieżdżone przestrzeni nazw. Element dostępne w przestrzeni nazw jest również dostępne w przestrzeni nazw zagnieżdżone wewnątrz tego obszaru nazw.  
  
 Jeśli projekt nie zawiera żadnych [instrukcji Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), wszystko w projekcie jest w tej samej przestrzeni nazw. W takim przypadku zakresie przestrzeni nazw można traktować jako zakres projektu. `Public` elementy w module, klasy lub struktury są również dostępne dla każdego projektu, który odwołuje się do swojego projektu.  
  
## <a name="choice-of-scope"></a>Wybór zakresu  
 Deklaracja zmiennej możesz należy mieć na uwadze następujące kwestie podczas wybierania jej zakres.  
  
### <a name="advantages-of-local-variables"></a>Zalety zmiennych lokalnych  
 Zmienne lokalne są dobrym rozwiązaniem w przypadku dowolnych tymczasowego obliczeń z następujących powodów:  
  
-   **Unikanie konfliktów nazw.** Nazwy zmiennych lokalnych nie są podatne na konflikt. Na przykład można utworzyć kilka różne procedury zawierające zmiennej o nazwie `intTemp`. Tak długo, jak każdy `intTemp` jest zadeklarowany jako zmienną lokalną każdej procedury rozpoznaje tylko własną wersję z `intTemp`. Wszelkie jednej procedury można zmienić wartości w jego lokalnej `intTemp` bez wpływu na `intTemp` zmiennych w innych procedur.  
  
-   **Zużycie pamięci.** Zmienne lokalne używa pamięci tylko wtedy, gdy ich procedura jest uruchomiona. Ich pamięci jest likwidowany, gdy procedura powróci do wywołującego kodu. Z kolei [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) i [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) zmienne zużywają zasoby pamięci, dopóki aplikacja przestanie działać, należy więc je tylko wtedy, gdy jest to konieczne. *Wystąpienie zmienne* używa pamięci podczas ich wystąpienia nadal istnieje, dzięki czemu ich mniej wydajne niż zmiennych lokalnych, ale potencjalnie bardziej efektywne niż `Shared` lub `Static` zmiennych.  
  
### <a name="minimizing-scope"></a>Minimalizowanie zakresu  
 Ogólnie rzecz biorąc, przy deklarowaniu dowolną zmienną lub stałą, jest dobrym programowania rozwiązań, aby zakres jak to możliwe (zakresie bloku jest najwęższym). Pomaga zachować pamięci i minimalizuje ryzyko błędnego odwołujących się do zmiennej niewłaściwy kod. Podobnie, należy zadeklarować zmiennej jako [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) tylko gdy jest konieczne w celu zachowania jego wartość z zakresu od wywołań procedur.  
  
## <a name="see-also"></a>Zobacz też  
 [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Instrukcje: kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
