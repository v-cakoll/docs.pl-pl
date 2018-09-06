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
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786612"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace — Operator (Visual Basic)
Pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odpowiada określony prefiks przestrzeni nazw XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Części  
 `xmlNamespacePrefix`  
 Opcjonalna. Ciąg, który identyfikuje prefiks przestrzeni nazw XML. Jeśli zostanie podany, ten ciąg musi być prawidłowym identyfikatorem XML. Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowane elementy i atrybuty XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Jeśli określono żadnego prefiksu, zwracany jest domyślny obszar nazw. Jeśli nie domyślny obszar nazw jest określony, zwracany jest pusta przestrzeń nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XNamespace> Obiekt, który odnosi się do prefiksu przestrzeni nazw XML.  
  
## <a name="remarks"></a>Uwagi  
 `GetXmlNamespace` Operator pobiera <xref:System.Xml.Linq.XNamespace> obiekt, który odnosi się do prefiksu przestrzeni nazw XML `xmlNamespacePrefix`.  
  
 Możesz użyć prefiksy przestrzeni nazw XML bezpośrednio w literałach XML i właściwości osi XML. Jednakże, należy użyć `GetXmlNamespace` operatora konwersji prefiksu przestrzeni nazw <xref:System.Xml.Linq.XNamespace> obiekt przed jego użyciem w kodzie. Możesz dołączyć niekwalifikowane nazwy do <xref:System.Xml.Linq.XNamespace> można uzyskać w pełni kwalifikowanym <xref:System.Xml.Linq.XName> obiekt, który wielu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody wymagają.  
  
## <a name="example"></a>Przykład  
 Następujący przykład importuje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:phone`. Następnie przekazuje tego węzła podrzędnego do `ShowName` podprocedury, który konstruuje nazwa kwalifikowana za pomocą `GetXmlNamespace` operatora. `ShowName` Podprocedury następnie przekazuje kwalifikowanej nazwy, która <xref:System.Xml.Linq.XNode.Ancestors%2A> metodę, aby uzyskać element nadrzędny `ns:contact` węzła.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Gdy wywołujesz `TestGetXmlNamespace.RunSample()`, wyświetla okno komunikatu, który zawiera następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też  
 [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Uzyskiwanie dostępu do XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
