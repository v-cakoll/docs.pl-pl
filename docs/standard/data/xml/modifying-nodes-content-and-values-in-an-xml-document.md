---
title: Modyfikowanie węzłów, zawartości i wartości w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
ms.openlocfilehash: f544b7d8472285095af9a71b1c24f94f61f93bc6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288826"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Modyfikowanie węzłów, zawartości i wartości w dokumencie XML
Istnieje wiele sposobów modyfikowania węzłów i zawartości w dokumencie. Dostępne możliwości:  
  
- Zmień wartość węzłów za pomocą <xref:System.Xml.XmlNode.Value%2A> właściwości.  
  
- Zmodyfikuj cały zestaw węzłów, zastępując węzły nowymi węzłami. Jest to wykonywane przy użyciu <xref:System.Xml.XmlNode.InnerXml%2A> właściwości.  
  
- Zamień istniejące węzły na nowe węzły przy użyciu <xref:System.Xml.XmlNode.RemoveChild%2A> metody.  
  
- Dodaj dodatkowe znaki do węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData> klasy przy <xref:System.Xml.XmlCharacterData.AppendData%2A> użyciu <xref:System.Xml.XmlCharacterData.InsertData%2A> metod, lub <xref:System.Xml.XmlCharacterData.ReplaceData%2A> .  
  
- Zmodyfikuj zawartość, usuwając zakres znaków przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody dla typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData> .  
  
 Prostą techniką zmiany wartości węzła jest użycie `node.Value = "new value";` . Poniższa tabela zawiera listę typów węzłów, na których działa ten pojedynczy wiersz kodu, oraz dokładnie jakie dane dla tego typu węzła są zmieniane.  
  
|Typ węzła|Zmieniono dane|  
|---------------|------------------|  
|Atrybut|Wartość atrybutu.|  
|CDATASection|Zawartość CDATASection.|  
|Komentarz|Zawartość komentarza.|  
|ProcessingInstruction|Zawartość, z wyłączeniem celu.|  
|Tekst|Zawartość tekstu.|  
|XmlDeclaration|Zawartość deklaracji, z wyłączeniem `<?xml` `?>` znaczników i.|  
|Białe znaki|Wartość odstępu. Można ustawić wartość jako jedną z czterech rozpoznanych białych znaków XML: Space, TAB, CR lub LF.|  
|SignificantWhitespace|Wartość znaczącego odstępu. Można ustawić wartość jako jedną z czterech rozpoznanych białych znaków XML: Space, TAB, CR lub LF.|  
  
 Każdy typ węzła niewymieniony w tabeli nie jest prawidłowym typem węzła, aby ustawić wartość. Ustawienie wartości na dowolnym innym typie węzła zgłasza <xref:System.InvalidOperationException> .  
  
 <xref:System.Xml.XmlNode.InnerXml%2A>Właściwość zmienia adiustację węzłów podrzędnych dla bieżącego węzła. Ustawienie tej właściwości zastępuje węzły podrzędne z przeanalizowana zawartością danego ciągu. Analizowanie odbywa się w kontekście bieżącego obszaru nazw. Ponadto program <xref:System.Xml.XmlNode.InnerXml%2A> usuwa nadmiarowe deklaracje przestrzeni nazw. W związku z tym wiele operacji wycinania i wklejania nie zwiększa rozmiaru dokumentu przy użyciu nadmiarowych deklaracji przestrzeni nazw. Dla przykładu kodu pokazującego efekt przestrzeni nazw w <xref:System.Xml.XmlNode.InnerXml%2A> operacji, zobacz <xref:System.Xml.XmlDocument.InnerXml%2A> Właściwość.  
  
 W przypadku korzystania <xref:System.Xml.XmlCharacterData.ReplaceData%2A> z <xref:System.Xml.XmlNode.RemoveChild%2A> metod i metody zwracają węzeł zastąpiony lub usunięty. Następnie można ponownie wstawić ten węzeł w innym miejscu w Document Object Model XML (DOM). <xref:System.Xml.XmlCharacterData.ReplaceData%2A>Metoda wykonuje dwie sprawdzenia poprawności w węźle wstawianym do dokumentu. Pierwsze sprawdzenie gwarantuje, że węzeł staje się elementem podrzędnym węzła, który może mieć węzły podrzędne tego typu. Druga kontrola gwarantuje, że wstawiany węzeł nie jest elementem nadrzędnym węzła, staje się elementem podrzędnym. Naruszenie jednego z tych warunków zgłasza <xref:System.InvalidOperationException> .  
  
 Jest to prawidłowe Dodawanie lub usuwanie elementu podrzędnego tylko do odczytu z węzła, który można edytować. Jednak próbuje zmodyfikować węzeł tylko do odczytu <xref:System.InvalidOperationException> . Przykładem jest modyfikowanie elementów podrzędnych <xref:System.Xml.XmlEntityReference> węzła. Elementy podrzędne są tylko do odczytu i nie można ich modyfikować. Każda próba ich zmodyfikowania wygeneruje <xref:System.InvalidOperationException> .  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
