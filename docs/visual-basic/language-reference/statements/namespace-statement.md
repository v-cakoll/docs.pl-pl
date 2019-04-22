---
title: Namespace — instrukcja (Visual Basic)
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
ms.openlocfilehash: 7f6b976af7933b3895f6992488d2d1532a8fc2f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820935"
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
  
 Jeśli chcesz określić istniejącą przestrzenią nazw w `Namespace` instrukcji, np. w tym przykładzie klasa listy ogólnej głównej przestrzeni nazw można ustawić wartości null. Aby to zrobić, kliknij przycisk **właściwości projektu** z **projektu** menu, a następnie wyczyść **głównej przestrzeni nazw** wpis, aby pole jest puste. Jeśli nie zrobisz to w przykładzie listy ogólnej klasy, kompilator Visual Basic zajęłoby `System.Collections.Generic` jako nową przestrzeń nazw w obrębie projektu `Payroll`, przy użyciu pełnej nazwy `Payroll.System.Collections.Generic`.  
  
 Alternatywnie, można użyć `Global` — słowo kluczowe do odwoływania się do elementów przestrzenie nazw zdefiniowane poza projektem. Umożliwia to zachować nazwę projektu jako głównej przestrzeni nazw. Zmniejsza to ryzyko przypadkowo scalania elementów programowania wraz z tymi istniejącej przestrzeni nazw. Aby uzyskać więcej informacji, zobacz sekcję "Globalne — słowo kluczowe w pełni kwalifikowanej nazwy" w [przestrzeni nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `Global` Również można użyć słowa kluczowego w instrukcji Namespace. Dzięki temu można zdefiniować obszar nazw poza głównej przestrzeni nazw projektu. Aby uzyskać więcej informacji, zobacz sekcję "Globalne — słowo kluczowe w Namespace instrukcji" w [przestrzeni nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Rozwiązywanie problemów.** Główna przestrzeń nazw może prowadzić do nieoczekiwanych konkatenacji nazw przestrzeni nazw. Jeśli odwołanie do przestrzeni nazw zdefiniowane poza projektem, kompilator Visual Basic mogą nie tworzą je jako zagnieżdżone przestrzenie nazw w głównej przestrzeni nazw. W takim przypadku kompilator nie rozpoznaje wszystkie typy, które zostały już zdefiniowane w przestrzeni nazw zewnętrznych. Aby tego uniknąć, ustaw głównej przestrzeni nazw ma wartość null, zgodnie z opisem w "Katalogu głównego Namespace" lub użyj `Global` — słowo kluczowe do dostępu do elementów zewnętrznych przestrzeni nazw.  
  
## <a name="attributes-and-modifiers"></a>Atrybuty i modyfikatorów  
 Nie można zastosować atrybutów do przestrzeni nazw. Atrybut przyczynia się informacji metadanych zestawu, który nie jest zrozumiały dla klasyfikatorów źródła, takie jak przestrzenie nazw.  
  
 Dostęp do wszystkich lub Modyfikatory procedury lub innych modyfikatorów nie można zastosować do przestrzeni nazw. Ponieważ nie jest typem, tych modyfikatorów nie są istotne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje dwie przestrzenie nazw, jednej zagnieżdżone w innych.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje wiele zagnieżdżone przestrzenie nazw w jednym wierszu i jest równoważny do poprzedniego przykładu.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład uzyskuje dostęp do klasy zdefiniowane w poprzednich przykładach.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje szkielet nową klasę listy ogólnej i dodaje go do <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.  
  
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
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
