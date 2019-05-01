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
ms.openlocfilehash: 9f13f9d95c40b964c5eb416c590a5d603d714bac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991019"
---
# <a name="schema-import-and-export"></a>Importowanie i eksportowanie schematu
Windows Communication Foundation (WCF) obejmuje nowy mechanizm serializacji, <xref:System.Runtime.Serialization.DataContractSerializer>. `DataContractSerializer` Tłumaczy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów i XML (w obu kierunkach). Oprócz samego elementu serializującego WCF obejmuje import skojarzonego schematu i mechanizmy eksportu schematu. *Schemat* jest posiadanie, dokładne i czytelnym opis kształt XML generuje serializator lub Deserializator mogą uzyskiwać dostęp do. WCF używa języka definicji schematu XML World Wide Web Consortium (W3C) (XSD) jako jego reprezentację schematu i jest szeroko współpracujący z wieloma platformami innych firm.  
  
 Składnik Importuj schemat <xref:System.Runtime.Serialization.XsdDataContractImporter>, przejście do dokumentu schematu XSD i generuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klas (zwykle klasy kontraktu danych) w taki sposób, że serializacji formularzy odnoszą się do danego schematu.  
  
 Na przykład poniższy schemat fragment:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 generuje następujący typ (uproszczony nieznacznie w celu zwiększenia czytelności).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Należy pamiętać, że wygenerowany typ następuje kilka danych kontraktu najlepszych rozwiązań (znalezione w [najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
- Typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
- Elementy członkowskie danych są implementowane jako właściwości publiczne, które umieszczają w otoce pól prywatnych.  
  
- Klasa jest klasą częściowe i dodatków jest możliwe bez konieczności modyfikowania kodu wygenerowanego.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Umożliwia sytuacja odwrotna — zająć typy, które są możliwe do serializacji z `DataContractSerializer` i generowania dokumentu schematu XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Dokładność nie jest gwarantowana.  
 Nie gwarantuje, że schematu lub typów wykonywać rund, za pomocą całkowita wierności. (A *obiegu* oznacza, że importowanie schematu, aby utworzyć zestaw klas i eksportowanie wyników, aby ponownie utworzyć schemat.) Nie można zwrócić ten sam schemat. Odwrócenie procesu również nie musi zachować wierność. (W tym celu należy wyeksportować typu do generowania jego schematu, a następnie zaimportuj typ ponownie. Jest mało prawdopodobne, zwracany jest ten sam typ).  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Model kontraktu danych obsługuje tylko ograniczony podzestaw schematu WC3. Żadnego schematu, który nie jest zgodny z tym podzbiorem spowoduje, że wyjątek w trakcie procesu importowania. Na przykład nie istnieje żaden sposób, aby określić, czy element członkowski danych kontraktu danych powinien zostać Zserializowany jako atrybut XML. W związku z tym schematów, które wymagają używania atrybutów XML nie są obsługiwane i spowoduje, że wyjątki podczas importowania, ponieważ nie jest możliwe do generowania kontraktu danych za pomocą poprawne projekcji XML.  
  
 Na przykład poniższy fragment schematu nie można zaimportować przy użyciu domyślnych ustawień importu.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Jeśli schemat nie jest zgodny z regułami kontraktu danych, za pomocą aparatu różnych serializacji. Na przykład <xref:System.Xml.Serialization.XmlSerializer> używa własny mechanizm Importowanie schematu oddzielne. Ponadto jest tryb import specjalne, w którym jest rozwinięta, zakres obsługiwanych schematu. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą generowania <xref:System.Xml.Serialization.IXmlSerializable> wpisuje [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter` Obsługiwane [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które może być serializowany z `DataContractSerializer`. Aby uzyskać więcej informacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Należy pamiętać, tym schemacie wygenerowany za pomocą `XsdDataContractExporter` jest zwykle prawidłowe dane, `XsdDataContractImporter` można użyć (chyba że <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> umożliwia dostosowanie schematu).  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Runtime.Serialization.XsdDataContractImporter>, zobacz [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Runtime.Serialization.XsdDataContractExporter>, zobacz [eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Importowanie schematu w celu generowania klas](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
- [Eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
