---
title: Imports — przestrzeń nazw XML
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 52864e4d1c8183b6243025e72368d23627049c84
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351062"
---
# <a name="imports-statement-xml-namespace"></a>Imports — Instrukcja (przestrzeń nazw XML)

Importuje prefiksy przestrzeni nazw XML do użycia w literałach XML i właściwościach osi XML.

## <a name="syntax"></a>Składnia

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Części

`xmlNamespacePrefix`  
Opcjonalna. Ciąg, przez który elementy i atrybuty XML mogą się odwoływać do `xmlNamespaceName`. Jeśli nie podano `xmlNamespacePrefix`, importowana przestrzeń nazw XML jest domyślną przestrzenią nazw XML. Musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Wymagana. Ciąg identyfikujący importowaną przestrzeń nazw XML.

## <a name="remarks"></a>Uwagi

Za pomocą instrukcji `Imports` można definiować globalne przestrzenie nazw XML, których można używać z literałami XML i właściwościami osi XML, lub jako parametry przesłane do operatora `GetXmlNamespace`. (Aby uzyskać informacje na temat używania instrukcji `Imports` do importowania aliasu, którego można użyć w przypadku używania nazw typów w kodzie, zobacz [Imports (przestrzeń nazw i typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md). Składnia do deklarowania przestrzeni nazw XML przy użyciu instrukcji `Imports` jest taka sama jak składnia użyta w kodzie XML. W związku z tym można skopiować deklarację przestrzeni nazw z pliku XML i użyć jej w instrukcji `Imports`.

Prefiksy przestrzeni nazw XML są przydatne, gdy chcesz wielokrotnie tworzyć elementy XML, które są z tego samego obszaru nazw. Prefiks przestrzeni nazw XML zadeklarowany za pomocą instrukcji `Imports` jest globalnie w sensie, że jest dostępny dla całego kodu w pliku. Można jej użyć podczas tworzenia literałów elementu XML i uzyskiwania dostępu do właściwości osi XML. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md).

Jeśli zdefiniujesz globalną przestrzeń nazw XML bez prefiksu przestrzeni nazw (na przykład `Imports <xmlns="http://SomeNameSpace>"`), ta przestrzeń nazw jest traktowana jako domyślna przestrzeń nazw XML. Domyślna przestrzeń nazw XML jest używana dla wszystkich literałów elementu XML lub właściwości osi XML, które nie określają jawnie przestrzeni nazw. Domyślna przestrzeń nazw jest również używana, jeśli określona przestrzeń nazw jest pustą przestrzenią nazw (czyli `xmlns=""`). Domyślna przestrzeń nazw XML nie ma zastosowania do atrybutów XML w literałach XML ani do właściwości osi atrybutu XML, które nie mają przestrzeni nazw.

Przestrzenie nazw XML, które są zdefiniowane w literale XML, które są nazywane *lokalnymi przestrzeniami nazw XML*, mają pierwszeństwo przed przestrzeniami nazw XML, które są zdefiniowane przez instrukcję `Imports` jako globalną. Przestrzenie nazw XML, które są zdefiniowane przez instrukcję `Imports`, mają pierwszeństwo przed przestrzeniami nazw XML importowanymi dla projektu Visual Basic. Jeśli literał XML definiuje przestrzeń nazw XML, ta lokalna przestrzeń nazw nie ma zastosowania do wyrażeń osadzonych.

Globalne przestrzenie nazw XML są zgodne z tymi samymi regułami określania zakresu i definicji co .NET Framework przestrzenie nazw. W związku z tym można dołączyć instrukcję `Imports`, aby zdefiniować globalną przestrzeń nazw XML w dowolnym miejscu, w którym można zaimportować .NET Framework przestrzeni nazw. Dotyczy to zarówno plików kodu, jak i importowanych przestrzeni nazw na poziomie projektu. Aby uzyskać informacje na temat importowanych przestrzeni nazw na poziomie projektu, zobacz [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Każdy plik źródłowy może zawierać dowolną liczbę instrukcji `Imports`. Muszą one być zgodne z deklaracjami opcji, takimi jak instrukcja `Option Strict`, i muszą poprzedzać deklaracje elementu programistycznego, takie jak instrukcje `Module` lub `Class`.

## <a name="example"></a>Przykład

Poniższy przykład importuje domyślną przestrzeń nazw XML i przestrzeń nazw XML zidentyfikowaną z prefiksem `ns`. Następnie tworzy literały XML używające obu przestrzeni nazw.

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

Ten kod wyświetla następujący tekst:

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a>Przykład

Poniższy przykład importuje prefiks przestrzeni nazw XML `ns`. Następnie tworzy literał XML, który używa prefiksu przestrzeni nazw i wyświetla ostateczną postać elementu.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Ten kod wyświetla następujący tekst:

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Zwróć uwagę, że kompilator przekonwertował prefiks przestrzeni nazw XML z globalnego prefiksu na definicję prefiksu lokalnego.

## <a name="example"></a>Przykład

Poniższy przykład importuje prefiks przestrzeni nazw XML `ns`. Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i uzyskać dostęp do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name`.

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Ten kod wyświetla następujący tekst:

`Patrick Hines`

## <a name="see-also"></a>Zobacz także

- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace, operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
