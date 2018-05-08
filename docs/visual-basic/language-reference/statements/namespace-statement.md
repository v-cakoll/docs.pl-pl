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
ms.openlocfilehash: 15d8d8185d895502df594bbd931443af604bef67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 Opcjonalna. Pozwala zdefiniować przestrzeń nazw poza główną przestrzenią nazw projektu. Zobacz [Przestrzenie nazw Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Wymagana. Unikatowa nazwa, która identyfikuje przestrzeń nazw. Musi być prawidłowym identyfikatorem języka Visual Basic. Aby uzyskać więcej informacji, zobacz [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) (Deklarowane nazwy elementów).  
  
 `componenttypes`  
 Opcjonalna. Elementy wchodzące w skład przestrzeni nazw. Obejmują one między inymi: wyliczenia, struktury, interfejsy, klasy, moduły, delegaty i inne przestrzenie nazw.  
  
 `End Namespace`  
 Kończy blok `Namespace`.  
  
## <a name="remarks"></a>Uwagi  
 Przestrzenie nazw są używane jako system organizacyjny. Umożliwiają one klasyfikowanie i prezentowanie elementów programowania, które są widoczne dla innych programów i aplikacji.  Należy pamiętać, że przestrzeń nazw nie ma *typu* w takim sensie, jak klasy lub struktury — nie można zadeklarować elementu programistycznego posiadającego typ danych przestrzeni nazw.  
  
 Wszystkie elementy programowania zadeklarowane po instrukcji `Namespace` należą do tej przestrzeni nazw. Program Visual Basic kontynuuje kompilację elementów do ostatniej zadeklarowanej przestrzeni nazw dopóki do napotka instrukcji `End Namespace` lub kolejnej instrukcji `Namespace`.  
  
 Jeśli przestrzeń nazw jest już zdefiniowana (nawet poza projektem), można do niej dodać elementy programistyczne. Aby to zrobić, należy użyć instrukcji `Namespace`, aby nakazać programowi Visual Basic skompilowanie elementów do tej przestrzeni nazw.  
  
 Instrukcja `Namespace` może być używana tylko na poziomie pliku lub przestrzeni nazw.  Oznacza to, że *kontekstem deklaracji* dla przestrzeni nazw musi być plik źródłowy lub inna przestrzeń nazw i nie może być to klasa, struktura, moduł, interfejs ani procedura.  Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
 Można zadeklarować jedną przestrzeń nazw w innej. Nie ma żadnych ścisłych limitów poziomów zagnieżdżenia deklaracji, ale należy pamiętać, że gdy inny kod uzyskuje dostęp do elementów zadeklarowanych w najbardziej zagnieżdżonej przestrzeni nazw, należy użyć ciągu kwalifikacji, który zawiera nazwy wszystkich przestrzeni nazw w hierarchii zagnieżdżenia.  
  
## <a name="access-level"></a>Poziom dostępu  
 Przestrzenie nazw są traktowane tak, jakby miały publiczny (`Public`) poziom dostępu.  Przestrzenie nazw są dostępne z kodu w dowolnym miejscu tego samego projektu, z innych projektów, które odwołują się do projektu i z wszystkich zestawów utworzonych na podstawie projektu.  
  
 Elementy programistyczne zadeklarowane na poziomie przestrzeni nazw (to znaczy w przestrzeni nazw, ale nie wewnątrz innych elementów) mogą mieć poziom dostępu `Public` lub `Friend` dostępu. Jeśli nie zostanie podany, domyślnym poziomem dostępu takiego elementu jest `Friend`. Elementy, które można zadeklarować na poziomie przestrzeni nazw obejmują klasy, struktury, moduły, interfejsy, wyliczenia i delegaty. Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
## <a name="root-namespace"></a>Główna przestrzeń nazw  
 Wszystkie nazwy przestrzeni nazw w projekcie są oparte na *głównej przestrzeni nazw*. Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie.  Na przykład jeśli projekt nosi nazwę `Payroll`, jego elementy programistyczne należą do przestrzeni nazw `Payroll`. Jeśli zadeklarujesz `Namespace funding`, pełną nazwą tego obszaru nazw jest `Payroll.funding`.  
  
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
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
