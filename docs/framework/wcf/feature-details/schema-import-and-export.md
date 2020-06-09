---
title: Importowanie i eksportowanie schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: 942ade69d92d8a213f65a3a2e463b6924e2f986e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590218"
---
# <a name="schema-import-and-export"></a>Importowanie i eksportowanie schematu
Windows Communication Foundation (WCF) zawiera nowy aparat serializacji, <xref:System.Runtime.Serialization.DataContractSerializer> . `DataContractSerializer`Tłumaczy między obiektami .NET Framework i XML (w obu kierunkach). Oprócz programu szeregującego, WCF zawiera skojarzone mechanizmy importowania schematu i eksportowania schematu. *Schemat* to formalny, dokładny i czytelny dla maszyn opis kształtu XML, który tworzy serializator lub który Deserializator może uzyskać dostęp. Funkcja WCF używa organizacja World Wide Web Consortium (W3C) języka definicji schematu XML (XSD) jako reprezentacji schematu, która jest szeroko współdziałana z wieloma platformami innych firm.  
  
 Składnik importowania schematu, <xref:System.Runtime.Serialization.XsdDataContractImporter> , pobiera dokument schematu XSD i generuje klasy .NET Framework (zazwyczaj klasy kontraktu danych), tak że serializowane formularze odpowiadają danemu schematowi.  
  
 Na przykład poniższy fragment schematu:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 generuje następujący typ (uproszczony nieznacznie w celu zwiększenia czytelności).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Należy zauważyć, że wygenerowany typ jest zgodny z kilkoma najlepszymi rozwiązaniami dotyczącymi kontraktu dotyczącego danych (które są dostępne w [najlepszych rozwiązaniach: wersja kontraktu danych](../best-practices-data-contract-versioning.md)):  
  
- Typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs. Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](forward-compatible-data-contracts.md).  
  
- Elementy członkowskie danych są implementowane jako właściwości publiczne, które zawijają pola prywatne.  
  
- Klasa jest klasą częściową, a dodatki można wprowadzać bez modyfikowania kodu wygenerowanego.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>Umożliwia przeprowadzenie odwrócenia — wykonaj typy, które można serializować przy użyciu `DataContractSerializer` i Generuj dokument schematu XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Wierność nie jest gwarantowana  
 Nie gwarantuje to, że schemat lub typy przedają w wyniku rundy całkowitą wierność. (W wyniku *rundy* należy zaimportować schemat, aby utworzyć zestaw klas, i wyeksportować wynik, aby ponownie utworzyć schemat). Nie można zwrócić tego samego schematu. Odwrócenie procesu nie gwarantuje również zachowania dokładności. (Wyeksportuj typ, aby wygenerować jego schemat, a następnie zaimportuj typ z powrotem. Jest mało prawdopodobne, że zwracany jest ten sam typ.)  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Model kontraktu danych obsługuje tylko ograniczony podzbiór schematu WC3. Każdy schemat, który nie jest zgodny z tym podzbiorem, spowoduje wyjątek podczas procesu importowania. Na przykład nie istnieje sposób, aby określić, że element członkowski danych kontraktu danych powinien być serializowany jako atrybut XML. W związku z tym schematy, które wymagają użycia atrybutów XML, nie są obsługiwane i spowodują wyjątki podczas importowania, ponieważ nie można wygenerować kontraktu danych z poprawnym rzutowaniem XML.  
  
 Na przykład poniższy fragment schematu nie może zostać zaimportowany przy użyciu domyślnych ustawień importu.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Aby uzyskać więcej informacji, zobacz informacje o [schemacie kontraktu danych](data-contract-schema-reference.md). Jeśli schemat nie jest zgodny z regułami kontraktu danych, użyj innego aparatu serializacji. Na przykład <xref:System.Xml.Serialization.XmlSerializer> używa własnego mechanizmu importowania schematu. Ponadto istnieje specjalny tryb importu, w którym jest rozwinięty zakres obsługiwanego schematu. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą generowania <xref:System.Xml.Serialization.IXmlSerializable> typów w temacie [Importowanie schematu do generowania klas](importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter`Obsługuje wszystkie typy .NET Framework, które można serializować przy użyciu `DataContractSerializer` . Aby uzyskać więcej informacji, zobacz [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md). Należy zauważyć, że schemat wygenerowany przy użyciu `XsdDataContractExporter` jest zwykle prawidłowymi danymi, które `XsdDataContractImporter` mogą być używane (chyba że <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> jest używany do dostosowywania schematu).  
  
 Aby uzyskać więcej informacji o używaniu programu <xref:System.Runtime.Serialization.XsdDataContractImporter> , zobacz [Importowanie schematu do generowania klas](importing-schema-to-generate-classes.md).  
  
 Aby uzyskać więcej informacji o używaniu programu <xref:System.Runtime.Serialization.XsdDataContractExporter> , zobacz [Eksportowanie schematów z klas](exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Importowanie schematu w celu generowania klas](importing-schema-to-generate-classes.md)
- [Eksportowanie schematów z klas](exporting-schemas-from-classes.md)
