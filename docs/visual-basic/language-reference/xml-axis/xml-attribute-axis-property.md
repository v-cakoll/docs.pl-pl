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
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352671"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Właściwości osi atrybutu XML (Visual Basic)
Zapewnia dostęp do wartości atrybutu dla obiektu <xref:System.Xml.Linq.XElement> lub do pierwszego elementu w kolekcji obiektów <xref:System.Xml.Linq.XElement>.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Części  
 `object`  
 Wymagana. Obiekt <xref:System.Xml.Linq.XElement> lub kolekcja obiektów <xref:System.Xml.Linq.XElement>.  
  
 .@  
 Wymagana. Wskazuje początek właściwości osi atrybutu.  
  
 <  
 Opcjonalna. Oznacza początek nazwy atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w Visual Basic.  
  
 `attribute`  
 Wymagana. Nazwa atrybutu, który ma zostać przypisany do formularza [`prefix`:]`name`.  
  
|Części|Opis|  
|----------|-----------------|  
|`prefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla atrybutu. Musi to być globalna przestrzeń nazw XML zdefiniowana za pomocą instrukcji `Imports`.|  
|`name`|Wymagana. Nazwa atrybutu lokalnego. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Opcjonalna. Oznacza koniec nazwy atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w Visual Basic.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ciąg, który zawiera wartość `attribute`. Jeśli nazwa atrybutu nie istnieje, zwracany jest `Nothing`.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć właściwości osi atrybutu XML, aby uzyskać dostęp do wartości atrybutu według nazwy z obiektu <xref:System.Xml.Linq.XElement> lub z pierwszego elementu w kolekcji obiektów <xref:System.Xml.Linq.XElement>. Możesz pobrać wartość atrybutu według nazwy lub dodać nowy atrybut do elementu, określając nową nazwę poprzedzoną identyfikatorem @.  
  
 W przypadku odwoływania się do atrybutu XML przy użyciu @ identyfikatora wartość atrybutu jest zwracana jako ciąg i nie trzeba jawnie określać właściwości <xref:System.Xml.Linq.XAttribute.Value%2A>.  
  
 Reguły nazewnictwa dla atrybutów XML różnią się od reguł nazewnictwa dla identyfikatorów Visual Basic. Aby uzyskać dostęp do atrybutu XML o nazwie, która nie jest prawidłowym identyfikatorem Visual Basic, ujmij ją w nawiasy kątowe (\< i >).  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Nazwa we właściwości osi atrybutu może używać tylko prefiksów przestrzeni nazw XML zadeklarowanych globalnie przy użyciu instrukcji `Imports`. Nie może używać prefiksów przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML o nazwach `phone`.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć atrybuty dla elementu XML w sposób deklaratywny, jako część pliku XML i dynamicznie przez dodanie atrybutu do wystąpienia obiektu <xref:System.Xml.Linq.XElement>. Atrybut `type` jest tworzony deklaratywnie, a atrybut `owner` jest tworzony dynamicznie.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Ten kod wyświetla następujący tekst:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto składni nawiasu ostrego, aby uzyskać wartość atrybutu XML o nazwie `number-type`, który nie jest prawidłowym identyfikatorem w Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone type: work`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
