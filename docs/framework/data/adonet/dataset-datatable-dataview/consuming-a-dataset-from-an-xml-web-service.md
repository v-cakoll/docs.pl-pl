---
title: Korzystanie z zestawu danych z usługi sieci Web XML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 9bfcd4d8dca38c9438c072c143cf7ba0eafd6ecf
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="7d471-102">Korzystanie z zestawu danych z usługi sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="7d471-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="7d471-103"><xref:System.Data.DataSet> Została zaprojektowana z projektem bez połączenia, w części w celu ułatwienia wygodny transportu danych za pośrednictwem Internetu.</span><span class="sxs-lookup"><span data-stu-id="7d471-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="7d471-104">**DataSet** jest "serializacji" można określić jako dane wejściowe lub dane wyjściowe z usług XML sieci Web bez dodatkowy kod wymagany do strumienia zawartości **DataSet** z usługi XML sieci Web do klienta i z powrotem.</span><span class="sxs-lookup"><span data-stu-id="7d471-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="7d471-105">**DataSet** jest niejawnie przekonwertować na strumień XML przy użyciu formatu elementu DiffGram wysyłane za pośrednictwem sieci i następnie odtworzyć strumienia XML jako **DataSet** po stronie odbiorczej.</span><span class="sxs-lookup"><span data-stu-id="7d471-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="7d471-106">Zapewnia to bardzo prosty i elastyczny — metoda przekazywania i zwracający dane relacyjne przy użyciu usług XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="7d471-107">Aby uzyskać więcej informacji na temat formatu elementu DiffGram, zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="7d471-107">For more information about the DiffGram format, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>  
  
 <span data-ttu-id="7d471-108">Poniższy przykład przedstawia sposób tworzenia usługi XML sieci Web i klienta, który używał **DataSet** do przesyłania danych relacyjnych (włącznie z danymi zmodyfikowanego) i rozwiązać wszelkie aktualizacje z powrotem do oryginalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7d471-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d471-109">Firma Microsoft zaleca zawsze rozważ wpływ na bezpieczeństwo podczas tworzenia usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="7d471-110">Aby uzyskać informacje na temat zabezpieczenia usługi XML sieci Web, zobacz [zabezpieczanie XML sieci Web usług utworzone za pomocą programu ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span><span class="sxs-lookup"><span data-stu-id="7d471-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="7d471-111">Aby utworzyć usługi XML sieci Web, która zwraca i korzysta z zestawu danych</span><span class="sxs-lookup"><span data-stu-id="7d471-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1.  <span data-ttu-id="7d471-112">Tworzenie usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="7d471-113">W tym przykładzie usługi XML sieci Web utworzono, która zwraca dane, w tym przypadku listę klientów z **Northwind** bazy danych i odbiera **DataSet** z aktualizacjami danych, które usługi XML sieci Web rozpoznaje wstecz do oryginalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7d471-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="7d471-114">Usługa XML sieci Web udostępnia dwie metody: **GetCustomers**, aby zwrócić listę klientów, a **UpdateCustomers**, aby rozpoznać aktualizacji źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7d471-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="7d471-115">Usługa XML sieci Web są przechowywane w pliku na serwerze sieci Web o nazwie DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="7d471-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="7d471-116">Poniższy kod przedstawia zawartość DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="7d471-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     <span data-ttu-id="7d471-117">W typowym scenariuszu **UpdateCustomers** metody powinny być zapisane catch naruszeń optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="7d471-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="7d471-118">Dla uproszczenia przykładzie nie obejmuje to.</span><span class="sxs-lookup"><span data-stu-id="7d471-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="7d471-119">Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [optymistycznej współbieżności](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="7d471-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).</span></span>  
  
2.  <span data-ttu-id="7d471-120">Utwórz serwer proxy usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="7d471-121">Klienci usługi XML sieci Web wymagają serwera proxy protokołu SOAP aby można było korzystać z metod uwidocznione.</span><span class="sxs-lookup"><span data-stu-id="7d471-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="7d471-122">Może mieć Visual Studio Generowanie ten serwer proxy dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="7d471-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="7d471-123">Ustawiając odwołanie sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie działania opisane w tym kroku wykonywane w sposób przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="7d471-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="7d471-124">Jeśli chcesz samodzielnie utworzyć klasy proxy kontynuować tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="7d471-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="7d471-125">W większości przypadków jednak można utworzyć klasy proxy dla aplikacji klienta przy użyciu programu Visual Studio jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="7d471-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="7d471-126">Serwer proxy można utworzyć za pomocą narzędzia języka opisu usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="7d471-127">Na przykład jeśli usługa XML sieci Web jest narażony na http://myserver/data/DataSetSample.asmx adres URL, należy wydać polecenie podobne do poniższych utworzyć proxy Visual Basic .NET z przestrzenią nazw z **WebData.DSSample** i zapisze go w pliku Sample.VB.</span><span class="sxs-lookup"><span data-stu-id="7d471-127">For example, if the XML Web service is exposed at the URL http://myserver/data/DataSetSample.asmx, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="7d471-128">Aby utworzyć serwer proxy C# w pliku sample.cs, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7d471-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="7d471-129">Serwer proxy można następnie skompilowany jako biblioteki i importowane do klienta usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="7d471-130">Aby skompilować kod serwera proxy Visual Basic .NET, które są przechowywane w sample.vb jako sample.dll, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7d471-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="7d471-131">Aby skompilować kod serwera proxy C# przechowywane w sample.cs jako sample.dll, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7d471-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  <span data-ttu-id="7d471-132">Tworzenie klienta usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="7d471-133">Jeśli chcesz, aby program Visual Studio Generowanie klasy serwera proxy usługi sieci Web, po prostu utworzyć projekt klienta i, w oknie Solution Explorer, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj odwołanie sieci Web**i wybierz usługę sieci Web z na liście dostępnych usług sieci Web (może to wymagać podając adres punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępny w bieżącym rozwiązaniu lub na bieżącym komputerze.) Jeśli serwer proxy usługi XML sieci Web samodzielnie utworzony (zgodnie z opisem w poprzednim kroku), można go zaimportować do kodu klienta i korzystać z metod usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7d471-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="7d471-134">Następujący przykładowy kod importuje biblioteki serwera proxy, wywołania **GetCustomers** w celu uzyskania listy klientów, dodaje nowego klienta, a następnie zwraca **DataSet** z aktualizacjami do **UpdateCustomers** .</span><span class="sxs-lookup"><span data-stu-id="7d471-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="7d471-135">Należy zauważyć, że przekazuje przykładzie **DataSet** zwrócony przez **DataSet.GetChanges** do **UpdateCustomers** ponieważ tylko zmodyfikowanych wierszy musi zostać przekazane do  **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="7d471-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="7d471-136">**UpdateCustomers** zwraca rozpoznać **zestawu danych**, które można następnie **scalania** do istniejącego **DataSet** uwzględnienie rozpoznać zmiany i wszystkie informacje o błędzie wiersza z aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="7d471-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="7d471-137">Poniższy kod założono użycie programu Visual Studio można utworzyć odwołania sieci Web i nazwy odwołania sieci Web do DsSample w **Dodaj odwołanie sieci Web** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7d471-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     <span data-ttu-id="7d471-138">Jeśli użytkownik zdecyduje się samodzielnie utworzyć klasy proxy, należy wykonać następujące dodatkowe czynności.</span><span class="sxs-lookup"><span data-stu-id="7d471-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="7d471-139">Aby skompilować próbki, podaj biblioteki serwera proxy, który został utworzony (sample.dll) i powiązane bibliotek .NET.</span><span class="sxs-lookup"><span data-stu-id="7d471-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="7d471-140">Do skompilowania programu Visual Basic .NET w wersji próbki przechowywane w client.vb pliku należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7d471-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="7d471-141">Do skompilowania wersji języka C# próbki przechowywane w client.cs pliku, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="7d471-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7d471-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d471-142">See Also</span></span>  
 [<span data-ttu-id="7d471-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d471-143">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="7d471-144">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="7d471-144">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="7d471-145">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="7d471-145">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="7d471-146">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7d471-146">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="7d471-147">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="7d471-147">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="7d471-148">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="7d471-148">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="7d471-149">Narzędzia języka opisu usługi sieci Web (Wsdl.exe)</span><span class="sxs-lookup"><span data-stu-id="7d471-149">Web Services Description Language Tool (Wsdl.exe)</span></span>](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [<span data-ttu-id="7d471-150">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="7d471-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
