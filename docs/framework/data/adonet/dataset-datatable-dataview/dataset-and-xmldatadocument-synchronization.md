---
title: Synchronizacja elementów DataSet i XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: e76e81153cb7d074fe975744c6b6041ee04be90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785428"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Synchronizacja elementów DataSet i XmlDataDocument
ADO.NET <xref:System.Data.DataSet> zapewnia relacyjną reprezentację danych. W przypadku dostępu do danych hierarchicznych można użyć klas XML dostępnych w .NET Framework. W przeszłości te dwie reprezentacje danych zostały użyte osobno. Jednak .NET Framework umożliwia dostęp synchroniczny w czasie rzeczywistym zarówno do relacyjnych, jak i hierarchicznych reprezentacji danych za pomocą obiektu **DataSet** i <xref:System.Xml.XmlDataDocument> obiektu.  
  
 Gdy **zestaw danych** jest synchronizowany z **XmlDataDocument**, oba obiekty pracują z pojedynczym zestawem danych. Oznacza to, że jeśli w **zestawie danych**zostanie wprowadzona zmiana, zmiana zostanie odzwierciedlona w **XmlDataDocument**i na odwrót. Relacja między **zestawem danych** a **XmlDataDocumentą** tworzy doskonałą elastyczność dzięki umożliwieniu pojedynczej aplikacji, korzystającej z pojedynczego zestawu danych, w celu uzyskania dostępu do całego zestawu usług utworzonych wokół **zestawu danych** (na przykład formularzy sieci Web i Formanty Windows Forms i Visual Studio .NET Designer), a także pakiet usług XML, w tym Extensible Stylesheet Language (XSL), przekształcenia XSL (XSLT) i XML Path Language (XPath). Nie trzeba wybierać zestawu usług przeznaczonych dla aplikacji; Oba te elementy są dostępne.  
  
 Istnieje kilka sposobów synchronizacji **zestawu danych** z **XmlDataDocument**. Można:  
  
- Wypełnij **zestaw danych** schematem (czyli strukturą relacyjną) i danymi, a następnie zsynchronizuj go z nowym **XmlDataDocument**. Zapewnia to hierarchiczny widok istniejących danych relacyjnych. Na przykład:  
  
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
  
- Wypełnij **zestaw danych** tylko schematem (na przykład **zestaw danych**o jednoznacznie określonym typie), zsynchronizuj go z **XmlDataDocument**, a następnie załaduj **XmlDataDocument** z dokumentu XML. Zapewnia to relacyjny widok istniejących danych hierarchicznych. Nazwy tabel i kolumn w schemacie **DataSet** muszą być zgodne z nazwami elementów XML, z którymi mają być synchronizowane. W tym dopasowaniu uwzględniana jest wielkość liter.  
  
     Należy zauważyć, że schemat **zestawu danych** musi być zgodny z elementami XML, które mają zostać ujawnione w widoku relacyjnym. W ten sposób można mieć bardzo duży dokument XML i bardzo małe relacyjne "okno" w tym dokumencie. **XmlDataDocument** zachowuje cały dokument XML, mimo że **zestaw danych** ujawnia tylko niewielką część tego dokumentu. (Aby zapoznać się z szczegółowym przykładem, zobacz [synchronizowanie zestawu danych z XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md)).  
  
     Poniższy przykład kodu przedstawia kroki tworzenia **zestawu danych** i wypełniania jego schematu, a następnie synchronizowanie go z **XmlDataDocument**. Należy zauważyć, że schemat **zestawu danych** musi pasować do elementów z **XmlDataDocument** , które chcesz uwidocznić przy użyciu **zestawu danych**.  
  
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
  
     Nie można załadować elementu **XmlDataDocument** , jeśli jest on synchronizowany z **zestawem** danych zawierającym dane. Zostanie zgłoszony wyjątek.  
  
- Utwórz nową **XmlDataDocument** i Załaduj ją z dokumentu XML, a następnie uzyskaj dostęp do widoku relacyjnego danych przy użyciu właściwości **DataSet** obiektu **XmlDataDocument**. Należy ustawić schemat **zestawu danych** , zanim będzie można wyświetlić dowolne dane w **XmlDataDocument** za pomocą **zestawu danych**. Ponownie nazwy tabel i kolumn w schemacie **DataSet** muszą być zgodne z nazwami elementów XML, z którymi mają być synchronizowane. W tym dopasowaniu uwzględniana jest wielkość liter.  
  
     Poniższy przykład kodu pokazuje, jak uzyskać dostęp do widoku relacyjnego danych w **XmlDataDocument**.  
  
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
  
 Inną zaletą synchronizowania **XmlDataDocument** z **zestawem danych** jest zachowywanie wierności dokumentu XML. Jeśli **zestaw danych** jest wypełniany z dokumentu XML przy użyciu **ReadXml**, gdy dane są zapisywane z powrotem jako dokument XML przy użyciu **WriteXml** , może się różnić od oryginalnego dokumentu XML. Jest to spowodowane tym, że **zestaw danych** nie zachowuje formatowania, takiego jak odstępy, lub informacji hierarchicznych, takich jak kolejność elementów, z dokumentu XML. **Zestaw danych** nie zawiera również elementów z dokumentu XML, który został zignorowany, ponieważ nie pasowały do schematu **zestawu danych**. Synchronizacja elementu **XmlDataDocument** z **zestawem danych** umożliwia przechowywanie formatowania i hierarchicznej struktury elementu oryginalnego dokumentu XML w **XmlDataDocument**, podczas gdy **zestaw danych** zawiera tylko dane i Informacje o schemacie odpowiednie dla **zestawu danych**.  
  
 W przypadku synchronizacji **zestawu danych** z **XmlDataDocument**wyniki mogą się różnić w zależności od tego, czy <xref:System.Data.DataRelation> obiekty są zagnieżdżone. Aby uzyskać więcej informacji, zobacz [zagnieżdżanie relacji](nesting-datarelations.md)danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Synchronizowanie elementu DataSet z elementem XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Demonstruje synchronizację **zestawu danych**o jednoznacznie określonym typie, z minimalnym schematem, z **XmlDataDocument**.  
  
 [Wykonywanie zapytania XPath w elemencie DataSet](performing-an-xpath-query-on-a-dataset.md)  
 Pokazuje wykonywanie zapytania XPath dla zawartości **zestawu danych**.  
  
 [Stosowanie transformacji XSLT do elementu DataSet](applying-an-xslt-transform-to-a-dataset.md)  
 Pokazuje, jak zastosować transformację XSLT do zawartości **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)  
 Opisuje, jak **zestaw** danych WSPÓŁDZIAŁA z XML jako źródło danych, w tym ładowanie i utrwalanie zawartości **zestawu** danych jako danych XML.  
  
 [Zagnieżdżanie elementów DataRelation](nesting-datarelations.md)  
 Omawia **znaczenie zagnieżdżonych** obiektów podczas reprezentowania zawartości **zestawu** danych jako danych XML i opisuje sposób tworzenia tych relacji.  
  
 [Elementy DataSet, DataTable i DataView](index.md)  
 Opisuje **zestaw danych** i sposób korzystania z niego do zarządzania danymi aplikacji oraz do współdziałania ze źródłami danych, w tym relacyjnych baz danych i XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Zawiera informacje referencyjne dotyczące klasy **XmlDataDocument** .  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../ado-net-overview.md)
