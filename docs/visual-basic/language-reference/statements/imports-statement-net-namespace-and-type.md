---
title: Imports — Instrukcja (.NET Namespace i Type)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: ef569b0ed6428d24d019e00c500e4d4b91c83d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports — Instrukcja (.NET Namespace i Type)
Umożliwia wpisz nazwy przywoływanie bez kwalifikacji przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`aliasname`|Opcjonalna. *Zaimportować alias* lub za pomocą którego kod może odwoływać się do nazwy `namespace` zamiast ciągu pełnej kwalifikacji. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Wymagana. Pełna nazwa importowanych przestrzeni nazw. Może być ciągiem przestrzeni nazw zagnieżdżone na dowolnym poziomie.|  
|`element`|Opcjonalna. Nazwa elementu programowania zadeklarowana w przestrzeni nazw. Może być dowolnym elemencie kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 `Imports` Instrukcji umożliwia typy, które są zawarte w danej przestrzeni nazw, aby odwoływać się bezpośrednio.  
  
 Można podać nazwę jednej przestrzeni nazw lub ciąg zagnieżdżonych obszarów nazw. Każdej zagnieżdżonej przestrzeni nazw jest oddzielona z następnym wyższym poziomu przestrzeni nazw kropką (`.`), jak pokazano w poniższym przykładzie.  
  
 `Imports System.Collections.Generic`  
  
 Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcje. Te należy wykonać wszelkimi deklaracjami opcji, takich jak `Option Strict` instrukcji i ich musi występować przed wszelkimi deklaracjami elementu programowania, takich jak `Module` lub `Class` instrukcje.  
  
 Można użyć `Imports` tylko na poziomie pliku. Oznacza to, w kontekście deklaracji Import musi być plikiem źródłowym i nie może być w przestrzeni nazw, klasy, struktury, modułu, interfejsu, procedurę lub blok.  
  
 Należy pamiętać, że `Imports` instrukcji nie udostępnia elementy z innych projektów i zespołów projektu. Importowanie nie odbywa się odwołanie do ustawienia. Tylko eliminuje konieczność na kwalifikować się nazw, które są już dostępne do projektu. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Można zdefiniować niejawne `Imports` instrukcji za pomocą [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>Importowanie aliasów  
 *Zaimportować alias* definiuje alias przestrzeni nazw lub typu. Importowanie aliasów są przydatne, gdy musisz użyć elementów o takiej samej nazwie, które są zadeklarowane w jedną lub kilka przestrzeni nazw. Więcej informacji oraz przykładem, zobacz "Kwalifikowanie nazwy elementu" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Nie należy deklarować Członkowskich na poziomie modułu z taką samą nazwę jak `aliasname`. Jeśli to zrobisz, kompilator Visual Basic używa `aliasname` tylko w przypadku zadeklarowanego elementu członkowskiego i nie rozpoznaje ją jako aliasu importu.  
  
 Mimo że składnia używana do deklarowania aliasu importu tak jak jest używany do importowania prefiks przestrzeni nazw XML, wyniki są różne. Aliasu importu można używać jako wyrażenia w kodzie, prefiks przestrzeni nazw XML można stosować tylko w literałach XML i właściwości osi XML jako prefiks kwalifikowaną elementu lub nazwa atrybutu.  
  
### <a name="element-names"></a>Nazwy elementów  
 Jeśli podasz `element`, musi reprezentować *element kontenera*, czyli programowania element, który może zawierać inne elementy. Elementy kontenera obejmują klasy, struktury, modułów, interfejsów i wyliczenia.  
  
 Zakres elementów udostępnione przez `Imports` instrukcji zależy od tego, czy wybrano `element`. Jeśli określisz tylko `namespace`, wszystkie jednoznacznie o nazwie członkami tej przestrzeni nazw i elementów członkowskich elementów kontenera w tej przestrzeni nazw, są dostępne bez kwalifikacji. Jeśli możesz określić ich obu `namespace` i `element`tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca wszystkie foldery w katalogu C:\ przy użyciu <xref:System.IO.DirectoryInfo> klasy.  
  
 Nie ma kodu `Imports` instrukcje w górnej części pliku. W związku z tym `DirectoryInfo`, <xref:System.Text.StringBuilder>, i <xref:Microsoft.VisualBasic.ControlChars.CrLf> odwołania są w pełni kwalifikowanej z przestrzeni nazw.  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcji, do którego istnieje odwołanie przestrzeni nazw. W związku z tym typów ma być w pełni kwalifikowana z przestrzeni nazw.  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów przywoływanego przestrzeni nazw. Typy są poprzedzone aliasów.  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów dla wskazanych typów. Aliasy służą do określania typów.  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
