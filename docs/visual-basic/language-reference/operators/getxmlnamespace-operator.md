---
title: GetXmlNamespace — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592166"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace — Operator (Visual Basic)
Pobiera obiekt <xref:System.Xml.Linq.XNamespace>, który odnosi się do określonego prefiksu przestrzeni nazw XML.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Części  
 `xmlNamespacePrefix`  
 Opcjonalny. Ciąg, który identyfikuje prefiks przestrzeni nazw XML. Jeśli jest podany, ten ciąg musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Jeśli nie określono żadnego prefiksu, zwracana jest domyślna przestrzeń nazw. Jeśli nie określono domyślnej przestrzeni nazw, zwracana jest pusta przestrzeń nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt <xref:System.Xml.Linq.XNamespace>, który odnosi się do prefiksu przestrzeni nazw XML.  
  
## <a name="remarks"></a>Uwagi  
 Operator `GetXmlNamespace` pobiera obiekt <xref:System.Xml.Linq.XNamespace>, który odnosi się do prefiksu przestrzeni nazw XML `xmlNamespacePrefix`.  
  
 Prefiksy przestrzeni nazw XML można używać bezpośrednio w literałach XML i właściwościach osi XML. Należy jednak użyć operatora `GetXmlNamespace`, aby przekonwertować prefiks przestrzeni nazw na obiekt <xref:System.Xml.Linq.XNamespace>, zanim będzie można go użyć w kodzie. Do obiektu <xref:System.Xml.Linq.XNamespace> można dołączyć niekwalifikowaną nazwę elementu, aby uzyskać w pełni kwalifikowany obiekt <xref:System.Xml.Linq.XName>, który wymaga wielu metod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i dostępu do pierwszego węzła podrzędnego, który ma kwalifikowaną nazwę `ns:phone`. Następnie przekazuje ten węzeł podrzędny do podprocedury `ShowName`, która konstruuje kwalifikowaną nazwę przy użyciu operatora `GetXmlNamespace`. Podprocedura `ShowName` przekazuje następnie nazwę kwalifikowaną do metody <xref:System.Xml.Linq.XNode.Ancestors%2A>, aby uzyskać nadrzędny węzeł `ns:contact`.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Gdy wywołasz `TestGetXmlNamespace.RunSample()`, zostanie wyświetlone okno komunikatu zawierające następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz także

- [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Uzyskiwanie dostępu do pliku XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
