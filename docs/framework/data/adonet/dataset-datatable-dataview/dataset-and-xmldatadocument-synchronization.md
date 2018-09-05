---
title: DataSet i XmlDataDocument synchronizacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 54991234d4eaa9edab218d3b0d221a6e477d2be5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530089"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="699b4-102">DataSet i XmlDataDocument synchronizacji</span><span class="sxs-lookup"><span data-stu-id="699b4-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="699b4-103">ADO.NET <xref:System.Data.DataSet> zapewnia relacyjnych reprezentację danych.</span><span class="sxs-lookup"><span data-stu-id="699b4-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="699b4-104">Uzyskać dostęp do danych hierarchicznych można użyć klasy XML dostępnych w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="699b4-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="699b4-105">W przeszłości te dwa reprezentacje danych zostały użyte oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="699b4-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="699b4-106">Jednak .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjne i hierarchiczne reprezentacje danych za pośrednictwem **DataSet** obiektu i <xref:System.Xml.XmlDataDocument> obiektu, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="699b4-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="699b4-107">Gdy **DataSet** jest zsynchronizowany z **XmlDataDocument**, oba obiekty działają z jednego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="699b4-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="699b4-108">Oznacza to, że jeśli zostanie podjęta zmiany **DataSet**, zmiana będzie odzwierciedlona we **XmlDataDocument**i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="699b4-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="699b4-109">Relacja między **DataSet** i **XmlDataDocument** tworzy dużą elastyczność, umożliwiając pojedynczej aplikacji, dostęp do całego zestawu usług oferowanych przy użyciu jednego zestawu danych, wokół **DataSet** (na przykład kontrolek Windows Forms i formularzy sieci Web i projektantów programu Visual Studio .NET), a także pakiet usług XML, w tym arkusza stylów języka XSL (Extensible), przekształcenia XSL (XSLT) i XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="699b4-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="699b4-110">Nie trzeba wybrać zestaw usług do obiektu docelowego przy użyciu aplikacji; obie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="699b4-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="699b4-111">Istnieje kilka sposobów, które można synchronizować **DataSet** z **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="699b4-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="699b4-112">Można:</span><span class="sxs-lookup"><span data-stu-id="699b4-112">You can:</span></span>  
  
-   <span data-ttu-id="699b4-113">Wypełnij **zestawu danych** danych i schematu (czyli relacyjnej struktury), a następnie synchronizować je za pomocą nowego **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="699b4-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="699b4-114">Dzięki temu hierarchiczny widok istniejących danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="699b4-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="699b4-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="699b4-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="699b4-116">Wypełnij **zestawu danych** przy użyciu samego schematu (takie jak silnie typizowaną **zestawu danych**), zsynchronizować ją z **XmlDataDocument**, a następnie załadować  **XmlDataDocument** z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="699b4-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="699b4-117">Dzięki temu relacyjny widok istniejące dane hierarchiczne.</span><span class="sxs-lookup"><span data-stu-id="699b4-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="699b4-118">Nazwy tabel i nazw kolumn w swojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z.</span><span class="sxs-lookup"><span data-stu-id="699b4-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="699b4-119">To dopasowanie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="699b4-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="699b4-120">Należy pamiętać, że schemat **DataSet** tylko musi być zgodna elementy XML, które chcesz udostępnić w danym widoku relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="699b4-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="699b4-121">W ten sposób może mieć bardzo dużych dokumentów XML i bardzo małych relacyjnych "okno" tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="699b4-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="699b4-122">**XmlDataDocument** zachowuje całego dokumentu XML, nawet jeśli **DataSet** przedstawia tylko niewielką część.</span><span class="sxs-lookup"><span data-stu-id="699b4-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="699b4-123">(Aby uzyskać szczegółowy przykład, zobacz [synchronizowanie elementu DataSet z elementem XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="699b4-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="699b4-124">Poniższy przykład kodu przedstawia kroki tworzenia **DataSet** i wypełnianie jej schematu, a następnie zsynchronizować go z **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="699b4-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="699b4-125">Należy pamiętać, że **DataSet** schematu musi tylko zgodne elementy z **XmlDataDocument** , którą chcesz udostępnić, za pomocą **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="699b4-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="699b4-126">Nie można załadować **XmlDataDocument** Jeśli jest zsynchronizowany z **DataSet** zawierający dane.</span><span class="sxs-lookup"><span data-stu-id="699b4-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="699b4-127">zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="699b4-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="699b4-128">Utwórz nową **XmlDataDocument** i załaduj go z dokumentu XML, a następnie przejść relacyjny widok danych przy użyciu **DataSet** właściwość **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="699b4-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="699b4-129">Należy ustawić schemat **DataSet** zanim będzie można wyświetlić dane w **XmlDataDocument** przy użyciu **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="699b4-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="699b4-130">Ponownie, nazwy tabel i kolumn nazwy w Twojej **DataSet** schematu musi być zgodne z nazwami elementów XML, które chcesz zsynchronizować z.</span><span class="sxs-lookup"><span data-stu-id="699b4-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="699b4-131">To dopasowanie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="699b4-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="699b4-132">Poniższy przykład kodu pokazuje, jak uzyskać dostęp relacyjny widok danych w **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="699b4-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="699b4-133">Inną zaletą synchronizowanie **XmlDataDocument** z **DataSet** jest, że zostaną zachowane wierności dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="699b4-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="699b4-134">Jeśli **DataSet** pochodzą z dokumentu XML przy użyciu **ReadXml**, gdy dane są zapisywane jako dokument XML przy użyciu **WriteXml** go może różnić się znacznie od oryginalny dokument XML.</span><span class="sxs-lookup"><span data-stu-id="699b4-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="699b4-135">Jest to spowodowane **DataSet** nie przechowuje formatowania, takie jak odstępy czy hierarchiczne informacje, takie jak kolejności elementów, z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="699b4-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="699b4-136">**DataSet** również nie zawiera elementów z dokumentu XML, które zostały zignorowane, ponieważ nie był zgodny ze schematem **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="699b4-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="699b4-137">Synchronizowanie **XmlDataDocument** z **DataSet** umożliwia formatowania i hierarchiczne struktury elementu oryginalnego dokumentu XML w **XmlDataDocument**, podczas gdy **DataSet** zawiera tylko danych i informacji o schemacie odpowiednie **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="699b4-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="699b4-138">Podczas synchronizowania **zestawu danych** z **XmlDataDocument**, wyniki mogą się różnić w zależności od tego, czy Twoje <xref:System.Data.DataRelation> są zagnieżdżone obiekty.</span><span class="sxs-lookup"><span data-stu-id="699b4-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="699b4-139">Aby uzyskać więcej informacji, zobacz [zagnieżdżanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="699b4-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="699b4-140">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="699b4-140">In This Section</span></span>  
 [<span data-ttu-id="699b4-141">Synchronizowanie elementu DataSet z elementem XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="699b4-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="699b4-142">Pokazuje synchronizowanie silnie typizowaną **zestawu danych**, z minimalnym schematu za pomocą **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="699b4-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="699b4-143">Wykonywanie zapytania XPath w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="699b4-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="699b4-144">Pokazuje, wykonywanie zapytania XPath zawartości **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="699b4-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="699b4-145">Stosowanie transformacji XSLT do elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="699b4-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="699b4-146">Ilustruje stosowanie transformacji XSLT do zawartości **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="699b4-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="699b4-147">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="699b4-147">Related Sections</span></span>  
 [<span data-ttu-id="699b4-148">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="699b4-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="699b4-149">W tym artykule opisano sposób, w jaki **DataSet** wchodzi w interakcję z danymi XML jako źródła danych, w tym ładowanie i przechowywanie zawartości **DataSet** jako danych XML.</span><span class="sxs-lookup"><span data-stu-id="699b4-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="699b4-150">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="699b4-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="699b4-151">W tym artykule omówiono znaczenie zagnieżdżonych **DataRelation** obiekty podczas reprezentujący zawartość **zestawu danych** jako danych XML i zawiera opis sposobu tworzenia tych relacji.</span><span class="sxs-lookup"><span data-stu-id="699b4-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="699b4-152">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="699b4-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="699b4-153">W tym artykule opisano **DataSet** i jak z niej korzystać, do zarządzania danymi aplikacji i wchodzić w interakcje ze źródeł danych, takich jak relacyjne bazy danych i XML.</span><span class="sxs-lookup"><span data-stu-id="699b4-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="699b4-154">Zawiera informacje o **XmlDataDocument** klasy.</span><span class="sxs-lookup"><span data-stu-id="699b4-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699b4-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="699b4-155">See Also</span></span>  
 [<span data-ttu-id="699b4-156">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="699b4-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
