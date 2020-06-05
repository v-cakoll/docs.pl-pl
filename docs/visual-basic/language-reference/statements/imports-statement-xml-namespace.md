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
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404540"
---
# <a name="imports-statement-xml-namespace"></a>Imports — Instrukcja (przestrzeń nazw XML)

Importuje prefiksy przestrzeni nazw XML do użycia w literałach XML i właściwościach osi XML.

## <a name="syntax"></a>Składnia

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Części

`xmlNamespacePrefix`  
Opcjonalny. Ciąg, do którego mogą się odwoływać elementy i atrybuty XML `xmlNamespaceName` . Jeśli nie `xmlNamespacePrefix` jest podany, importowana przestrzeń nazw XML jest domyślną przestrzenią nazw XML. Musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Wymagany. Ciąg identyfikujący importowaną przestrzeń nazw XML.

## <a name="remarks"></a>Uwagi

Możesz użyć instrukcji, `Imports` Aby zdefiniować globalne przestrzenie nazw XML, których można używać z literałami XML i właściwościami osi XML, lub jako parametry przesłane do `GetXmlNamespace` operatora. (Aby uzyskać informacje o używaniu `Imports` instrukcji do importowania aliasu, którego można użyć w przypadku używania nazw typów w kodzie, zobacz [Imports (przestrzeń nazw i typ platformy .NET)](imports-statement-net-namespace-and-type.md). Składnia do deklarowania przestrzeni nazw XML przy użyciu `Imports` instrukcji jest taka sama jak składnia użyta w kodzie XML. W związku z tym można skopiować deklarację przestrzeni nazw z pliku XML i użyć jej w `Imports` instrukcji.

Prefiksy przestrzeni nazw XML są przydatne, gdy chcesz wielokrotnie tworzyć elementy XML, które są z tego samego obszaru nazw. Prefiks przestrzeni nazw XML zadeklarowany za pomocą `Imports` instrukcji jest globalnie w sensie, że jest dostępny dla całego kodu w pliku. Można jej użyć podczas tworzenia literałów elementu XML i uzyskiwania dostępu do właściwości osi XML. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../xml-literals/xml-element-literal.md) i [Właściwości osi XML](../xml-axis/index.md).

Jeśli zdefiniujesz globalną przestrzeń nazw XML bez prefiksu przestrzeni nazw (na przykład `Imports <xmlns="http://SomeNameSpace>"` ), ta przestrzeń nazw jest traktowana jako domyślna przestrzeń nazw XML. Domyślna przestrzeń nazw XML jest używana dla wszystkich literałów elementu XML lub właściwości osi XML, które nie określają jawnie przestrzeni nazw. Domyślna przestrzeń nazw jest również używana, jeśli określona przestrzeń nazw jest pustą przestrzenią nazw (czyli `xmlns=""` ). Domyślna przestrzeń nazw XML nie ma zastosowania do atrybutów XML w literałach XML ani do właściwości osi atrybutu XML, które nie mają przestrzeni nazw.

Przestrzenie nazw XML, które są zdefiniowane w literale XML, które są nazywane *lokalnymi przestrzeniami nazw XML*, mają pierwszeństwo przed przestrzeniami nazw XML, które są zdefiniowane przez `Imports` instrukcję jako globalną. Przestrzenie nazw XML, które są zdefiniowane przez `Imports` instrukcję, mają pierwszeństwo przed przestrzeniami nazw XML importowanymi dla projektu Visual Basic. Jeśli literał XML definiuje przestrzeń nazw XML, ta lokalna przestrzeń nazw nie ma zastosowania do wyrażeń osadzonych.

Globalne przestrzenie nazw XML są zgodne z tymi samymi regułami określania zakresu i definicji co .NET Framework przestrzenie nazw. W związku z tym można dołączyć `Imports` instrukcję definiowania globalnej przestrzeni nazw XML w dowolnym miejscu, w którym można zaimportować .NET Framework przestrzeni nazw. Dotyczy to zarówno plików kodu, jak i importowanych przestrzeni nazw na poziomie projektu. Aby uzyskać informacje na temat importowanych przestrzeni nazw na poziomie projektu, zobacz [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji. Muszą one być zgodne z deklaracjami opcji, takimi jak `Option Strict` instrukcja, i muszą poprzedzać deklaracje elementów programistycznych, takich jak `Module` lub `Class` instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład importuje domyślną przestrzeń nazw XML i przestrzeń nazw XML zidentyfikowaną z prefiksem `ns` . Następnie tworzy literały XML używające obu przestrzeni nazw.

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

Poniższy przykład importuje prefiks przestrzeni nazw XML `ns` . Następnie tworzy literał XML, który używa prefiksu przestrzeni nazw i wyświetla ostateczną postać elementu.

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

Poniższy przykład importuje prefiks przestrzeni nazw XML `ns` . Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name` .

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Ten kod wyświetla następujący tekst:

`Patrick Hines`

## <a name="see-also"></a>Zobacz też

- [Literał elementu XML](../xml-literals/xml-element-literal.md)
- [Właściwości osi XML](../xml-axis/index.md)
- [Nazwy deklarowanych elementów XML oraz atrybuty](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace, operator](../operators/getxmlnamespace-operator.md)
