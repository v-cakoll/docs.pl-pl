---
title: Korzystanie z zestawu danych z usługi sieci Web XML
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 2c8924ee3374489dded7e819ecde8e4d9da750bb
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374389"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="f5d9d-102">Korzystanie z zestawu danych z usługi sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="f5d9d-102">Consume a DataSet from an XML web service</span></span>

<span data-ttu-id="f5d9d-103"><xref:System.Data.DataSet>Został zaprojektowany z rozłączonym projektem, w części aby ułatwić wygodne przesyłanie danych przez Internet.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="f5d9d-104">**Zestaw danych** jest "możliwy do serializacji" w tym, że może być określony jako dane wejściowe lub wyjściowe z usług sieci Web XML bez dodatkowego kodowania wymaganego do przesyłania strumieniowego zawartości **zestawu danych** z usługi sieci Web XML do klienta i z powrotem.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="f5d9d-105">**Zestaw danych** jest niejawnie konwertowany na strumień XML przy użyciu formatu DiffGram, wysyłanego przez sieć, a następnie ponownie skonstruowany ze strumienia XML jako **zestaw danych** na końcu odbiorczej.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="f5d9d-106">Zapewnia to prostą i elastyczną metodę przesyłania i zwracania danych relacyjnych przy użyciu usług sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-106">This gives you a simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="f5d9d-107">Aby uzyskać więcej informacji na temat formatu DiffGram, zobacz [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="f5d9d-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="f5d9d-108">Poniższy przykład pokazuje, jak utworzyć usługę sieci Web XML i klienta, który używa **zestawu danych** do transportowania danych relacyjnych (w tym zmodyfikowanych danych) i rozwiązać wszelkie aktualizacje z powrotem do oryginalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5d9d-109">Przesyłanie `DataSet` lub `DataTable` wystąpienia w ramach wywołań usługi sieci Web XML nie jest bezpieczne, jeśli dane wejściowe nie są zaufane.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-109">Transmitting `DataSet` or `DataTable` instances as part of XML Web service calls is not safe if the input is not trusted.</span></span> <span data-ttu-id="f5d9d-110">Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące zabezpieczeń zestawów danych i DataTable](/dotnet/framework/data/adonet/dataset-datatable-dataview/security-guidance).</span><span class="sxs-lookup"><span data-stu-id="f5d9d-110">For more information, see [DataSet and DataTable security guidance](/dotnet/framework/data/adonet/dataset-datatable-dataview/security-guidance).</span></span>
> <span data-ttu-id="f5d9d-111">Zalecamy również, aby podczas tworzenia usługi sieci Web XML zawsze uwzględnić implikacje związane z bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-111">We also recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="f5d9d-112">Aby uzyskać informacje na temat zabezpieczania usługi sieci Web XML, zobacz [Zabezpieczanie usług sieci Web XML utworzonych za pomocą ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f5d9d-112">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
## <a name="create-an-xml-web-service"></a><span data-ttu-id="f5d9d-113">Tworzenie usługi sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="f5d9d-113">Create an XML web service</span></span>
  
1. <span data-ttu-id="f5d9d-114">Utwórz usługę sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-114">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="f5d9d-115">W tym przykładzie zostanie utworzona usługa sieci Web XML, która zwraca dane, w tym przypadku listę klientów z bazy danych **Northwind** i otrzymuje **zestaw danych** z aktualizacjami danych, które usługa sieci Web XML rozpoznaje z powrotem do oryginalnego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-115">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="f5d9d-116">Usługa sieci Web XML uwidacznia dwie metody: **GetCustomers**, aby zwrócić listę klientów i **UpdateCustomers**, aby rozwiązać aktualizacje z powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-116">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="f5d9d-117">Usługa sieci Web XML jest przechowywana w pliku na serwerze sieci Web o nazwie DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-117">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="f5d9d-118">Poniższy kod przedstawia zawartość DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-118">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
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
  
     <span data-ttu-id="f5d9d-119">W typowym scenariuszu Metoda **UpdateCustomers** jest zapisywana w celu przechwytywania optymistycznych naruszeń współbieżności.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-119">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="f5d9d-120">Dla uproszczenia nie obejmuje to przykładu.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-120">For simplicity, the example does not include this.</span></span> <span data-ttu-id="f5d9d-121">Aby uzyskać więcej informacji na temat współbieżności optymistycznej, zobacz [optymistyczne współbieżność](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="f5d9d-121">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="f5d9d-122">Utwórz serwer proxy usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-122">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="f5d9d-123">Klienci usługi sieci Web XML wymagają serwera proxy protokołu SOAP, aby można było korzystać z uwidocznionych metod.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-123">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="f5d9d-124">Program Visual Studio może generować ten serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-124">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="f5d9d-125">Przez ustawienie odwołania sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie zachowania opisane w tym kroku są wykonywane w sposób przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-125">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="f5d9d-126">Jeśli chcesz samodzielnie utworzyć klasę proxy, przejdź do tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-126">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="f5d9d-127">Jednak w większości przypadków użycie programu Visual Studio do utworzenia klasy proxy dla aplikacji klienckiej jest wystarczające.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-127">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="f5d9d-128">Serwer proxy można utworzyć za pomocą narzędzia Web Services Description Language.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-128">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="f5d9d-129">Jeśli na przykład usługa sieci Web XML jest uwidoczniona pod adresem URL `http://myserver/data/DataSetSample.asmx` , należy wydać następujące polecenie, aby utworzyć serwer proxy Visual Basic .NET z przestrzenią nazw **webdata. DSSample** i zapisać go w pliku Sample. vb.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-129">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="f5d9d-130">Aby utworzyć serwer proxy C# w pliku sample.cs, wydaj następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-130">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="f5d9d-131">Serwer proxy może być następnie skompilowany jako biblioteka i zaimportowany do klienta usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-131">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="f5d9d-132">Aby skompilować kod serwera proxy programu Visual Basic .NET zapisany w przykład. vb jako sample.dll, wydaj następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-132">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="f5d9d-133">Aby skompilować kod serwera proxy C# przechowywany w sample.cs jako sample.dll, wydaj następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-133">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="f5d9d-134">Utwórz klienta usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-134">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="f5d9d-135">Jeśli chcesz, aby program Visual Studio wygenerował klasę proxy usługi sieci Web, po prostu Utwórz projekt klienta, a następnie w oknie Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-135">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, and then select **Add** > **Service Reference**.</span></span> <span data-ttu-id="f5d9d-136">W oknie dialogowym **Dodaj odwołanie do usługi** wybierz pozycję **Zaawansowane**, a następnie wybierz pozycję **Dodaj odwołanie sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-136">In the **Add Service Reference** dialog box, select **Advanced**, and then select **Add Web Reference**.</span></span> <span data-ttu-id="f5d9d-137">Wybierz usługę sieci Web z listy dostępnych usług sieci Web (może to wymagać dostarczenia adresu punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępna w ramach bieżącego rozwiązania lub na bieżącym komputerze).</span><span class="sxs-lookup"><span data-stu-id="f5d9d-137">Select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint if the Web service isn't available within the current solution or on the current computer).</span></span> <span data-ttu-id="f5d9d-138">Jeśli utworzysz serwer proxy usługi sieci Web XML samodzielnie (zgodnie z opisem w poprzednim kroku), możesz zaimportować go do kodu klienta i korzystać z metod usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-138">If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span>

     <span data-ttu-id="f5d9d-139">Poniższy przykładowy kod importuje bibliotekę proxy, wywołuje metodę **GetCustomers** , aby uzyskać listę klientów, dodaje nowego klienta, a następnie zwraca **zestaw danych** z aktualizacjami do **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-139">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="f5d9d-140">Przykład przekazuje **zestaw danych** zwrócony przez **DataSet. GetChanges** to **UpdateCustomers** , ponieważ tylko zmodyfikowane wiersze muszą być przekazywane do **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-140">The example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="f5d9d-141">**UpdateCustomers** zwraca rozpoznany **zestaw danych**, który można następnie **scalić** z istniejącym **zestawem danych** , aby uwzględnić rozwiązane zmiany i informacje o błędzie wiersza z aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-141">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="f5d9d-142">Poniższy kod zakłada, że program Visual Studio został użyty do utworzenia odwołania sieci Web i że zmieniono nazwę odwołania sieci Web na DsSample w oknie dialogowym **Dodaj odwołanie sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="f5d9d-142">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
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
  
     <span data-ttu-id="f5d9d-143">Jeśli zdecydujesz się samodzielnie utworzyć klasę proxy, musisz wykonać następujące dodatkowe czynności.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-143">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="f5d9d-144">Aby skompilować przykład, należy podać bibliotekę proxy, która została utworzona (sample.dll) i powiązane biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-144">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="f5d9d-145">Aby skompilować wersję próbną programu Visual Basic .NET, która jest przechowywana w pliku Client. vb, wydaj następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-145">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="f5d9d-146">Aby skompilować wersję języka C# z przykładu, która jest przechowywana w pliku client.cs, wydaj następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="f5d9d-146">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f5d9d-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5d9d-147">See also</span></span>

- [<span data-ttu-id="f5d9d-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5d9d-148">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="f5d9d-149">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="f5d9d-149">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="f5d9d-150">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="f5d9d-150">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="f5d9d-151">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="f5d9d-151">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="f5d9d-152">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="f5d9d-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="f5d9d-153">Parametry elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="f5d9d-153">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="f5d9d-154">[Narzędzie Web Services Description Language (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f5d9d-154">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- [<span data-ttu-id="f5d9d-155">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5d9d-155">ADO.NET Overview</span></span>](../ado-net-overview.md)
