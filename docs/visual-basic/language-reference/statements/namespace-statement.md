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
ms.openlocfilehash: 0f1ba9a038fc604b6e4ede758891832e087fc096
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404437"
---
# <a name="namespace-statement"></a>Namespace — Instrukcja
Deklaruje nazwę przestrzeni nazw i powoduje, że kod źródłowy, który następuje po deklaracji, jest kompilowany w obrębie tej przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Części  
 Globalnie  
 Opcjonalny. Umożliwia zdefiniowanie przestrzeni nazw spoza głównej przestrzeni nazw projektu. Zobacz [przestrzenie nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Wymagany. Unikatowa nazwa identyfikująca przestrzeń nazw. Musi być prawidłowym identyfikatorem Visual Basic. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Opcjonalny. Elementy wchodzące w skład przestrzeni nazw. Obejmują one, ale nie są ograniczone do, wyliczenia, struktury, interfejsy, klasy, moduły, Delegaty i inne przestrzenie nazw.  
  
 `End Namespace`  
 Kończy `Namespace` blok.  
  
## <a name="remarks"></a>Uwagi  
 Przestrzenie nazw są używane jako system organizacyjny. Umożliwiają one klasyfikowanie i prezentowanie elementów programistycznych, które są dostępne dla innych programów i aplikacji. Należy zauważyć, że przestrzeń nazw nie jest *typem* w sensie, że Klasa lub struktura to — nie można zadeklarować elementu programistycznego w taki sposób, aby miał typ danych przestrzeni nazw.  
  
 Wszystkie elementy programistyczne zadeklarowane po `Namespace` instrukcji należy do tej przestrzeni nazw. Visual Basic kontynuuje Kompilowanie elementów do ostatnio zadeklarowanej przestrzeni nazw do momentu napotkania `End Namespace` instrukcji lub innej `Namespace` instrukcji.  
  
 Jeśli przestrzeń nazw jest już zdefiniowana, nawet poza projektem, można dodać do niej elementy programistyczne. W tym celu należy użyć instrukcji, `Namespace` Aby skierować Visual Basic do kompilowania elementów w tej przestrzeni nazw.  
  
 Instrukcji można używać `Namespace` tylko na poziomie pliku lub przestrzeni nazw. Oznacza to, że *kontekst deklaracji* dla przestrzeni nazw musi być plikiem źródłowym lub inną przestrzenią nazw i nie może być klasą, strukturą, modułem, interfejsem ani procedurą. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 Można zadeklarować jedną przestrzeń nazw w innym. Nie istnieje ścisły limit poziomów zagnieżdżenia, które można zadeklarować, ale należy pamiętać, że gdy inny kod uzyskuje dostęp do elementów zadeklarowanych w wewnętrznej przestrzeni nazw, musi użyć ciągu kwalifikacji, który zawiera wszystkie nazwy przestrzeni nazw w hierarchii zagnieżdżania.  
  
## <a name="access-level"></a>Poziom dostępu  
 Przestrzenie nazw są traktowane tak, jakby miały `Public` poziom dostępu. Do przestrzeni nazw można uzyskać dostęp z kodu dowolnego miejsca w tym samym projekcie, od innych projektów odwołujących się do projektu oraz z dowolnego zestawu skompilowanego z projektu.  
  
 Elementy programistyczne zadeklarowane na poziomie przestrzeni nazw, znaczenie w przestrzeni nazw, ale nie w żadnym innym elemencie, mogą mieć `Public` lub mieć `Friend` dostęp. Jeśli nie zostanie określony, poziom dostępu tego elementu jest domyślnie stosowany `Friend` . Elementy, które można zadeklarować na poziomie przestrzeni nazw, obejmują klasy, struktury, moduły, interfejsy, wyliczenia i delegatów. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Główna przestrzeń nazw  
 Wszystkie nazwy przestrzeni nazw w projekcie są oparte na *głównej przestrzeni nazw*. Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie. Na przykład jeśli projekt ma nazwę `Payroll` , jego elementy programistyczne należą do przestrzeni nazw `Payroll` . Jeśli zadeklarujesz `Namespace funding` , pełna nazwa tej przestrzeni nazw to `Payroll.funding` .  
  
 Jeśli chcesz określić istniejącą przestrzeń nazw w `Namespace` instrukcji, np. w przykładowej klasy listy ogólnej, możesz ustawić główną przestrzeń nazw na wartość null. Aby to zrobić, kliknij pozycję **właściwości projektu** w menu **projekt** , a następnie wyczyść pozycję **główna przestrzeń nazw** , aby pole było puste. Jeśli nie zostało to zrobione w przykładowej klasie listy ogólnej, kompilator Visual Basic będzie miał `System.Collections.Generic` jako nową przestrzeń nazw w ramach projektu `Payroll` , z pełną nazwą `Payroll.System.Collections.Generic` .  
  
 Alternatywnie można użyć `Global` słowa kluczowego, aby odwołać się do elementów przestrzeni nazw zdefiniowanych poza projektem. Dzięki temu można zachować nazwę projektu jako główną przestrzeń nazw. Zmniejsza to możliwość przypadkowego scalania elementów programistycznych z tymi istniejącymi przestrzeniami nazw. Aby uzyskać więcej informacji, zobacz sekcję "globalne słowo kluczowe w w pełni kwalifikowanych nazw" w obszarze [nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md).  
  
 `Global`Słowo kluczowe może być również używane w instrukcji Namespace. Pozwala to definiować przestrzeń nazw poza główną przestrzenią nazw projektu. Aby uzyskać więcej informacji, zobacz sekcję "globalne słowo kluczowe w instrukcjach przestrzeni nazw" w obszarze [nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md).  
  
 **Rozwiązywanie problemów z.** Główna przestrzeń nazw może prowadzić do nieoczekiwanych łączenia nazw przestrzeni nazw. Jeśli wprowadzisz odwołanie do przestrzeni nazw zdefiniowanych poza projektem, kompilator Visual Basic może interpretować je jako zagnieżdżone przestrzenie nazw w głównej przestrzeni nazw. W takim przypadku kompilator nie rozpoznaje żadnych typów, które zostały już zdefiniowane w zewnętrznych przestrzeniach nazw. Aby tego uniknąć, należy ustawić w głównej przestrzeni nazw wartość null zgodnie z opisem w części "główna przestrzeń nazw" lub użyć `Global` słowa kluczowego w celu uzyskania dostępu do elementów zewnętrznych przestrzeni nazw.  
  
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
 Poniższy przykład definiuje szkielet nowej klasy listy ogólnej i dodaje ją do <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Zobacz też

- [Imports — Instrukcja (.NET Namespace i Type)](imports-statement-net-namespace-and-type.md)
- [Nazwy zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Przestrzenie nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md)
