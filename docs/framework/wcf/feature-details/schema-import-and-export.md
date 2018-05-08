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
ms.openlocfilehash: c9bb0d6df362380a37ae3079694ab91e9577741d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="schema-import-and-export"></a>Importowanie i eksportowanie schematu
Windows Communication Foundation (WCF) obejmuje nowy aparat serializacji <xref:System.Runtime.Serialization.DataContractSerializer>. `DataContractSerializer` Tłumaczy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiektów i XML (w obu kierunkach). Oprócz samego elementu serializującego WCF zawiera importu skojarzony schemat i mechanizmów eksportowania schematu. *Schemat* jest posiadanie, dokładne i czytelną opis kształtu XML tworzącego serializator lub które mogą uzyskiwać dostęp do deserializacji. Usługi WCF używa języka definicji sieci World Wide Web konsorcjum W3C schematu XML (XSD) jako jego reprezentacja schemat, który jest powszechnie współdziała z wielu platform innych firm.  
  
 Składnik importowania schematu <xref:System.Runtime.Serialization.XsdDataContractImporter>, pobiera dokument schematu XSD i generuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy (zwykle klasy kontraktu danych) w taki sposób, że serializacji formularze odpowiadają dany schemat.  
  
 Na przykład poniższy schemat fragment:  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 generuje następujący typ (uproszczony nieco w celu zwiększenia czytelności).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Należy pamiętać, że wygenerowany typ postępuje kilka danych kontraktu najlepsze rozwiązania (znalezione w [najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
-   Typ implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
-   Elementy członkowskie danych są zaimplementowane jako właściwości publiczne, które otaczają pól prywatnych.  
  
-   Klasa jest klasą częściowe i dodatków jest możliwe bez modyfikowania wygenerowanego kodu.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> Umożliwia sytuacja odwrotna — zająć typy, które są do serializacji z `DataContractSerializer` i wygenerować dokumentu schematu XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Dokładność nie jest gwarantowana.  
 Nie gwarantuje, że schemat lub typów dokonać podróż z całkowitej wierności. (A *Rundy* oznacza, że można zaimportować schematu, aby utworzyć zestaw klas i eksportowanie wyników do ponownego utworzenia schematu.) Nie można zwrócić tego samego schematu. Odwracanie proces jest również nie gwarantuje zachować wierność. (W tym celu należy wyeksportować typu do generowania schematem, a następnie zaimportuj ponownie typu. Jest mało prawdopodobne, zwracany jest ten sam typ).  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Model kontraktu danych obsługuje tylko ograniczony podzestaw WC3 schematu. Wystąpił wyjątek podczas procesu importowania spowoduje, że żadnego schematu, który nie jest zgodna z tego podzbioru. Na przykład nie istnieje żaden sposób, aby określić, że element członkowski danych klasy kontraktu danych powinny być zserializowane jako atrybutu XML. W związku z tym schematów, które wymagają używania atrybutów XML nie są obsługiwane i spowoduje, że wyjątki podczas importowania, ponieważ nie można wygenerować kontrakt danych o poprawne projekcji XML.  
  
 Na przykład poniższy fragment schematu nie można zaimportować z ustawieniami domyślnymi importu.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Aby uzyskać więcej informacji, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Jeśli schemat nie jest zgodny z regułami kontraktu danych, należy użyć aparatu różnych serializacji. Na przykład <xref:System.Xml.Serialization.XmlSerializer> używa własnego mechanizmu importu oddzielne schematu. Jest również tryb specjalne importu, w którym jest rozwinięta zakres obsługiwanych schematu. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą generowania <xref:System.Xml.Serialization.IXmlSerializable> typy w [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter` Obsługuje dowolne [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które może być serializowany z `DataContractSerializer`. Aby uzyskać więcej informacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Należy pamiętać, schemat wygenerowanych przy użyciu `XsdDataContractExporter` jest zwykle prawidłowych danych który `XsdDataContractImporter` można użyć (chyba że <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> służy do dostosowywania schematu).  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Runtime.Serialization.XsdDataContractImporter>, zobacz [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Runtime.Serialization.XsdDataContractExporter>, zobacz [eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [Importowanie schematu w celu generowania klas](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [Eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
