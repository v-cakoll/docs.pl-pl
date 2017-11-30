---
title: Zestaw danych i dokumentu XmlDataDocument synchronizacji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923a6b6cf1523c8a11cb509679443b9658e07ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Zestaw danych i dokumentu XmlDataDocument synchronizacji
ADO.NET <xref:System.Data.DataSet> zapewnia relacyjne reprezentację danych. Danymi hierarchicznymi dostępu można użyć klasy XML dostępne w programie .NET Framework. W przeszłości te dwie reprezentacje dane zostały już użyte oddzielnie. Jednak programu .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjnych i hierarchicznych reprezentacje danych za pośrednictwem **DataSet** obiektu i <xref:System.Xml.XmlDataDocument> obiekt odpowiednio.  
  
 Gdy **DataSet** jest zsynchronizowany z **dokumentu XmlDataDocument**, oba obiekty pracuje z jednego zestawu danych. Oznacza to, że jeśli zostaną zmienione jej **DataSet**, zmiany zostaną odzwierciedlone w **dokumentu XmlDataDocument**i na odwrót. Relacja między **DataSet** i **dokumentu XmlDataDocument** tworzy elastyczność zezwalając pojedynczej aplikacji, za pomocą jednego zestawu danych, aby uzyskać dostęp do całego pakietu usług utworzona wokół **DataSet** (na przykład formantów formularzy systemu Windows i formularzy sieci Web i projektantów programu Visual Studio .NET), a także do pakietu usług XML w tym rozszerzonego arkusza stylów XSL (Language), transformacji XSL (XSLT) i XML Path Language (XPath). Nie trzeba wybrać zestaw usług do docelowej aplikacji; dostępne są obie.  
  
 Istnieje kilka metod, które można synchronizować **DataSet** z **dokumentu XmlDataDocument**. Można:  
  
-   Wypełnij **DataSet** schematu (to znaczy relacyjne struktury) i danych, a następnie zsynchronizować je z nowej **dokumentu XmlDataDocument**. Zapewnia to hierarchiczny widok istniejących danych relacyjnych. Na przykład:  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   Wypełnij **zestawu danych** ze schematem tylko (takich jak silnie typizowaną **zestawu danych**), zsynchronizować je z **dokumentu XmlDataDocument**, a następnie załadować  **Dokumentu XmlDataDocument** z dokumentu XML. Zapewnia to relacyjny widok istniejących danych hierarchicznej. Nazwy tabel i nazw kolumn w Twojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z. To dopasowanie jest rozróżniana wielkość liter.  
  
     Należy pamiętać, że schemat **DataSet** tylko musi być zgodna elementów XML, które chcesz udostępnić w widoku relacyjne. W ten sposób może mieć bardzo dużych dokumentu XML i bardzo małych relacyjne "okna" w tym dokumencie. **Dokumentu XmlDataDocument** zachowuje całego dokumentu XML, nawet jeśli **DataSet** przedstawia tylko niewielką część. (Aby uzyskać szczegółowy przykład tego, zobacz [synchronizowanie zestawu danych z dokumentu XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Poniższy przykładowy kod przedstawia kroki tworzenia **DataSet** i wypełnianie jej schematu, a następnie zsynchronizować go z **dokumentu XmlDataDocument**. Należy pamiętać, że **DataSet** schematu tylko musi być zgodna z elementów **dokumentu XmlDataDocument** , który ma zostać udostępniona za pomocą **zestawu danych**.  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     Nie można załadować **dokumentu XmlDataDocument** Jeśli jest zsynchronizowany z **DataSet** zawierający dane. Zostanie wygenerowany wyjątek.  
  
-   Utwórz nową **dokumentu XmlDataDocument** i załaduj go z dokumentu XML, a następnie przejść relacyjny widok danych przy użyciu **DataSet** właściwość **dokumentu XmlDataDocument**. Należy ustawić schemat **DataSet** zanim będzie można wyświetlić dane w **dokumentu XmlDataDocument** przy użyciu **zestawu danych**. Ponownie, nazwy nazwy tabel i kolumn w Twojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z. To dopasowanie jest rozróżniana wielkość liter.  
  
     Poniższy przykładowy kod przedstawia sposób dostępu relacyjny widok danych w **dokumentu XmlDataDocument**.  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 Inną zaletą synchronizowanie **dokumentu XmlDataDocument** z **DataSet** jest zachowywanie wierności dokumentu XML. Jeśli **DataSet** pochodzą z dokumentu XML przy użyciu **ReadXml**, gdy dane są zapisywane jako dokument XML przy użyciu **WriteXml** go może różnić się znacząco od oryginalny dokument XML. Jest to spowodowane **DataSet** nie przechowuje formatowania, takich jak biały znak lub hierarchiczna informacje, takie jak kolejności elementów z dokumentu XML. **DataSet** również nie zawiera elementów z dokumentu XML, które zostały zignorowane, ponieważ nie był zgodny ze schematem **zestawu danych**. Synchronizowanie **dokumentu XmlDataDocument** z **DataSet** umożliwia strukturze elementu formatowania i hierarchicznego oryginalnego dokumentu XML w **dokumentu XmlDataDocument**, podczas gdy **DataSet** zawiera tylko informacje danych i schematu należy **zestawu danych**.  
  
 Podczas synchronizowania **DataSet** z **dokumentu XmlDataDocument**, wyniki mogą się różnić w zależności od tego, czy Twoje <xref:System.Data.DataRelation> obiekty są zagnieżdżone. Aby uzyskać więcej informacji, zobacz [zagnieżdżania DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Synchronizowanie zestawu danych z dokumentu XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Pokazuje synchronizowanie silnie typizowaną **DataSet**, z minimalnym schematu z **dokumentu XmlDataDocument**.  
  
 [Wykonywanie kwerendy XPath w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Pokazuje wykonywanie kwerendy XPath na zawartość **zestawu danych**.  
  
 [Stosowanie przekształcenia XSLT do zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Pokazuje, zastosowanie transformacji XSLT do zawartości **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Za pomocą języka XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Opisuje sposób **DataSet** współdziała z językiem XML jako źródło danych, w tym ładowanie i przechowywanie zawartości **zestawu danych** danych XML.  
  
 [DataRelations zagnieżdżenia](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 W tym artykule omówiono znaczenie zagnieżdżonych **DataRelation** obiektów po reprezentujący zawartość **zestawu danych** danych XML i zawiera opis sposobu tworzenia tych relacji.  
  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 W tym artykule opisano **DataSet** i jak z niego korzystać, aby zarządzać dane aplikacji i wchodzić w interakcje z źródeł danych, takich jak relacyjnych baz danych i XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Zawiera informacje o **dokumentu XmlDataDocument** klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
