---
title: Synchronizacja elementów DataSet i XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 3bbe28423385cae0f09f301c03b2b1a59edf101d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205072"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="a122b-102">Synchronizacja elementów DataSet i XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="a122b-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="a122b-103">ADO.NET <xref:System.Data.DataSet> zapewnia relacyjną reprezentację danych.</span><span class="sxs-lookup"><span data-stu-id="a122b-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="a122b-104">W przypadku dostępu do danych hierarchicznych można użyć klas XML dostępnych w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a122b-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="a122b-105">W przeszłości te dwie reprezentacje danych zostały użyte osobno.</span><span class="sxs-lookup"><span data-stu-id="a122b-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="a122b-106">Jednak .NET Framework umożliwia dostęp synchroniczny w czasie rzeczywistym zarówno do relacyjnych, jak i hierarchicznych reprezentacji danych za pomocą obiektu **DataSet** i <xref:System.Xml.XmlDataDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a122b-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="a122b-107">Gdy **zestaw danych** jest synchronizowany z **XmlDataDocument**, oba obiekty pracują z pojedynczym zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="a122b-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="a122b-108">Oznacza to, że jeśli w **zestawie danych**zostanie wprowadzona zmiana, zmiana zostanie odzwierciedlona w **XmlDataDocument**i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="a122b-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="a122b-109">Relacja między **zestawem danych** a **XmlDataDocumentą** tworzy doskonałą elastyczność dzięki umożliwieniu pojedynczej aplikacji, korzystającej z pojedynczego zestawu danych, w celu uzyskania dostępu do całego zestawu usług utworzonych wokół **zestawu danych** (na przykład formularzy sieci Web i Formanty Windows Forms i Visual Studio .NET Designer), a także pakiet usług XML, w tym Extensible Stylesheet Language (XSL), przekształcenia XSL (XSLT) i XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="a122b-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="a122b-110">Nie trzeba wybierać zestawu usług przeznaczonych dla aplikacji; Oba te elementy są dostępne.</span><span class="sxs-lookup"><span data-stu-id="a122b-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="a122b-111">Istnieje kilka sposobów synchronizacji **zestawu danych** z **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="a122b-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="a122b-112">Można:</span><span class="sxs-lookup"><span data-stu-id="a122b-112">You can:</span></span>  
  
- <span data-ttu-id="a122b-113">Wypełnij **zestaw danych** schematem (czyli strukturą relacyjną) i danymi, a następnie zsynchronizuj go z nowym **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="a122b-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="a122b-114">Zapewnia to hierarchiczny widok istniejących danych relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a122b-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="a122b-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a122b-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="a122b-116">Wypełnij **zestaw danych** tylko schematem (na przykład **zestaw danych**o jednoznacznie określonym typie), zsynchronizuj go z **XmlDataDocument**, a następnie załaduj **XmlDataDocument** z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a122b-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="a122b-117">Zapewnia to relacyjny widok istniejących danych hierarchicznych.</span><span class="sxs-lookup"><span data-stu-id="a122b-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="a122b-118">Nazwy tabel i kolumn w schemacie **DataSet** muszą być zgodne z nazwami elementów XML, z którymi mają być synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="a122b-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="a122b-119">W tym dopasowaniu uwzględniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a122b-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="a122b-120">Należy zauważyć, że schemat **zestawu danych** musi być zgodny z elementami XML, które mają zostać ujawnione w widoku relacyjnym.</span><span class="sxs-lookup"><span data-stu-id="a122b-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="a122b-121">W ten sposób można mieć bardzo duży dokument XML i bardzo małe relacyjne "okno" w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a122b-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="a122b-122">**XmlDataDocument** zachowuje cały dokument XML, mimo że **zestaw danych** ujawnia tylko niewielką część tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a122b-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="a122b-123">(Aby zapoznać się z szczegółowym przykładem, zobacz [synchronizowanie zestawu danych z XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md)).</span><span class="sxs-lookup"><span data-stu-id="a122b-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="a122b-124">Poniższy przykład kodu przedstawia kroki tworzenia **zestawu danych** i wypełniania jego schematu, a następnie synchronizowanie go z **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="a122b-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="a122b-125">Należy zauważyć, że schemat **zestawu danych** musi pasować do elementów z **XmlDataDocument** , które chcesz uwidocznić przy użyciu **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a122b-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="a122b-126">Nie można załadować elementu **XmlDataDocument** , jeśli jest on synchronizowany z **zestawem** danych zawierającym dane.</span><span class="sxs-lookup"><span data-stu-id="a122b-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="a122b-127">Zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a122b-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="a122b-128">Utwórz nową **XmlDataDocument** i Załaduj ją z dokumentu XML, a następnie uzyskaj dostęp do widoku relacyjnego danych przy użyciu właściwości **DataSet** obiektu **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="a122b-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="a122b-129">Należy ustawić schemat **zestawu danych** , zanim będzie można wyświetlić dowolne dane w **XmlDataDocument** za pomocą **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a122b-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="a122b-130">Ponownie nazwy tabel i kolumn w schemacie **DataSet** muszą być zgodne z nazwami elementów XML, z którymi mają być synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="a122b-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="a122b-131">W tym dopasowaniu uwzględniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a122b-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="a122b-132">Poniższy przykład kodu pokazuje, jak uzyskać dostęp do widoku relacyjnego danych w **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="a122b-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="a122b-133">Inną zaletą synchronizowania **XmlDataDocument** z zestawem **danych** jest zachowywanie wierności dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a122b-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="a122b-134">Jeśli **zestaw danych** jest wypełniany z dokumentu XML przy użyciu **ReadXml**, gdy dane są zapisywane z powrotem jako dokument XML przy użyciu **WriteXml** , może się różnić od oryginalnego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a122b-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="a122b-135">Jest to spowodowane tym, że **zestaw danych** nie zachowuje formatowania, takiego jak odstępy, lub informacji hierarchicznych, takich jak kolejność elementów, z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a122b-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="a122b-136">**Zestaw danych** nie zawiera również elementów z dokumentu XML, który został zignorowany, ponieważ nie pasowały do schematu **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a122b-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="a122b-137">Synchronizacja elementu **XmlDataDocument** z zestawem **danych** umożliwia przechowywanie formatowania i hierarchicznej struktury elementu oryginalnego dokumentu XML w **XmlDataDocument**, podczas gdy **zestaw danych** zawiera tylko dane i Informacje o schemacie odpowiednie dla **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a122b-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="a122b-138">W przypadku synchronizacji **zestawu danych** z **XmlDataDocument**wyniki mogą się różnić w zależności od tego, czy <xref:System.Data.DataRelation> obiekty są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="a122b-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="a122b-139">Aby uzyskać więcej informacji, zobacz [zagnieżdżanie relacji](nesting-datarelations.md)danych.</span><span class="sxs-lookup"><span data-stu-id="a122b-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a122b-140">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a122b-140">In This Section</span></span>  
 [<span data-ttu-id="a122b-141">Synchronizowanie elementu DataSet z elementem XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="a122b-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="a122b-142">Demonstruje synchronizację **zestawu danych**o jednoznacznie określonym typie, z minimalnym schematem, z **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="a122b-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="a122b-143">Wykonywanie zapytania XPath w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="a122b-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="a122b-144">Pokazuje wykonywanie zapytania XPath dla zawartości **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a122b-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="a122b-145">Stosowanie transformacji XSLT do elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a122b-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="a122b-146">Pokazuje, jak zastosować transformację XSLT do zawartości **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a122b-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a122b-147">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a122b-147">Related Sections</span></span>  
 [<span data-ttu-id="a122b-148">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="a122b-148">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="a122b-149">Opisuje, jak **zestaw** danych WSPÓŁDZIAŁA z XML jako źródło danych, w tym ładowanie i utrwalanie zawartości **zestawu** danych jako danych XML.</span><span class="sxs-lookup"><span data-stu-id="a122b-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="a122b-150">Zagnieżdżanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="a122b-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="a122b-151">Omawia znaczenie zagnieżdżonych obiektów podczas reprezentowania zawartości **zestawu** danych jako danych XML i opisuje sposób tworzenia tych relacji.</span><span class="sxs-lookup"><span data-stu-id="a122b-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="a122b-152">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="a122b-152">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="a122b-153">Opisuje **zestaw danych** i sposób korzystania z niego do zarządzania danymi aplikacji oraz do współdziałania ze źródłami danych, w tym relacyjnych baz danych i XML.</span><span class="sxs-lookup"><span data-stu-id="a122b-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="a122b-154">Zawiera informacje referencyjne dotyczące klasy **XmlDataDocument** .</span><span class="sxs-lookup"><span data-stu-id="a122b-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a122b-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a122b-155">See also</span></span>

- [<span data-ttu-id="a122b-156">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a122b-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
