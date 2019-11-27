---
title: GetXmlNamespace, operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353193"
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
  
 Prefiksy przestrzeni nazw XML można używać bezpośrednio w literałach XML i właściwościach osi XML. Należy jednak użyć operatora `GetXmlNamespace`, aby skonwertować prefiks przestrzeni nazw do obiektu <xref:System.Xml.Linq.XNamespace>, zanim będzie można go użyć w kodzie. Do obiektu <xref:System.Xml.Linq.XNamespace> można dołączyć niekwalifikowaną nazwę elementu, aby uzyskać w pełni kwalifikowany obiekt <xref:System.Xml.Linq.XName>, który jest wymagany przez wiele metod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i uzyskać dostęp do pierwszego węzła podrzędnego, który ma kwalifikowaną nazwę `ns:phone`. Następnie przekazuje ten węzeł podrzędny do podprocedury `ShowName`, która konstruuje kwalifikowaną nazwę przy użyciu operatora `GetXmlNamespace`. Podprocedura `ShowName` następnie przekazuje kwalifikowaną nazwę do metody <xref:System.Xml.Linq.XNode.Ancestors%2A>, aby uzyskać węzeł nadrzędny `ns:contact`.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Gdy wywołasz `TestGetXmlNamespace.RunSample()`, zostanie wyświetlone okno komunikatu zawierające następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz także

- [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Uzyskiwanie dostępu do pliku XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
