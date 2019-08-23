---
title: Imports, instrukcja-przestrzeń nazw i typ .NET (Visual Basic)
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
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912388"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports — Instrukcja (.NET Namespace i Type)
Umożliwia odwoływanie się do nazw typów bez kwalifikacji przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`aliasname`|Opcjonalna. Alias lub nazwa *importu* , do `namespace` którego kod może odwoływać się zamiast pełnego ciągu kwalifikacji. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Wymagane. W pełni kwalifikowana nazwa importowanej przestrzeni nazw. Może być ciągiem przestrzeni nazw zagnieżdżonych na dowolnym poziomie.|  
|`element`|Opcjonalny. Nazwa elementu programowania zadeklarowanego w przestrzeni nazw. Może być dowolnym elementem kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 `Imports` Instrukcja włącza typy, które są zawarte w danej przestrzeni nazw, mają być bezpośrednio przywoływane.  
  
 Można podać nazwę pojedynczej przestrzeni nazw lub ciąg zagnieżdżonych przestrzeni nazw. Każda zagnieżdżona przestrzeń nazw jest oddzielona od kolejnej przestrzeni nazw wyższego`.`poziomu o kropkę (), jak pokazano w poniższym przykładzie.  
  
 `Imports System.Collections.Generic`  
  
 Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji. Muszą one być zgodne z dowolnymi deklaracjami `Option Strict` opcji, takimi jak instrukcja, i muszą poprzedzać deklaracje `Module` elementów `Class` programistycznych, takich jak lub instrukcji.  
  
 Można używać `Imports` tylko na poziomie pliku. Oznacza to, że kontekst deklaracji dla importu musi być plikiem źródłowym i nie może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem, procedurą lub blokiem.  
  
 Należy zauważyć, `Imports` że instrukcja nie udostępnia elementów z innych projektów i zestawów dostępnych dla projektu. Importowanie nie ma miejsca na ustawienie odwołania. Tylko eliminuje konieczność kwalifikowania nazw, które są już dostępne dla projektu. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w odniesieniu [do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
> Niejawne `Imports` instrukcje można definiować przy użyciu [strony odwołania, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Aby uzyskać więcej informacji, zobacz [jak: Dodaj lub Usuń zaimportowane przestrzenie nazw](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)(Visual Basic).  
  
## <a name="import-aliases"></a>Zaimportuj aliasy  
 *Alias importu* definiuje alias dla przestrzeni nazw lub typu. Aliasy importu są przydatne, gdy trzeba użyć elementów o tej samej nazwie, które są zadeklarowane w co najmniej jednym obszarze nazw. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "Kwalifikowanie nazwy elementu" w [odwołaniach do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Nie należy deklarować elementu członkowskiego na poziomie modułu o tej samej nazwie co `aliasname`. Jeśli to zrobisz, kompilator Visual Basic używa `aliasname` tylko dla zadeklarowanego elementu członkowskiego i nie rozpoznaje go już jako aliasu importu.  
  
 Mimo że składnia używana do deklarowania aliasu importu jest taka sama jak ta, która jest używana do importowania prefiksu przestrzeni nazw XML, wyniki są różne. Alias importu może służyć jako wyrażenie w kodzie, natomiast prefiks przestrzeni nazw XML może być używany tylko w literałach XML lub właściwościach osi XML jako prefiks dla kwalifikowanego elementu lub nazwy atrybutu.  
  
### <a name="element-names"></a>Nazwy elementów  
 Jeśli dostarczasz `element`, musi reprezentować *element kontenera*, czyli element programistyczny, który może zawierać inne elementy. Elementy kontenera obejmują klasy, struktury, moduły, interfejsy i wyliczenia.  
  
 Zakres elementów udostępnianych przez `Imports` instrukcję zależy od tego, czy określono. `element` Jeśli określisz tylko `namespace`, wszystkie jednoznacznie nazwane elementy członkowskie tej przestrzeni nazw i elementy członkowskie elementów kontenera w tej przestrzeni nazw są dostępne bez kwalifikacji. W przypadku określenia obu `namespace` elementów `element`i, tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca wszystkie foldery w C:\ Katalog przy użyciu <xref:System.IO.DirectoryInfo> klasy.  
  
 Kod nie zawiera żadnych `Imports` instrukcji w górnej części pliku. W związku z tym,, <xref:Microsoft.VisualBasic.ControlChars.CrLf> i odwołania są całkowicie kwalifikowane do przestrzeni nazw. `DirectoryInfo` <xref:System.Text.StringBuilder>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcje dla przestrzeni nazw, do których się odwołuje. W związku z tym typy nie muszą być w pełni kwalifikowane z przestrzeniami nazw.  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcje tworzące aliasy dla przestrzeni nazw, do których się odwołuje. Typy są kwalifikowane przy użyciu aliasów.  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera `Imports` instrukcje tworzące aliasy dla typów, do których istnieją odwołania. Aliasy są używane do określania typów.  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>Zobacz także

- [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Referencje i instrukcja Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
