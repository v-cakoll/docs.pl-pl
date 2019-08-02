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
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512849"
---
# <a name="scope-in-visual-basic"></a>Zakres w Visual Basic

*Zakres* zadeklarowanego elementu jest zestawem wszystkich kodów, które mogą odwoływać się do niego bez zakwalifikowania jego nazwy lub udostępniania za pomocą [instrukcji Imports (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Element może mieć zakres na jednym z następujących poziomów:

|Poziom|Opis|
|-----------|-----------------|
|Zakres bloku|Dostępne tylko w bloku kodu, w którym jest zadeklarowany|
|Zakres procedury|Dostępne dla całego kodu w ramach procedury, w której jest zadeklarowany|
|Zakres modułu|Dostępne dla wszystkich kodów w module, klasie lub strukturze, w których jest zadeklarowana|
|Zakres przestrzeni nazw|Dostępne dla całego kodu w przestrzeni nazw, w którym jest zadeklarowany|

Poziomy postęp zakresu od najwęższego (bloku) do najszerszego (przestrzeni nazw), gdzie najwęższy *zakres* oznacza najmniejszy zestaw kodu, który może odwoływać się do elementu bez kwalifikacji. Aby uzyskać więcej informacji, zobacz sekcję "poziomy zakresu" na tej stronie.

## <a name="specifying-scope-and-defining-variables"></a>Określanie zakresu i Definiowanie zmiennych

Należy określić zakres elementu podczas jego deklarowania. Zakres może zależeć od następujących czynników:

- Region (blok, procedura, moduł, Klasa lub struktura), w którym deklarujesz element

- Przestrzeń nazw zawierająca deklarację elementu

- Poziom dostępu zadeklarowany dla elementu

Należy zachować ostrożność podczas definiowania zmiennych o tej samej nazwie, ale innym zakresie, ponieważ takie działanie może prowadzić do nieoczekiwanych wyników. Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="levels-of-scope"></a>Poziomy zakresu

Element programistyczny jest dostępny w całym regionie, w którym jest zadeklarowana. Cały kod w tym samym regionie może odwoływać się do elementu bez kwalifikowania jego nazwy.

### <a name="block-scope"></a>Zakres bloku

Blok to zestaw instrukcji ujętych w instrukcji inicjujących i kończących deklaracje, takich jak następujące:

- `Do` i `Loop`

- `For`[`Each`] i`Next`

- `If` i `End If`

- `Select` i `End Select`

- `SyncLock` i `End SyncLock`

- `Try` i `End Try`

- `While` i `End While`

- `With` i `End With`

Jeśli zadeklarujesz zmienną w bloku, można jej używać tylko w obrębie tego bloku. W poniższym przykładzie zakres `cube` zmiennej całkowitej jest blokiem między `If` i `End If`i nie można już się odwoływać `cube` , gdy wykonywanie kończy się z bloku.

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> Nawet jeśli zakres zmiennej jest ograniczony do bloku, jego okres istnienia jest nadal w całej procedurze. W przypadku wprowadzenia bloku więcej niż raz podczas procedury Każda zmienna bloku zachowuje poprzednią wartość. Aby uniknąć nieoczekiwanych wyników w taki sposób, należy inicjować zmienne blokowe na początku bloku.

### <a name="procedure-scope"></a>Zakres procedury

Element zadeklarowany w ramach procedury nie jest dostępny poza tą procedurą. Tylko procedura, która zawiera deklarację, może jej używać. Zmienne na tym poziomie są również nazywane *zmiennymi lokalnymi*. Deklaruje je za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)z lub bez słowa kluczowego [static](../../../../visual-basic/language-reference/modifiers/static.md) .

Procedura i zakres bloku są ściśle powiązane. Jeśli zadeklarujesz zmienną wewnątrz procedury, ale poza jakimkolwiek blokiem w ramach tej procedury, można myśleć o zmiennej jako zakresu bloku, gdzie blok jest całą procedurą.

> [!NOTE]
> Wszystkie elementy lokalne, nawet jeśli są `Static` zmiennymi, są prywatne do procedury, w której się znajdują. Nie można zadeklarować żadnego elementu za pomocą [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) słowa kluczowego w ramach procedury.

### <a name="module-scope"></a>Zakres modułu

Dla wygody poziom jednoterminowego *modułu* jest stosowany równomiernie dla modułów, klas i struktur. Można zadeklarować elementy na tym poziomie poprzez umieszczenie instrukcji deklaracji poza procedurą lub blokiem, ale w module, klasie lub strukturze.

Po wprowadzeniu deklaracji na poziomie modułu wybrany poziom dostępu określa zakres. Przestrzeń nazw, która zawiera moduł, klasę lub strukturę, ma także wpływ na zakres.

Elementy, dla których deklarujesz [prywatny](../../../../visual-basic/language-reference/modifiers/private.md) poziom dostępu, są dostępne dla każdej procedury w tym module, ale nie do żadnego kodu w innym module. W przypadku, `Dim`gdynie sąużywaneżadnesłowakluczowepoziomudostępu.`Private` Jednak zakres i poziom dostępu można uczynić bardziej oczywistymi przy użyciu `Private` słowa kluczowego `Dim` w instrukcji.

W poniższym przykładzie wszystkie procedury zdefiniowane w module mogą odwoływać się do zmiennej `strMsg`ciągu. Gdy druga procedura jest wywoływana, wyświetla zawartość zmiennej `strMsg` String w oknie dialogowym.

```vb
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

### <a name="namespace-scope"></a>Zakres przestrzeni nazw

Jeśli zadeklarujesz element na poziomie modułu przy użyciu [](../../../../visual-basic/language-reference/modifiers/friend.md) słowa kluczowego zaprzyjaźnione lub [publiczne](../../../../visual-basic/language-reference/modifiers/public.md) , będzie on dostępny dla wszystkich procedur w całym obszarze nazw, w którym jest zadeklarowany element. Przy następujących zmianach do powyższego przykładu zmienna `strMsg` String może być określana przez kod w dowolnym miejscu w przestrzeni nazw swojej deklaracji.

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

Zakres przestrzeni nazw zawiera zagnieżdżone przestrzenie nazw. Element dostępny w przestrzeni nazw jest również dostępny z poziomu dowolnej przestrzeni nazw zagnieżdżonej w tej przestrzeni nazw.

Jeśli projekt nie zawiera żadnych [instrukcji Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), wszystko w projekcie znajduje się w tej samej przestrzeni nazw. W takim przypadku zakres przestrzeni nazw może być uważany za zakres projektu. `Public`elementy w module, klasie lub strukturze są również dostępne dla każdego projektu, który odwołuje się do projektu.

## <a name="choice-of-scope"></a>Wybór zakresu

Podczas deklarowania zmiennej należy pamiętać o następujących kwestiach podczas wybierania jej zakresu.

### <a name="advantages-of-local-variables"></a>Zalety zmiennych lokalnych

Zmienne lokalne są dobrym wyborem dla dowolnego rodzaju obliczeń tymczasowych, z następujących powodów:

- **Unikanie konfliktu nazw.** Nazwy zmiennych lokalnych nie są podatne na konflikt. Na przykład można utworzyć kilka różnych procedur zawierających zmienną o nazwie `intTemp`. O ile każda z `intTemp` nich jest zadeklarowana jako zmienna lokalna, każda procedura rozpoznaje tylko własną wersję programu `intTemp`. Każda procedura może zmienić wartość w jej lokalnej `intTemp` bez `intTemp` wpływu na zmienne w innych procedurach.

- **Użycie pamięci.** Zmienne lokalne zużywają pamięć tylko wtedy, gdy ich procedura jest uruchomiona. Pamięć jest wydawana, gdy procedura wraca do kodu wywołującego. Z kolei zmienne [udostępnione](../../../../visual-basic/language-reference/modifiers/shared.md) i [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) zużywają zasoby pamięci do momentu zatrzymania działania aplikacji, dlatego należy używać ich tylko w razie potrzeby. *Zmienne wystąpień* zużywają pamięć, gdy ich wystąpienie nadal istnieje, co sprawia, że są mniej wydajne niż zmienne lokalne, ale potencjalnie `Shared` bardziej `Static` wydajne niż lub zmienne.

### <a name="minimizing-scope"></a>Minimalizacja zakresu

Ogólnie rzecz biorąc, w przypadku deklarowania dowolnej zmiennej lub stałej jest dobrym sposobem programowania, aby zakres był możliwie wąski (zakres blokowy jest najwęższy). Pozwala to zaoszczędzić pamięć i zminimalizować prawdopodobieństwo błędnego kodu do niewłaściwej zmiennej. Podobnie należy zadeklarować zmienną, która ma być [statyczna](../../../../visual-basic/language-reference/modifiers/static.md) tylko wtedy, gdy jest to konieczne, aby zachować jej wartość między wywołaniami procedur.

## <a name="see-also"></a>Zobacz także

- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Instrukcje: Kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
