---
title: Korzystanie z elementu DataSet w usłudze internetowej XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d7328949e3eb4822b1a645bb5f0c1866f01ecb0a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389752"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="4a69a-102">Korzystanie z zestawu danych z usługi sieci web XML</span><span class="sxs-lookup"><span data-stu-id="4a69a-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="4a69a-103">Został <xref:System.Data.DataSet> zaprojektowany z odłączony projekt, w części w celu ułatwienia wygodnego transportu danych przez Internet.</span><span class="sxs-lookup"><span data-stu-id="4a69a-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="4a69a-104">**Zestaw danych** jest "serializowalny", ponieważ można go określić jako dane wejściowe lub wyjściowe z usług sieci Web XML bez dodatkowego kodowania wymaganego do przesyłania strumieniowego zawartości **zestawu danych** z usługi sieci Web XML do klienta i z powrotem.</span><span class="sxs-lookup"><span data-stu-id="4a69a-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="4a69a-105">**Zestaw danych** jest niejawnie konwertowany na strumień XML przy użyciu formatu DiffGram, wysyłany przez sieć, a następnie rekonstruowany ze strumienia XML jako **zestaw danych** na końcu odbierania.</span><span class="sxs-lookup"><span data-stu-id="4a69a-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="4a69a-106">Zapewnia to bardzo prostą i elastyczną metodę przesyłania i zwracania relacyjnych danych przy użyciu usług sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="4a69a-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="4a69a-107">Aby uzyskać więcej informacji na temat formatu DiffGram, zobacz [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="4a69a-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="4a69a-108">W poniższym przykładzie pokazano, jak utworzyć usługę sieci Web XML i klienta, które używają **zestawu danych** do transportu danych relacyjnych (w tym zmodyfikowanych danych) i rozwiązywania wszelkich aktualizacji z powrotem do oryginalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4a69a-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a69a-109">Podczas tworzenia usługi sieci Web XML zaleca się zawsze uwzględnianie implikacji dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="4a69a-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="4a69a-110">Aby uzyskać informacje dotyczące zabezpieczania usługi sieci Web XML, zobacz [Zabezpieczanie usług sieci Web XML utworzonych przy użyciu ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4a69a-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="4a69a-111">Tworzenie usługi sieci web XML</span><span class="sxs-lookup"><span data-stu-id="4a69a-111">Create an XML web service</span></span>
  
1. <span data-ttu-id="4a69a-112">Utwórz usługę sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="4a69a-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="4a69a-113">W tym przykładzie tworzona jest usługa sieci Web XML, która zwraca dane, w tym przypadku listę klientów z bazy danych **Northwind** i odbiera **zestaw danych** z aktualizacjami danych, które usługa sieci Web XML jest rozpoznawana z powrotem do oryginalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4a69a-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="4a69a-114">Usługa sieci Web XML udostępnia dwie metody: **GetCustomers**, aby zwrócić listę klientów i **UpdateCustomers**, aby rozwiązać aktualizacje z powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4a69a-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="4a69a-115">Usługa sieci Web XML jest przechowywana w pliku na serwerze sieci Web o nazwie DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="4a69a-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="4a69a-116">Poniższy kod przedstawia zawartość DataSetSample.asmx.</span><span class="sxs-lookup"><span data-stu-id="4a69a-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="4a69a-117">W typowym scenariuszu **UpdateCustomers** metoda zostanie napisana, aby złapać naruszenia współbieżności optymistyczne.</span><span class="sxs-lookup"><span data-stu-id="4a69a-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="4a69a-118">Dla uproszczenia przykład nie obejmuje tego.</span><span class="sxs-lookup"><span data-stu-id="4a69a-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="4a69a-119">Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [Optymistyczna współbieżność](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="4a69a-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="4a69a-120">Tworzenie serwera proxy usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="4a69a-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="4a69a-121">Klienci usługi sieci Web XML wymagają serwera proxy PROTOKOŁU SOAP w celu korzystania z metod narażonych.</span><span class="sxs-lookup"><span data-stu-id="4a69a-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="4a69a-122">Program Visual Studio może wygenerować ten serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="4a69a-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="4a69a-123">Ustawiając odwołanie do sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie zachowanie opisane w tym kroku odbywa się w sposób przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="4a69a-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="4a69a-124">Jeśli chcesz samodzielnie utworzyć klasę proxy, kontynuuj tę dyskusję.</span><span class="sxs-lookup"><span data-stu-id="4a69a-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="4a69a-125">W większości przypadków jednak za pomocą programu Visual Studio do utworzenia klasy proxy dla aplikacji klienckiej jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="4a69a-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="4a69a-126">Serwer proxy można utworzyć za pomocą narzędzia językowego opisu usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4a69a-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="4a69a-127">Jeśli na przykład usługa sieci Web XML `http://myserver/data/DataSetSample.asmx`jest widoczna pod adresem URL, należy wydać polecenie, takie jak poniższe, aby utworzyć serwer proxy Visual Basic .NET z obszarem nazw **webdata.DSSample** i zapisać go w pliku sample.vb.</span><span class="sxs-lookup"><span data-stu-id="4a69a-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="4a69a-128">Aby utworzyć serwer proxy języka C# w pliku sample.cs, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4a69a-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="4a69a-129">Serwer proxy można następnie skompilować jako bibliotekę i zaimportować do klienta usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="4a69a-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="4a69a-130">Aby skompilować kod serwera proxy visual basic .NET przechowywany w pliku sample.vb jako plik sample.dll, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4a69a-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="4a69a-131">Aby skompilować kod serwera proxy języka C# przechowywany w sample.cs jako plik sample.dll, należy wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4a69a-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="4a69a-132">Utwórz klienta usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="4a69a-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="4a69a-133">Jeśli chcesz, aby program Visual Studio wygenerował klasę serwera proxy usługi sieci Web, po prostu utwórz projekt klienta, a w oknie Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="4a69a-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="4a69a-134">W oknie dialogowym **Dodawanie odwołania do usługi** wybierz pozycję **Zaawansowane**, a następnie wybierz pozycję Dodaj odwołanie do **sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="4a69a-134">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="4a69a-135">Wybierz usługę sieci Web z listy dostępnych usług sieci Web (może to wymagać podania adresu punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępna w bieżącym rozwiązaniu lub na bieżącym komputerze).</span><span class="sxs-lookup"><span data-stu-id="4a69a-135">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="4a69a-136">Jeśli serwer proxy usługi sieci Web XML zostanie utworzony samodzielnie (zgodnie z opisem w poprzednim kroku), można zaimportować go do kodu klienta i korzystać z metod usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="4a69a-136">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="4a69a-137">Poniższy przykładowy kod importuje bibliotekę proxy, wywołuje **GetCustomers,** aby uzyskać listę klientów, dodaje nowego klienta, a następnie zwraca **zestaw danych** z aktualizacjami **do UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="4a69a-137">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="4a69a-138">Przykład przekazuje **DataSet** zwracany przez **DataSet.GetChanges** do **UpdateCustomers,** ponieważ tylko zmodyfikowane wiersze muszą być przekazywane do **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="4a69a-138">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="4a69a-139">**UpdateCustomers** zwraca rozwiązany **DataSet**, który można następnie **scalić** do istniejącego **zestawu danych,** aby uwzględnić rozwiązane zmiany i wszelkie informacje o błędzie wiersza z aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="4a69a-139">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="4a69a-140">Poniższy kod zakłada, że program Visual Studio został użyty do utworzenia odwołania do sieci Web i że w oknie dialogowym Dodawanie odwołania do **sieci Web** zmieniono nazwę odwołania do sieci Web na dsSample.</span><span class="sxs-lookup"><span data-stu-id="4a69a-140">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="4a69a-141">Jeśli zdecydujesz się utworzyć klasę proxy samodzielnie, należy wykonać następujące dodatkowe kroki.</span><span class="sxs-lookup"><span data-stu-id="4a69a-141">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="4a69a-142">Aby skompilować przykład, podaj bibliotekę proxy, która została utworzona (sample.dll) i powiązane biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="4a69a-142">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="4a69a-143">Aby skompilować wersję programu Visual Basic .NET próbki przechowywanej w pliku client.vb, wystawić następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4a69a-143">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="4a69a-144">Aby skompilować wersję C# próbki, przechowywane w pliku client.cs, wydać następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4a69a-144">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a69a-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a69a-145">See also</span></span>

- [<span data-ttu-id="4a69a-146">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a69a-146">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="4a69a-147">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="4a69a-147">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4a69a-148">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="4a69a-148">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="4a69a-149">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="4a69a-149">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="4a69a-150">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="4a69a-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="4a69a-151">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="4a69a-151">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="4a69a-152">[Narzędzie do opisu opisu usług sieci Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4a69a-152">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="4a69a-153">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a69a-153">ADO.NET Overview</span></span>](../ado-net-overview.md)
