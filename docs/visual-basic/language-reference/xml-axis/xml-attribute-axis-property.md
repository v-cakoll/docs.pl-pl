---
title: Właściwości osi atrybutu XML (Visual Basic)
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
ms.openlocfilehash: 9107b946394ab70980e4865364fc1ba9683e2025
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785163"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Właściwości osi atrybutu XML (Visual Basic)
Zapewnia dostęp do wartości atrybutu dla <xref:System.Xml.Linq.XElement> obiektu lub do pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Części  
 `object`  
 Wymagane. <xref:System.Xml.Linq.XElement> Obiekt lub kolekcję <xref:System.Xml.Linq.XElement> obiektów.  
  
 .@  
 Wymagane. Oznacza początek właściwości osi atrybutu.  
  
 <  
 Opcjonalna. Oznacza początek nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.  
  
 `attribute`  
 Wymagane. Nazwa atrybutu, aby uzyskać dostęp, w postaci [`prefix`:]`name`.  
  
|Część|Opis|  
|----------|-----------------|  
|`prefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla atrybutu. Musi być globalnej przestrzeni nazw XML zdefiniowana z `Imports` instrukcji.|  
|`name`|Wymagane. Nazwa atrybutu lokalnego. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Opcjonalna. Oznacza koniec nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ciąg, który zawiera wartość `attribute`. Jeśli nazwa atrybutu nie istnieje, `Nothing` jest zwracana.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości osi atrybutu XML umożliwia dostęp do wartości atrybutu za pomocą nazwy z <xref:System.Xml.Linq.XElement> obiektu lub od pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów. Pobrać wartość atrybutu według nazwy lub dodać nowy atrybut do elementu, określając nowy nazwę poprzedzoną znakiem @ identyfikatora.  
  
 Gdy odwołasz się do atrybutu XML przy użyciu @ identyfikator, wartość atrybutu jest zwracany jako ciąg znaków i nie trzeba jawnie określić <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.  
  
 Reguły nazewnictwa dotyczące atrybutów XML różnią się od reguł nazewnictwa identyfikatorów języka Visual Basic. Aby uzyskać dostęp do atrybutu XML, który ma nazwę, która nie jest prawidłowym identyfikatorem języka Visual Basic, należy wpisać nazwę w nawiasy ostre (\< i >).  
  
## <a name="xml-namespaces"></a>Obszary nazw XML  
 Nazwa właściwości osi atrybutu można używać tylko takie prefiksy przestrzeni nazw XML, globalnie zadeklarowane za pomocą `Imports` instrukcji. Nie można go używać prefiksy przestrzeni nazw XML zadeklarowany lokalnie w literałach — element XML. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML, które są nazwane `phone`.  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak Utwórz atrybuty dla elementu XML zarówno deklaratywnie w ramach XML i dynamicznie przez dodawanie atrybutu do wystąpienia <xref:System.Xml.Linq.XElement> obiektu. `type` Atrybut jest tworzony w sposób deklaratywny i `owner` atrybutu jest tworzony dynamicznie.  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto składnię nawiasu ostrego, aby uzyskać wartość atrybutu XML o nazwie `number-type`, który nie jest prawidłowym identyfikatorem w języku Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone type: work`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o kwalifikowanej nazwie "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
