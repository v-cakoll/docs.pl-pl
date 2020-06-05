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
ms.openlocfilehash: 85422fb9e11d78e228577adc25cba746149c645a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371119"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace — Operator (Visual Basic)
Pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do określonego prefiksu przestrzeni nazw XML.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Części  
 `xmlNamespacePrefix`  
 Opcjonalny. Ciąg, który identyfikuje prefiks przestrzeni nazw XML. Jeśli jest podany, ten ciąg musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Jeśli nie określono żadnego prefiksu, zwracana jest domyślna przestrzeń nazw. Jeśli nie określono domyślnej przestrzeni nazw, zwracana jest pusta przestrzeń nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XNamespace>Obiekt, który odnosi się do prefiksu przestrzeni nazw XML.  
  
## <a name="remarks"></a>Uwagi  
 `GetXmlNamespace`Operator pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do prefiksu przestrzeni nazw XML `xmlNamespacePrefix` .  
  
 Prefiksy przestrzeni nazw XML można używać bezpośrednio w literałach XML i właściwościach osi XML. Należy jednak użyć `GetXmlNamespace` operatora, aby przekonwertować prefiks przestrzeni nazw na <xref:System.Xml.Linq.XNamespace> obiekt, zanim będzie można go użyć w kodzie. Do obiektu można dołączyć niekwalifikowaną nazwę elementu <xref:System.Xml.Linq.XNamespace> , aby uzyskać w pełni kwalifikowany <xref:System.Xml.Linq.XName> obiekt, którego [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wymaga wiele metod.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i uzyskać dostęp do pierwszego węzła podrzędnego, który ma kwalifikowaną nazwę `ns:phone` . Następnie przekazuje ten węzeł podrzędny do `ShowName` podprocedury, która konstruuje kwalifikowaną nazwę przy użyciu `GetXmlNamespace` operatora. `ShowName`Procedura ta przekazuje nazwę kwalifikowaną do <xref:System.Xml.Linq.XNode.Ancestors%2A> metody w celu pobrania `ns:contact` węzła nadrzędnego.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Po wywołaniu programu zostanie `TestGetXmlNamespace.RunSample()` wyświetlone okno komunikatu zawierające następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też

- [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](../../programming-guide/language-features/xml/accessing-xml.md)
