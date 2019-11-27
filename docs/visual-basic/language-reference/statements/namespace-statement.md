---
title: Namespace — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 19207a42890640bd82ec547e53eb6d833668e4b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329602"
---
# <a name="namespace-statement"></a>Namespace — Instrukcja
Deklaruje nazwę przestrzeni nazw i powoduje, że kod źródłowy znajdujący się w deklaracji jest kompilowany w obrębie tej przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Części  
 Global  
 Opcjonalna. Pozwala zdefiniować przestrzeń nazw poza główną przestrzenią nazw projektu. Zobacz [przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Wymagana. Unikatowa nazwa, która identyfikuje przestrzeń nazw. Musi być prawidłowym identyfikatorem języka Visual Basic. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Opcjonalna. Elementy wchodzące w skład przestrzeni nazw. Obejmują one między inymi: wyliczenia, struktury, interfejsy, klasy, moduły, delegaty i inne przestrzenie nazw.  
  
 `End Namespace`  
 Kończy blok `Namespace`.  
  
## <a name="remarks"></a>Uwagi  
 Przestrzenie nazw są używane jako system organizacyjny. Umożliwiają one klasyfikowanie i prezentowanie elementów programowania, które są widoczne dla innych programów i aplikacji. Należy zauważyć, że przestrzeń nazw nie jest *typem* w sensie, że Klasa lub struktura to — nie można zadeklarować elementu programistycznego w taki sposób, aby miał typ danych przestrzeni nazw.  
  
 Wszystkie elementy programistyczne zadeklarowane po instrukcji `Namespace` należy do tej przestrzeni nazw. Visual Basic kontynuuje Kompilowanie elementów do ostatnio zadeklarowanej przestrzeni nazw do momentu napotkania instrukcji `End Namespace` lub innej instrukcji `Namespace`.  
  
 Jeśli przestrzeń nazw jest już zdefiniowana (nawet poza projektem), można do niej dodać elementy programistyczne. W tym celu należy użyć instrukcji `Namespace`, aby skierować Visual Basic do kompilowania elementów w tej przestrzeni nazw.  
  
 Instrukcji `Namespace` można użyć tylko na poziomie pliku lub przestrzeni nazw. Oznacza to, że *kontekst deklaracji* dla przestrzeni nazw musi być plikiem źródłowym lub inną przestrzenią nazw i nie może być klasą, strukturą, modułem, interfejsem ani procedurą. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Można zadeklarować jedną przestrzeń nazw w innej. Nie ma żadnych ścisłych limitów poziomów zagnieżdżenia deklaracji, ale należy pamiętać, że gdy inny kod uzyskuje dostęp do elementów zadeklarowanych w najbardziej zagnieżdżonej przestrzeni nazw, należy użyć ciągu kwalifikacji, który zawiera nazwy wszystkich przestrzeni nazw w hierarchii zagnieżdżenia.  
  
## <a name="access-level"></a>Poziom dostępu  
 Przestrzenie nazw są traktowane tak, jakby miały `Public` poziomu dostępu. Przestrzenie nazw są dostępne z kodu w dowolnym miejscu tego samego projektu, z innych projektów, które odwołują się do projektu i z wszystkich zestawów utworzonych na podstawie projektu.  
  
 Elementy programistyczne zadeklarowane na poziomie przestrzeni nazw, znaczenie w przestrzeni nazw, ale nie w żadnym innym elemencie, mogą mieć `Public` lub `Friend` dostępu. Jeśli nie zostanie określony, poziom dostępu takiego elementu domyślnie używa `Friend`. Elementy, które można zadeklarować na poziomie przestrzeni nazw obejmują klasy, struktury, moduły, interfejsy, wyliczenia i delegaty. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Główna przestrzeń nazw  
 Wszystkie nazwy przestrzeni nazw w projekcie są oparte na *głównej przestrzeni nazw*. Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie. Na przykład jeśli projekt ma nazwę `Payroll`, jego elementy programistyczne należą do `Payroll`przestrzeni nazw. Jeśli zadeklarujesz `Namespace funding`, pełna nazwa tej przestrzeni nazw jest `Payroll.funding`.  
  
 Jeśli chcesz określić istniejącą przestrzeń nazw w instrukcji `Namespace`, na przykład w przykładowej klasie list generycznych, możesz ustawić główną przestrzeń nazw na wartość null. Aby to zrobić, kliknij pozycję **właściwości projektu** w menu **projekt** , a następnie wyczyść pozycję **główna przestrzeń nazw** , aby pole było puste. Jeśli nie zostało to zrobione w przykładowej klasie list ogólnych, kompilator Visual Basic będzie miał `System.Collections.Generic` jako nową przestrzeń nazw w `Payroll`projektu, z pełną nazwą `Payroll.System.Collections.Generic`.  
  
 Alternatywnie można użyć słowa kluczowego `Global`, aby odwołać się do elementów przestrzeni nazw zdefiniowanych poza projektem. Dzięki temu można zachować nazwę projektu jako główną przestrzeń nazw. Zmniejsza to możliwość przypadkowego scalania elementów programistycznych z tymi istniejącymi przestrzeniami nazw. Aby uzyskać więcej informacji, zobacz sekcję "globalne słowo kluczowe w w pełni kwalifikowanych nazw" w obszarze [nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 Słowa kluczowego `Global` można również użyć w instrukcji Namespace. Pozwala to definiować przestrzeń nazw poza główną przestrzenią nazw projektu. Aby uzyskać więcej informacji, zobacz sekcję "globalne słowo kluczowe w instrukcjach przestrzeni nazw" w obszarze [nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Rozwiązywanie problemów z.** Główna przestrzeń nazw może prowadzić do nieoczekiwanych łączenia nazw przestrzeni nazw. Jeśli wprowadzisz odwołanie do przestrzeni nazw zdefiniowanych poza projektem, kompilator Visual Basic może interpretować je jako zagnieżdżone przestrzenie nazw w głównej przestrzeni nazw. W takim przypadku kompilator nie rozpoznaje żadnych typów, które zostały już zdefiniowane w zewnętrznych przestrzeniach nazw. Aby tego uniknąć, należy ustawić w głównej przestrzeni nazw wartość null zgodnie z opisem w "głównej przestrzeni nazw" lub użyć słowa kluczowego `Global`, aby uzyskać dostęp do elementów zewnętrznych przestrzeni nazw.  
  
## <a name="attributes-and-modifiers"></a>Atrybuty i Modyfikatory  
 Nie można zastosować atrybutów do przestrzeni nazw. Atrybut zawiera informacje o metadanych zestawu, który nie jest znaczący dla klasyfikatorów źródłowych, takich jak przestrzenie nazw.  
  
 Nie można zastosować żadnych modyfikatorów dostępu ani procedur ani żadnych innych modyfikatorów do przestrzeni nazw. Ponieważ nie jest to typ, Modyfikatory te nie mają znaczenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje dwie przestrzenie nazw, jeden zagnieżdżony w drugim.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje wiele zagnieżdżonych przestrzeni nazw w jednym wierszu i jest odpowiednikiem poprzedniego przykładu.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uzyskuje dostęp do klasy zdefiniowanej w poprzednich przykładach.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje szkielet nowej klasy listy ogólnej i dodaje ją do przestrzeni nazw <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Zobacz także

- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
