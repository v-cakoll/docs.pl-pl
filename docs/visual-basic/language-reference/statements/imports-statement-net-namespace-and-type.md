---
title: Imports — instrukcja — .NET Namespace i Type (Visual Basic)
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
ms.openlocfilehash: 93b299ffd8d2be1b1fabfd752e75d18ef87714b2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974383"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports — Instrukcja (.NET Namespace i Type)
Pozwala wpisać nazwy przywoływanie bez kwalifikacji przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`aliasname`|Opcjonalna. *Zaimportować alias* lub za pomocą którego kod może odnosić się do nazwy `namespace` zamiast ciągu pełnej kwalifikacji. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Wymagana. W pełni kwalifikowana nazwa importowanych przestrzeni nazw. Może być ciągiem przestrzenie nazw zagnieżdżona na dowolnym poziomie.|  
|`element`|Opcjonalna. Nazwa elementu programistycznego zadeklarowanych w przestrzeni nazw. Może być dowolny element kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 `Imports` Instrukcji umożliwia typy, które są zawarte w danej przestrzeni nazw, aby odwoływać się bezpośrednio.  
  
 Możesz podać nazwę jednej przestrzeni nazw lub ciąg zagnieżdżone przestrzenie nazw. Każdy zagnieżdżone przestrzenie nazw są oddzielone od dalej wyższym poziomie przestrzeni nazw kropkę (`.`), tak jak pokazano w poniższym przykładzie.  
  
 `Imports System.Collections.Generic`  
  
 Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji. Te muszą być zgodne wszystkie deklaracje opcji, takich jak `Option Strict` instrukcji, dlatego musi poprzedzać żadnych deklaracji elementu programowania, takich jak `Module` lub `Class` instrukcji.  
  
 Możesz użyć `Imports` tylko na poziomie pliku. Oznacza to, kontekst deklaracji importowanie musi być plikiem źródłowym, a nie może być przestrzeni nazw, klasy, struktury, moduł, interfejsu, procedurę lub blok.  
  
 Należy pamiętać, że `Imports` instrukcji nie udostępnia elementy z innych projektów i zestawów do projektu. Importowanie nie odbywa się odwołanie do ustawienia. Powoduje tylko usunięcie potrzeby kwalifikowania nazwy, które są już dostępne do projektu. Aby uzyskać więcej informacji, zobacz "Importowanie zawierający elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Można zdefiniować niejawne `Imports` instrukcji za pomocą [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>Importowanie aliasów  
 *Zaimportować alias* definiuje aliasu dla typu lub przestrzeni nazw. Importowanie aliasów są przydatne, gdy należy użyć elementów o takiej samej nazwie, które są zadeklarowane w jeden lub kilka przestrzeni nazw. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz "Kwalifikowanie elementu Name" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Nie należy zadeklarować członka na poziomie modułu z taką samą nazwę jak `aliasname`. Jeśli to zrobisz, kompilator języka Visual Basic używa `aliasname` wyłącznie do zadeklarowanej składowej, a nie znajduje się już rozpoznaje je jako aliasu importu.  
  
 Mimo że składnia używane do deklarowania aliasu importu Krewny, który jest używany do importowania prefiks przestrzeni nazw XML, wyniki są różne. Import alias może służyć jako wyrażenia w swoim kodzie, prefiks przestrzeni nazw XML należy stosować tylko w literałach XML i właściwości osi XML jako prefiks dla elementu kwalifikowaną lub nazwa atrybutu.  
  
### <a name="element-names"></a>Nazwy elementów  
 Jeśli podasz `element`, musi reprezentować *element kontenera*, czyli programowania element, który może zawierać innych elementów. Elementy kontenera zawierają klasy, struktury, moduły, interfejsy i wyliczenia.  
  
 Zakres elementy udostępnione przez `Imports` instrukcja jest zależna od tego, czy należy określić `element`. Jeśli określisz tylko `namespace`, wszystkie jednoznacznie o nazwie członków tego obszaru nazw, a członkowie kontenerów elementów w obrębie tej przestrzeni nazw, są dostępne bez kwalifikacji. Jeśli określisz zarówno `namespace` i `element`tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca wszystkie foldery w katalogu C:\ przy użyciu <xref:System.IO.DirectoryInfo> klasy.  
  
 Nie ma kodu `Imports` instrukcji w górnej części pliku. W związku z tym `DirectoryInfo`, <xref:System.Text.StringBuilder>, i <xref:Microsoft.VisualBasic.ControlChars.CrLf> odwołania są w pełni kwalifikowaną z przestrzeni nazw.  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcji dla przywoływane obszary nazw. W związku z tym typy ma być w pełni kwalifikowana przestrzenie nazw.  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów przywoływane obszary nazw. Typy są kwalifikowany za pomocą aliasów.  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów dla typów odwołania. Aliasy są używane do określania typów.  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>Zobacz także
- [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
