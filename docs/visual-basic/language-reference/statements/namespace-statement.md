---
title: "Namespace — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a>Namespace — Instrukcja
Deklaruje nazwę przestrzeni nazw i powoduje, że kod źródłowy znajdujący się deklaracji jest kompilowany w obrębie tej przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Części  
 Globalne  
 Opcjonalny. Można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu. Zobacz [przestrzeni nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Wymagany. Unikatowa nazwa, która identyfikuje przestrzeni nazw. Musi być prawidłowym identyfikatorem języka Visual Basic. Aby uzyskać więcej informacji, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Opcjonalny. Elementy wchodzące w skład przestrzeni nazw. Te obejmują, ale nie są ograniczone do wyliczenia, struktury, interfejsy, klasy, modułów, delegatów i innych przestrzeniach nazw.  
  
 `End Namespace`  
 Kończy `Namespace` bloku.  
  
## <a name="remarks"></a>Uwagi  
 Przestrzenie nazw są używane jako system organizacji. Umożliwiają one klasyfikowania i prezentowanie elementów programowania, które są widoczne dla innych programów i aplikacji. Należy pamiętać, że przestrzeń nazw nie jest *typu* w tym sensie, że klasy lub struktury — nie można zadeklarować elementu programistycznego typu danych w przestrzeni nazw.  
  
 Wszystkie elementy programowania zadeklarowanych po `Namespace` instrukcji należą do tej przestrzeni nazw. Visual Basic w dalszym ciągu skompilować elementy do ostatniego zadeklarowane przestrzeni nazw, aż do napotkania albo `End Namespace` instrukcji lub innym `Namespace` instrukcji.  
  
 Jeśli przestrzeń nazw już jest zdefiniowany, nawet poza projektem, programistyczny można dodać do niego. Aby to zrobić, należy użyć `Namespace` instrukcji, aby nakazać programowi Visual Basic, aby skompilować elementy do tej przestrzeni nazw.  
  
 Można użyć `Namespace` instrukcji tylko na poziomie pliku lub przestrzeni nazw. Oznacza to, że *kontekście deklaracji* dla przestrzeni nazw musi być plikiem źródłowym lub innej przestrzeni nazw i nie może być klasy, struktury, modułu, interfejsem lub procedury. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Można zadeklarować jednej przestrzeni nazw w innym. Nie ma żadnych strict limitu poziomów zagnieżdżenia zadeklarować, ale należy pamiętać, że gdy inny kod uzyskuje dostęp do elementów zadeklarowany w najbardziej przestrzeni nazw, należy użyć kwalifikacji ciąg, który zawiera wszystkie nazwy przestrzeni nazw w hierarchii zagnieżdżenia.  
  
## <a name="access-level"></a>Poziom dostępu  
 Przestrzenie nazw są traktowane jako mają `Public` poziom dostępu. Przestrzeń nazw są dostępne z kodu w dowolnym miejscu tego samego projektu z innych projektów, które odwołują się do projektu i z wszelkich zestawu utworzonego na podstawie projektu.  
  
 Elementy programowania zadeklarowane na poziomie przestrzeni nazw, co oznacza w przestrzeni nazw, ale nie znajduje się w innych elementów, może mieć `Public` lub `Friend` dostępu. Jeśli nie zostanie podany, poziom dostępu do takiego elementu używa `Friend` domyślnie. Elementy, które można zadeklarować na poziomie przestrzeni nazw obejmują klasy, struktury modułów, interfejsy, wyliczenia i delegaty. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Namespace głównego  
 Wszystkie nazwy przestrzeni nazw w projekcie są oparte na *głównej przestrzeni nazw*. Visual Studio przypisuje nazwę projektu jako domyślną przestrzeń nazw głównego dla całego kodu w projekcie. Na przykład, jeśli nosi nazwę projektu `Payroll`, jego element programistyczny należy do przestrzeni nazw `Payroll`. W przypadku `Namespace funding`, pełną nazwą tego obszaru nazw jest `Payroll.funding`.  
  
 Jeśli chcesz określić istniejącą przestrzenią nazw w `Namespace` instrukcji, takie jak w przykładzie klasa listy ogólnej, można ustawić przestrzeni nazw głównych ma wartość null. Aby to zrobić, kliknij przycisk **właściwości projektu** z **projektu** menu, a następnie wyczyść zaznaczenie **głównej przestrzeni nazw** wpis tak, że pole jest puste. Jeśli użytkownik nie zostało to wykonane w tym przykładzie klasa listy ogólnej, kompilator Visual Basic zajmie `System.Collections.Generic` jako nowej przestrzeni nazw w projekcie `Payroll`, pełną nazwą `Payroll.System.Collections.Generic`.  
  
 Alternatywnie można użyć `Global` — słowo kluczowe do odwoływania się do elementów przestrzenie nazw zdefiniowane poza projektem. Umożliwia to zachowują swoją nazwę projektu jako głównej przestrzeni nazw. Zmniejsza ryzyko przypadkowo scalenia programowania elementów wraz z istniejących przestrzeni nazw. Aby uzyskać więcej informacji, zobacz sekcję "— słowo kluczowe w pełni kwalifikowanej nazwy globalne" w [przestrzeni nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `Global` Można również użyć słowa kluczowego w instrukcji Namespace. Dzięki temu można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu. Aby uzyskać więcej informacji, zobacz sekcję "Globalne — słowo kluczowe w Namespace instrukcje" w [przestrzeni nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Rozwiązywanie problemów.** Główna przestrzeń nazw może prowadzić do nieoczekiwanego konkatenacji nazw przestrzeni nazw. Jeśli wprowadzisz odwołania do przestrzeni nazw zdefiniowane poza projektem, kompilator Visual Basic można nie tworzą je jako zagnieżdżony przestrzeni nazw w głównej przestrzeni nazw. W takim przypadku kompilator nie rozpoznaje żadnych typów, które zostały już zdefiniowane w zewnętrznych przestrzeni nazw. Aby tego uniknąć, ustaw przestrzeni nazw głównych ma wartość null, zgodnie z opisem w "Namespace głównego", lub użyj `Global` — słowo kluczowe elementy dostępu zewnętrznego przestrzeni nazw.  
  
## <a name="attributes-and-modifiers"></a>Atrybuty i Modyfikatory  
 Nie można zastosować atrybutów do przestrzeni nazw. Atrybut przyczynia się informacji metadanych zestawu, która nie jest zrozumiały dla klasyfikatory źródła, takich jak obszary nazw.  
  
 Dostęp do wszystkich lub procedury modyfikatorów ani innych modyfikatorów, nie można zastosować do przestrzeni nazw. Ponieważ nie jest typem, te modyfikatorów nie są istotne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje dwie przestrzenie nazw, jeden zagnieżdżone w innym.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje wiele zagnieżdżonych obszarów nazw w jednym wierszu, i jest odpowiednikiem poprzedniego przykładu.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład korzysta klasa zdefiniowana w poprzednich przykładach.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie definiuje szkielet nową klasę listy ogólnej i dodaje go do <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Imports — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
