---
title: Synchronizacja elementów DataSet i XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 7763e7065e74d99ee5521ea1e4f48fa0108f235a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623398"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Synchronizacja elementów DataSet i XmlDataDocument
ADO.NET <xref:System.Data.DataSet> zapewnia relacyjnych reprezentację danych. Uzyskać dostęp do danych hierarchicznych można użyć klasy XML dostępnych w programie .NET Framework. W przeszłości te dwa reprezentacje danych zostały użyte oddzielnie. Jednak .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjne i hierarchiczne reprezentacje danych za pośrednictwem **DataSet** obiektu i <xref:System.Xml.XmlDataDocument> obiektu, odpowiednio.  
  
 Gdy **DataSet** jest zsynchronizowany z **XmlDataDocument**, oba obiekty działają z jednego zestawu danych. Oznacza to, że jeśli zostanie podjęta zmiany **DataSet**, zmiana będzie odzwierciedlona we **XmlDataDocument**i na odwrót. Relacja między **DataSet** i **XmlDataDocument** tworzy dużą elastyczność, umożliwiając pojedynczej aplikacji, dostęp do całego zestawu usług oferowanych przy użyciu jednego zestawu danych, wokół **DataSet** (na przykład kontrolek Windows Forms i formularzy sieci Web i projektantów programu Visual Studio .NET), a także pakiet usług XML, w tym arkusza stylów języka XSL (Extensible), przekształcenia XSL (XSLT) i XML Path Language (XPath). Nie trzeba wybrać zestaw usług do obiektu docelowego przy użyciu aplikacji; obie są dostępne.  
  
 Istnieje kilka sposobów, które można synchronizować **DataSet** z **XmlDataDocument**. Można:  
  
- Wypełnij **zestawu danych** danych i schematu (czyli relacyjnej struktury), a następnie synchronizować je za pomocą nowego **XmlDataDocument**. Dzięki temu hierarchiczny widok istniejących danych relacyjnych. Na przykład:  
  
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
  
- Wypełnij **zestawu danych** przy użyciu samego schematu (takie jak silnie typizowaną **zestawu danych**), zsynchronizować ją z **XmlDataDocument**, a następnie załadować  **XmlDataDocument** z dokumentu XML. Dzięki temu relacyjny widok istniejące dane hierarchiczne. Nazwy tabel i nazw kolumn w swojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z. To dopasowanie jest rozróżniana wielkość liter.  
  
     Należy pamiętać, że schemat **DataSet** tylko musi być zgodna elementy XML, które chcesz udostępnić w danym widoku relacyjnych. W ten sposób może mieć bardzo dużych dokumentów XML i bardzo małych relacyjnych "okno" tego dokumentu. **XmlDataDocument** zachowuje całego dokumentu XML, nawet jeśli **DataSet** przedstawia tylko niewielką część. (Aby uzyskać szczegółowy przykład, zobacz [synchronizowanie elementu DataSet z elementem XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Poniższy przykład kodu przedstawia kroki tworzenia **DataSet** i wypełnianie jej schematu, a następnie zsynchronizować go z **XmlDataDocument**. Należy pamiętać, że **DataSet** schematu musi tylko zgodne elementy z **XmlDataDocument** , którą chcesz udostępnić, za pomocą **zestawu danych**.  
  
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
  
     Nie można załadować **XmlDataDocument** Jeśli jest zsynchronizowany z **DataSet** zawierający dane. zostanie zgłoszony wyjątek.  
  
- Utwórz nową **XmlDataDocument** i załaduj go z dokumentu XML, a następnie przejść relacyjny widok danych przy użyciu **DataSet** właściwość **XmlDataDocument**. Należy ustawić schemat **DataSet** zanim będzie można wyświetlić dane w **XmlDataDocument** przy użyciu **zestawu danych**. Ponownie, nazwy tabel i kolumn nazwy w Twojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z. To dopasowanie jest rozróżniana wielkość liter.  
  
     Poniższy przykład kodu pokazuje, jak uzyskać dostęp relacyjny widok danych w **XmlDataDocument**.  
  
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
  
 Inną zaletą synchronizowanie **XmlDataDocument** z **DataSet** jest, że zostaną zachowane wierności dokumentu XML. Jeśli **DataSet** pochodzą z dokumentu XML przy użyciu **ReadXml**, gdy dane są zapisywane jako dokument XML przy użyciu **WriteXml** go może różnić się znacznie od oryginalny dokument XML. Jest to spowodowane **DataSet** nie przechowuje formatowania, takie jak odstępy czy hierarchiczne informacje, takie jak kolejności elementów, z dokumentu XML. **DataSet** również nie zawiera elementów z dokumentu XML, które zostały zignorowane, ponieważ nie był zgodny ze schematem **zestawu danych**. Synchronizowanie **XmlDataDocument** z **DataSet** umożliwia formatowania i hierarchiczne struktury elementu oryginalnego dokumentu XML w **XmlDataDocument**, podczas gdy **DataSet** zawiera tylko danych i informacji o schemacie odpowiednie **zestawu danych**.  
  
 Podczas synchronizowania **zestawu danych** z **XmlDataDocument**, wyniki mogą się różnić w zależności od tego, czy Twoje <xref:System.Data.DataRelation> są zagnieżdżone obiekty. Aby uzyskać więcej informacji, zobacz [zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Synchronizowanie elementu DataSet z elementem XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Pokazuje synchronizowanie silnie typizowaną **zestawu danych**, z minimalnym schematu za pomocą **XmlDataDocument**.  
  
 [Wykonywanie zapytania XPath w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Pokazuje, wykonywanie zapytania XPath zawartości **zestawu danych**.  
  
 [Stosowanie transformacji XSLT do elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 Ilustruje stosowanie transformacji XSLT do zawartości **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 W tym artykule opisano sposób, w jaki **DataSet** wchodzi w interakcję z danymi XML jako źródła danych, w tym ładowanie i przechowywanie zawartości **DataSet** jako danych XML.  
  
 [Zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 W tym artykule omówiono znaczenie zagnieżdżonych **DataRelation** obiekty podczas reprezentujący zawartość **zestawu danych** jako danych XML i zawiera opis sposobu tworzenia tych relacji.  
  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 W tym artykule opisano **DataSet** i jak z niej korzystać, do zarządzania danymi aplikacji i wchodzić w interakcje ze źródeł danych, takich jak relacyjne bazy danych i XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Zawiera informacje o **XmlDataDocument** klasy.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
