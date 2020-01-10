---
title: Modyfikowanie węzłów, zawartości i wartości w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
ms.openlocfilehash: 4a53ba4fe16a3653b1be380da49e6b75cb347a28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710677"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Modyfikowanie węzłów, zawartości i wartości w dokumencie XML
Istnieje wiele sposobów modyfikowania węzłów i zawartości w dokumencie. Można:  
  
- Zmień wartość węzłów za pomocą właściwości <xref:System.Xml.XmlNode.Value%2A>.  
  
- Zmodyfikuj cały zestaw węzłów, zastępując węzły nowymi węzłami. Jest to realizowane przy użyciu właściwości <xref:System.Xml.XmlNode.InnerXml%2A>.  
  
- Zamień istniejące węzły na nowe węzły przy użyciu metody <xref:System.Xml.XmlNode.RemoveChild%2A>.  
  
- Dodaj dodatkowe znaki do węzłów, które dziedziczą z klasy <xref:System.Xml.XmlCharacterData> przy użyciu metod <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>lub <xref:System.Xml.XmlCharacterData.ReplaceData%2A>.  
  
- Zmodyfikuj zawartość, usuwając zakres znaków przy użyciu metody <xref:System.Xml.XmlCharacterData.DeleteData%2A> w typach węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>.  
  
 Prostą techniką zmiany wartości węzła jest użycie `node.Value = "new value";`. Poniższa tabela zawiera listę typów węzłów, na których działa ten pojedynczy wiersz kodu, oraz dokładnie jakie dane dla tego typu węzła są zmieniane.  
  
|Typ węzła|Zmieniono dane|  
|---------------|------------------|  
|Atrybut|Wartość atrybutu.|  
|CDATASection|Zawartość CDATASection.|  
|Komentarz|Zawartość komentarza.|  
|ProcessingInstruction|Zawartość, z wyłączeniem celu.|  
|Tekst|Zawartość tekstu|  
|XmlDeclaration|Zawartość deklaracji, z wyłączeniem `<?xml` i `?>` znaczników.|  
|Odstępu|Wartość odstępu. Można ustawić wartość jako jedną z czterech rozpoznanych białych znaków XML: Space, TAB, CR lub LF.|  
|SignificantWhitespace|Wartość znaczącego odstępu. Można ustawić wartość jako jedną z czterech rozpoznanych białych znaków XML: Space, TAB, CR lub LF.|  
  
 Każdy typ węzła niewymieniony w tabeli nie jest prawidłowym typem węzła, aby ustawić wartość. Ustawienie wartości na dowolnym innym typie węzła zgłasza <xref:System.InvalidOperationException>.  
  
 Właściwość <xref:System.Xml.XmlNode.InnerXml%2A> zmienia adiustację węzłów podrzędnych dla bieżącego węzła. Ustawienie tej właściwości zastępuje węzły podrzędne z przeanalizowana zawartością danego ciągu. Analizowanie odbywa się w kontekście bieżącego obszaru nazw. Ponadto <xref:System.Xml.XmlNode.InnerXml%2A> usuwa nadmiarowe deklaracje przestrzeni nazw. W związku z tym wiele operacji wycinania i wklejania nie zwiększa rozmiaru dokumentu przy użyciu nadmiarowych deklaracji przestrzeni nazw. Aby zapoznać się z przykładem kodu pokazującym wpływ przestrzeni nazw na <xref:System.Xml.XmlNode.InnerXml%2A> operacji, zobacz Właściwość <xref:System.Xml.XmlDocument.InnerXml%2A>.  
  
 W przypadku korzystania z metod <xref:System.Xml.XmlCharacterData.ReplaceData%2A> i <xref:System.Xml.XmlNode.RemoveChild%2A> metody zwracają węzeł zastąpiony lub usunięty. Następnie można ponownie wstawić ten węzeł w innym miejscu w Document Object Model XML (DOM). Metoda <xref:System.Xml.XmlCharacterData.ReplaceData%2A> wykonuje dwie sprawdzenia poprawności w węźle wstawianym do dokumentu. Pierwsze sprawdzenie gwarantuje, że węzeł staje się elementem podrzędnym węzła, który może mieć węzły podrzędne tego typu. Druga kontrola gwarantuje, że wstawiany węzeł nie jest elementem nadrzędnym węzła, staje się elementem podrzędnym. Naruszenie jednego z tych warunków zgłasza <xref:System.InvalidOperationException>.  
  
 Jest to prawidłowe Dodawanie lub usuwanie elementu podrzędnego tylko do odczytu z węzła, który można edytować. Jednak próbuje zmodyfikować węzeł tylko do odczytu w celu wyrzucania <xref:System.InvalidOperationException>. Przykładem jest modyfikowanie elementów podrzędnych węzła <xref:System.Xml.XmlEntityReference>. Elementy podrzędne są tylko do odczytu i nie można ich modyfikować. Każda próba ich zmodyfikowania zgłasza <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
