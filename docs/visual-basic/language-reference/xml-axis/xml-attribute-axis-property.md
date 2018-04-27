---
title: Właściwości osi atrybutu XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9968e5de0f8cb45fb896ba43c80d9c9a3ab8ef08
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Właściwości osi atrybutu XML (Visual Basic)
Zapewnia dostęp do wartości atrybutu <xref:System.Xml.Linq.XElement> obiektu lub do pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Części  
 `object`  
 Wymagana. <xref:System.Xml.Linq.XElement> Obiekcie lub kolekcji <xref:System.Xml.Linq.XElement> obiektów.  
  
 .@  
 Wymagana. Oznacza początek właściwości osi atrybutu.  
  
 <  
 Opcjonalna. Oznacza początek nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.  
  
 `attribute`  
 Wymagana. Nazwa atrybutu, aby uzyskać dostęp w formie [`prefix`:]`name`.  
  
|Część|Opis|  
|----------|-----------------|  
|`prefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla atrybutu. Musi być globalnej przestrzeni nazw XML zdefiniowany za pomocą `Imports` instrukcji.|  
|`name`|Wymagana. Nazwa atrybutu lokalnego. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Opcjonalna. Oznacza koniec nazwę atrybutu, gdy `attribute` nie jest prawidłowym identyfikatorem w języku Visual Basic.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ciąg zawierający wartość `attribute`. Jeśli nazwa atrybutu nie istnieje, `Nothing` jest zwracany.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości osi atrybutu XML służy do uzyskania dostępu do wartości atrybutu według nazwy z <xref:System.Xml.Linq.XElement> obiektu lub z pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> obiektów. Można pobrać wartość atrybutu o nazwie lub Dodaj nowy atrybut do elementu, określając nazwę nowej poprzedzone @ identyfikator.  
  
 Odwołań do atrybutu XML przy użyciu @ identyfikator, wartość atrybutu jest zwracana jako ciąg znaków i nie trzeba jawnie określać <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.  
  
 Reguły nazewnictwa dotyczące atrybutów XML różnią się od reguł nazewnictwa dla identyfikatorów języka Visual Basic. Aby uzyskać dostęp do atrybutu XML o nazwie, która nie jest prawidłowym identyfikatorem języka Visual Basic, należy wpisać nazwę w nawiasy (\< i >).  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Nazwa właściwości osi atrybutu można użyć tylko takie prefiksy przestrzeni nazw XML, zadeklarowany globalnie za pomocą `Imports` instrukcji. Nie można go użyć lokalnie zadeklarowane w literałach XML elementu prefiksy przestrzeni nazw XML. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać wartości atrybutów XML o nazwie `type` z kolekcji elementów XML, które są nazywane `phone`.  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia deklaratywnie jako część pliku XML i dynamicznie przez dodanie atrybutu do wystąpienia utworzyć atrybuty elementu XML zarówno <xref:System.Xml.Linq.XElement> obiektu. `type` Deklaratywnie utworzyć atrybutu i `owner` dynamicznie utworzyć atrybutu.  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto składni nawiasu ostrego można pobrać wartości atrybutu XML o nazwie `number-type`, która nie jest prawidłowym identyfikatorem w języku Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Phone type: work`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i dostępu do pierwszy węzeł podrzędny o nazwie kwalifikowanej "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
