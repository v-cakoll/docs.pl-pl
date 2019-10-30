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
ms.openlocfilehash: 573bb7383b292e0ad2e85a4355d89cf92fe8dd7d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040737"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports — Instrukcja (.NET Namespace i Type)

Umożliwia odwoływanie się do nazw typów bez kwalifikacji przestrzeni nazw.

## <a name="syntax"></a>Składnia

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`aliasname`|Opcjonalny. *Alias importu* lub nazwa, za pomocą którego kod może odwoływać się do `namespace` zamiast pełnego ciągu kwalifikacji. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`namespace`|Wymagany. W pełni kwalifikowana nazwa importowanej przestrzeni nazw. Może być ciągiem przestrzeni nazw zagnieżdżonych na dowolnym poziomie.|
|`element`|Opcjonalny. Nazwa elementu programowania zadeklarowanego w przestrzeni nazw. Może być dowolnym elementem kontenera.|

## <a name="remarks"></a>Uwagi

Instrukcja `Imports` umożliwia bezpośrednie wywoływanie typów zawartych w danej przestrzeni nazw.

Można podać nazwę pojedynczej przestrzeni nazw lub ciąg zagnieżdżonych przestrzeni nazw. Każda zagnieżdżona przestrzeń nazw jest oddzielona od kolejnej przestrzeni nazw wyższego poziomu przez okres (`.`), co ilustruje poniższy przykład:

```vb
Imports System.Collections.Generic
```

Każdy plik źródłowy może zawierać dowolną liczbę instrukcji `Imports`. Muszą one być zgodne z dowolnymi deklaracjami opcji, takimi jak instrukcja `Option Strict`, i muszą poprzedzać deklaracje elementów programistycznych, takie jak `Module` lub `Class` instrukcji.

`Imports` można użyć tylko na poziomie pliku. Oznacza to, że kontekst deklaracji dla importu musi być plikiem źródłowym i nie może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem, procedurą lub blokiem.

Należy zauważyć, że instrukcja `Imports` nie sprawia, że elementy z innych projektów i zestawów są dostępne dla projektu. Importowanie nie ma miejsca na ustawienie odwołania. Tylko eliminuje konieczność kwalifikowania nazw, które są już dostępne dla projektu. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odniesieniu do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

> [!NOTE]
> Niejawne instrukcje `Imports` można definiować przy użyciu [strony odwołania, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).

## <a name="import-aliases"></a>Zaimportuj aliasy

*Alias importu* definiuje alias dla przestrzeni nazw lub typu. Aliasy importu są przydatne, gdy trzeba użyć elementów o tej samej nazwie, które są zadeklarowane w co najmniej jednym obszarze nazw. Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "Kwalifikowanie nazwy elementu" w [odwołaniach do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Nie należy deklarować elementu członkowskiego na poziomie modułu o takiej samej nazwie jak `aliasname`. W takim przypadku kompilator Visual Basic używa `aliasname` tylko dla zadeklarowanego elementu członkowskiego i nie rozpoznaje go jako aliasu importu.

Mimo że składnia używana do deklarowania aliasu importu jest taka sama jak ta, która jest używana do importowania prefiksu przestrzeni nazw XML, wyniki są różne. Alias importu może służyć jako wyrażenie w kodzie, natomiast prefiks przestrzeni nazw XML może być używany tylko w literałach XML lub właściwościach osi XML jako prefiks dla kwalifikowanego elementu lub nazwy atrybutu.

### <a name="element-names"></a>Nazwy elementów

Jeśli podasz `element`, musi on reprezentować *element kontenera*, czyli element programistyczny, który może zawierać inne elementy. Elementy kontenera obejmują klasy, struktury, moduły, interfejsy i wyliczenia.

Zakres elementów udostępnianych przez instrukcję `Imports` zależy od tego, czy określono `element`. Jeśli określisz tylko `namespace`, wszystkie jednoznacznie nazwane elementy członkowskie tej przestrzeni nazw oraz członkowie elementów kontenera w tej przestrzeni nazw są dostępne bez kwalifikacji. Jeśli określisz zarówno `namespace` i `element`, tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.

## <a name="example"></a>Przykład

Poniższy przykład zwraca wszystkie foldery w katalogu *C:\\* przy użyciu klasy <xref:System.IO.DirectoryInfo>:

Kod nie zawiera instrukcji `Imports` w górnej części pliku. W związku z tym odwołania <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>i <xref:Microsoft.VisualBasic.ControlChars.CrLf> są całkowicie kwalifikowane do przestrzeni nazw.

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a>Przykład

Poniższy przykład zawiera instrukcje `Imports` dla przestrzeni nazw, do których się odwołuje. W związku z tym typy nie muszą być w pełni kwalifikowane z przestrzeniami nazw.

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a>Przykład

Poniższy przykład zawiera instrukcje `Imports`, które tworzą aliasy dla przywoływanych przestrzeni nazw. Typy są kwalifikowane przy użyciu aliasów.

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a>Przykład

Poniższy przykład zawiera instrukcje `Imports`, które tworzą aliasy dla typów, do których istnieją odwołania. Aliasy są używane do określania typów.

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a>Zobacz także

- [Namespace, instrukcja](namespace-statement.md)
- [Przestrzenie nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Referencje i instrukcja Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports, instrukcja (przestrzeń nazw XML)](imports-statement-xml-namespace.md)
- [Odwołania do elementów zadeklarowanych](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
