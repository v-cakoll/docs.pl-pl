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
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="85e8a-102">Zestaw danych i dokumentu XmlDataDocument synchronizacji</span><span class="sxs-lookup"><span data-stu-id="85e8a-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="85e8a-103">ADO.NET <xref:System.Data.DataSet> zapewnia relacyjne reprezentację danych.</span><span class="sxs-lookup"><span data-stu-id="85e8a-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="85e8a-104">Danymi hierarchicznymi dostępu można użyć klasy XML dostępne w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85e8a-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="85e8a-105">W przeszłości te dwie reprezentacje dane zostały już użyte oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="85e8a-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="85e8a-106">Jednak programu .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjnych i hierarchicznych reprezentacje danych za pośrednictwem **DataSet** obiektu i <xref:System.Xml.XmlDataDocument> obiekt odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="85e8a-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="85e8a-107">Gdy **DataSet** jest zsynchronizowany z **dokumentu XmlDataDocument**, oba obiekty pracuje z jednego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="85e8a-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="85e8a-108">Oznacza to, że jeśli zostaną zmienione jej **DataSet**, zmiany zostaną odzwierciedlone w **dokumentu XmlDataDocument**i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="85e8a-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="85e8a-109">Relacja między **DataSet** i **dokumentu XmlDataDocument** tworzy elastyczność zezwalając pojedynczej aplikacji, za pomocą jednego zestawu danych, aby uzyskać dostęp do całego pakietu usług utworzona wokół **DataSet** (na przykład formantów formularzy systemu Windows i formularzy sieci Web i projektantów programu Visual Studio .NET), a także do pakietu usług XML w tym rozszerzonego arkusza stylów XSL (Language), transformacji XSL (XSLT) i XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="85e8a-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="85e8a-110">Nie trzeba wybrać zestaw usług do docelowej aplikacji; dostępne są obie.</span><span class="sxs-lookup"><span data-stu-id="85e8a-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="85e8a-111">Istnieje kilka metod, które można synchronizować **DataSet** z **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="85e8a-112">Można:</span><span class="sxs-lookup"><span data-stu-id="85e8a-112">You can:</span></span>  
  
-   <span data-ttu-id="85e8a-113">Wypełnij **DataSet** schematu (to znaczy relacyjne struktury) i danych, a następnie zsynchronizować je z nowej **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="85e8a-114">Zapewnia to hierarchiczny widok istniejących danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="85e8a-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="85e8a-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="85e8a-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="85e8a-116">Wypełnij **zestawu danych** ze schematem tylko (takich jak silnie typizowaną **zestawu danych**), zsynchronizować je z **dokumentu XmlDataDocument**, a następnie załadować  **Dokumentu XmlDataDocument** z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="85e8a-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="85e8a-117">Zapewnia to relacyjny widok istniejących danych hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="85e8a-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="85e8a-118">Nazwy tabel i nazw kolumn w Twojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z.</span><span class="sxs-lookup"><span data-stu-id="85e8a-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="85e8a-119">To dopasowanie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="85e8a-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="85e8a-120">Należy pamiętać, że schemat **DataSet** tylko musi być zgodna elementów XML, które chcesz udostępnić w widoku relacyjne.</span><span class="sxs-lookup"><span data-stu-id="85e8a-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="85e8a-121">W ten sposób może mieć bardzo dużych dokumentu XML i bardzo małych relacyjne "okna" w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="85e8a-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="85e8a-122">**Dokumentu XmlDataDocument** zachowuje całego dokumentu XML, nawet jeśli **DataSet** przedstawia tylko niewielką część.</span><span class="sxs-lookup"><span data-stu-id="85e8a-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="85e8a-123">(Aby uzyskać szczegółowy przykład tego, zobacz [synchronizowanie zestawu danych z dokumentu XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="85e8a-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="85e8a-124">Poniższy przykładowy kod przedstawia kroki tworzenia **DataSet** i wypełnianie jej schematu, a następnie zsynchronizować go z **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="85e8a-125">Należy pamiętać, że **DataSet** schematu tylko musi być zgodna z elementów **dokumentu XmlDataDocument** , który ma zostać udostępniona za pomocą **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="85e8a-126">Nie można załadować **dokumentu XmlDataDocument** Jeśli jest zsynchronizowany z **DataSet** zawierający dane.</span><span class="sxs-lookup"><span data-stu-id="85e8a-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="85e8a-127">Zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="85e8a-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="85e8a-128">Utwórz nową **dokumentu XmlDataDocument** i załaduj go z dokumentu XML, a następnie przejść relacyjny widok danych przy użyciu **DataSet** właściwość **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="85e8a-129">Należy ustawić schemat **DataSet** zanim będzie można wyświetlić dane w **dokumentu XmlDataDocument** przy użyciu **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="85e8a-130">Ponownie, nazwy nazwy tabel i kolumn w Twojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z.</span><span class="sxs-lookup"><span data-stu-id="85e8a-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="85e8a-131">To dopasowanie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="85e8a-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="85e8a-132">Poniższy przykładowy kod przedstawia sposób dostępu relacyjny widok danych w **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="85e8a-133">Inną zaletą synchronizowanie **dokumentu XmlDataDocument** z **DataSet** jest zachowywanie wierności dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="85e8a-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="85e8a-134">Jeśli **DataSet** pochodzą z dokumentu XML przy użyciu **ReadXml**, gdy dane są zapisywane jako dokument XML przy użyciu **WriteXml** go może różnić się znacząco od oryginalny dokument XML.</span><span class="sxs-lookup"><span data-stu-id="85e8a-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="85e8a-135">Jest to spowodowane **DataSet** nie przechowuje formatowania, takich jak biały znak lub hierarchiczna informacje, takie jak kolejności elementów z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="85e8a-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="85e8a-136">**DataSet** również nie zawiera elementów z dokumentu XML, które zostały zignorowane, ponieważ nie był zgodny ze schematem **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="85e8a-137">Synchronizowanie **dokumentu XmlDataDocument** z **DataSet** umożliwia strukturze elementu formatowania i hierarchicznego oryginalnego dokumentu XML w **dokumentu XmlDataDocument**, podczas gdy **DataSet** zawiera tylko informacje danych i schematu należy **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="85e8a-138">Podczas synchronizowania **DataSet** z **dokumentu XmlDataDocument**, wyniki mogą się różnić w zależności od tego, czy Twoje <xref:System.Data.DataRelation> obiekty są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="85e8a-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="85e8a-139">Aby uzyskać więcej informacji, zobacz [zagnieżdżania DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="85e8a-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85e8a-140">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="85e8a-140">In This Section</span></span>  
 [<span data-ttu-id="85e8a-141">Synchronizowanie zestawu danych z dokumentu XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="85e8a-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="85e8a-142">Pokazuje synchronizowanie silnie typizowaną **DataSet**, z minimalnym schematu z **dokumentu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="85e8a-143">Wykonywanie kwerendy XPath w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="85e8a-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="85e8a-144">Pokazuje wykonywanie kwerendy XPath na zawartość **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="85e8a-145">Stosowanie przekształcenia XSLT do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="85e8a-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="85e8a-146">Pokazuje, zastosowanie transformacji XSLT do zawartości **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="85e8a-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="85e8a-147">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="85e8a-147">Related Sections</span></span>  
 [<span data-ttu-id="85e8a-148">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="85e8a-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="85e8a-149">Opisuje sposób **DataSet** współdziała z językiem XML jako źródło danych, w tym ładowanie i przechowywanie zawartości **zestawu danych** danych XML.</span><span class="sxs-lookup"><span data-stu-id="85e8a-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="85e8a-150">DataRelations zagnieżdżenia</span><span class="sxs-lookup"><span data-stu-id="85e8a-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="85e8a-151">W tym artykule omówiono znaczenie zagnieżdżonych **DataRelation** obiektów po reprezentujący zawartość **zestawu danych** danych XML i zawiera opis sposobu tworzenia tych relacji.</span><span class="sxs-lookup"><span data-stu-id="85e8a-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="85e8a-152">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="85e8a-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="85e8a-153">W tym artykule opisano **DataSet** i jak z niego korzystać, aby zarządzać dane aplikacji i wchodzić w interakcje z źródeł danych, takich jak relacyjnych baz danych i XML.</span><span class="sxs-lookup"><span data-stu-id="85e8a-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="85e8a-154">Zawiera informacje o **dokumentu XmlDataDocument** klasy.</span><span class="sxs-lookup"><span data-stu-id="85e8a-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e8a-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85e8a-155">See Also</span></span>  
 [<span data-ttu-id="85e8a-156">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="85e8a-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
