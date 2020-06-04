---
title: Właściwości osi atrybutu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408435"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Właściwości osi atrybutu XML (Visual Basic)
Zapewnia dostęp do wartości atrybutu dla <xref:System.Xml.Linq.XElement> obiektu lub do pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Części  
 `object`  
 Wymagany. <xref:System.Xml.Linq.XElement>Obiekt lub kolekcja <xref:System.Xml.Linq.XElement> obiektów.  
  
 .@  
 Wymagany. Wskazuje początek właściwości osi atrybutu.  
  
 <  
 Opcjonalny. Oznacza początek nazwy atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w Visual Basic.  
  
 `attribute`  
 Wymagany. Nazwa atrybutu do uzyskania dostępu w postaci [ `prefix` :] `name` .  
  
|Część|Opis|  
|----------|-----------------|  
|`prefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla atrybutu. Musi być globalną przestrzenią nazw XML zdefiniowaną za pomocą `Imports` instrukcji.|  
|`name`|Wymagany. Nazwa atrybutu lokalnego. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Opcjonalny. Oznacza koniec nazwy atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w Visual Basic.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ciąg, który zawiera wartość `attribute` . Jeśli nazwa atrybutu nie istnieje, `Nothing` jest zwracana.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć właściwości osi atrybutu XML, aby uzyskać dostęp do wartości atrybutu według nazwy z <xref:System.Xml.Linq.XElement> obiektu lub z pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów. Możesz pobrać wartość atrybutu według nazwy lub dodać nowy atrybut do elementu, określając nową nazwę poprzedzoną identyfikatorem @.  
  
 W przypadku odwoływania się do atrybutu XML przy użyciu @ identyfikatora wartość atrybutu jest zwracana jako ciąg i nie trzeba jawnie określać <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.  
  
 Reguły nazewnictwa dla atrybutów XML różnią się od reguł nazewnictwa dla identyfikatorów Visual Basic. Aby uzyskać dostęp do atrybutu XML o nazwie, która nie jest prawidłowym identyfikatorem Visual Basic, ujmij ją w nawiasy kątowe ( \< and > ).  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Nazwa we właściwości osi atrybutu może używać tylko prefiksów przestrzeni nazw XML zadeklarowanych globalnie przy użyciu `Imports` instrukcji. Nie może używać prefiksów przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML o nazwie `phone` .  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć atrybuty dla elementu XML w sposób deklaratywny, jako część pliku XML i dynamicznie przez dodanie atrybutu do wystąpienia <xref:System.Xml.Linq.XElement> obiektu. Ten `type` atrybut jest tworzony deklaratywnie, a `owner` atrybut jest tworzony dynamicznie.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Ten kod wyświetla następujący tekst:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto składni nawiasu ostrego, aby uzyskać wartość atrybutu XML o nazwie `number-type` , który nie jest prawidłowym identyfikatorem w Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone type: work`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy " `ns:name` ".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](index.md)
- [Literały XML](../xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Nazwy deklarowanych elementów XML oraz atrybuty](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
