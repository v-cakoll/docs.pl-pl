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
ms.openlocfilehash: e21cf160d10f308990894d1a85c4f5d05b90f68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace — Operator (Visual Basic)
Pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada określony prefiks przestrzeni nazw XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Części  
 `xmlNamespacePrefix`  
 Opcjonalna. Ciąg, który identyfikuje prefiks przestrzeni nazw XML. Jeśli podany, ten ciąg musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowany elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Jeśli określono bez prefiksu, jest zwracany domyślny obszar nazw. Jeśli nie domyślnej przestrzeni nazw jest określony, zwracana jest pusta przestrzeń nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XNamespace> Obiekt, który odpowiada prefiks przestrzeni nazw XML.  
  
## <a name="remarks"></a>Uwagi  
 `GetXmlNamespace` Uzyskuje operator <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada prefiks przestrzeni nazw XML `xmlNamespacePrefix`.  
  
 Możesz użyć prefiksy przestrzeni nazw XML bezpośrednio w literałach XML i właściwości osi XML. Jednak należy użyć `GetXmlNamespace` operatora prefiksu przestrzeni nazw, aby przekonwertować <xref:System.Xml.Linq.XNamespace> obiekt przed użyciem w kodzie. Możesz dołączyć nazwę elementu niekwalifikowane do <xref:System.Xml.Linq.XNamespace> obiektu można uzyskać w pełni kwalifikowanej <xref:System.Xml.Linq.XName> obiektów, które wielu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody wymagają.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępu do pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:phone`. Następnie przekazuje tego węzła podrzędnego do `ShowName` procedury, która tworzy nazwy kwalifikowanej przy użyciu `GetXmlNamespace` operatora. `ShowName` Podprocedury następnie przekazuje nazwę kwalifikowaną <xref:System.Xml.Linq.XNode.Ancestors%2A> metodę, aby pobrać element nadrzędny `ns:contact` węzła.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Podczas wywoływania `TestGetXmlNamespace.RunSample()`, wyświetla komunikat, który zawiera następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też  
 [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Uzyskiwanie dostępu do XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
