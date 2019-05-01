---
title: Modyfikowanie węzłów, zawartości i wartości w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee45d983483d907b2a1e8b9e5ee12841e5c89c91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924114"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Modyfikowanie węzłów, zawartości i wartości w dokumencie XML
Istnieje wiele sposobów, można zmodyfikować węzłów i zawartości w dokumencie. Można:  
  
- Zmień wartość węzłów przy użyciu <xref:System.Xml.XmlNode.Value%2A> właściwości.  
  
- Zmodyfikuj cały zestaw węzłów, zastępując węzły nowe węzły. Odbywa się przy użyciu <xref:System.Xml.XmlNode.InnerXml%2A> właściwości.  
  
- Zamień istniejące węzły nowych węzłów przy użyciu <xref:System.Xml.XmlNode.RemoveChild%2A> metody.  
  
- Dodaj dodatkowe znaki do węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData> przy użyciu <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, lub <xref:System.Xml.XmlCharacterData.ReplaceData%2A> metody.  
  
- Modyfikowanie zawartości, usuwając szeroką gamę znaków, przy użyciu <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody w ramach typów węzłów, które dziedziczą z <xref:System.Xml.XmlCharacterData>.  
  
 Proste techniki, w przypadku zmiany wartości węzła jest użycie `node.Value = "new value";`. W poniższej tabeli wymieniono typy węzłów, które pracuje tego jednego wiersza kodu, i dokładnie dane dla tego typu węzła jest zmieniany.  
  
|Typ węzła|Zmiany danych|  
|---------------|------------------|  
|Atrybut|Wartość atrybutu.|  
|CDATASection|Zawartość CDATASection.|  
|Komentarz|Treść komentarza.|  
|ProcessingInstruction|Zawartość, z wyłączeniem element docelowy.|  
|Tekst|Zawartość tekstu.|  
|XmlDeclaration|Treść deklaracji, z wyłączeniem `<?xml` i `?>` znaczników.|  
|Białe znaki|Wartość wolnego miejsca. Można ustawić wartość była jedną z czterech rozpoznawanym białe znaki XML: miejsce, tab, CR lub LF.|  
|SignificantWhitespace|Wartość istotnych białych. Można ustawić wartość była jedną z czterech rozpoznawanym białe znaki XML: miejsce, tab, CR lub LF.|  
  
 Dowolny typ węzła nie są wymienione w tabeli nie jest typem nieprawidłowy węzeł, aby ustawić wartość na. Ustawienie wartości w przypadku dowolnego innego typu węzeł zgłasza <xref:System.InvalidOperationException>.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> Zmienia właściwość znaczników węzłów podrzędnych dla bieżącego węzła. Ustawienie tej właściwości jest zastępowany węzłów podrzędnych przeanalizowany zawartość podanego ciągu. Analiza odbywa się w bieżącym kontekście przestrzeni nazw. Ponadto <xref:System.Xml.XmlNode.InnerXml%2A> usuwa deklaracje przestrzeni nazw nadmiarowe. Jako wynik liczne wycinanie i wklejanie operacje zwiększa rozmiar dokumentu za pomocą deklaracje przestrzeni nazw nadmiarowe. Na przykład kod, przedstawiający efekt przestrzeni nazw na <xref:System.Xml.XmlNode.InnerXml%2A> operacji, zobacz <xref:System.Xml.XmlDocument.InnerXml%2A> właściwości.  
  
 Korzystając z <xref:System.Xml.XmlCharacterData.ReplaceData%2A> i <xref:System.Xml.XmlNode.RemoveChild%2A> metody, metody zwracają węzła zastąpione lub usunięta. Ten węzeł może następnie ponownie gdzieś else w XML Document Object Model (DOM). <xref:System.Xml.XmlCharacterData.ReplaceData%2A> Metoda wykonuje dwa sprawdzanie poprawności w węźle jest wstawiany do dokumentu. Sprawdź najpierw gwarantuje, że węzeł staje się elementem podrzędnym węzła, który może mieć węzłów podrzędnych dla jego typu. Drugi wyboru zapewnia, że węzeł jest wstawiany nie jest elementem nadrzędnym węzła, który staje się elementem podrzędnym. Naruszenie któraś z tych warunków zgłasza <xref:System.InvalidOperationException>.  
  
 Jest on prawidłowy, aby dodać lub usunąć element podrzędny tylko do odczytu z węzła, który można edytować. Jednak zgłasza próbuje zmodyfikować sam węzeł tylko do odczytu <xref:System.InvalidOperationException>. Na przykład modyfikuje element podrzędny elementu <xref:System.Xml.XmlEntityReference> węzła. Elementy podrzędne są przeznaczone tylko do odczytu i nie może być modyfikowany. Dowolne próba je zmodyfikować zgłasza <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
