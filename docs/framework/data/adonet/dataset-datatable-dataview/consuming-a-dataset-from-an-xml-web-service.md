---
title: Korzystanie z elementu DataSet w usłudze internetowej XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d835ffe7a10492ee731de8e5301e6d34545f9c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151393"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Korzystanie z elementu DataSet w usłudze internetowej XML
Został <xref:System.Data.DataSet> zaprojektowany z odłączony projekt, w części w celu ułatwienia wygodnego transportu danych przez Internet. **Zestaw danych** jest "serializowalny", ponieważ można go określić jako dane wejściowe lub wyjściowe z usług sieci Web XML bez dodatkowego kodowania wymaganego do przesyłania strumieniowego zawartości **zestawu danych** z usługi sieci Web XML do klienta i z powrotem. **Zestaw danych** jest niejawnie konwertowany na strumień XML przy użyciu formatu DiffGram, wysyłany przez sieć, a następnie rekonstruowany ze strumienia XML jako **zestaw danych** na końcu odbierania. Zapewnia to bardzo prostą i elastyczną metodę przesyłania i zwracania relacyjnych danych przy użyciu usług sieci Web XML. Aby uzyskać więcej informacji na temat formatu DiffGram, zobacz [DiffGrams](diffgrams.md).  
  
 W poniższym przykładzie pokazano, jak utworzyć usługę sieci Web XML i klienta, które używają **zestawu danych** do transportu danych relacyjnych (w tym zmodyfikowanych danych) i rozwiązywania wszelkich aktualizacji z powrotem do oryginalnego źródła danych.  
  
> [!NOTE]
> Podczas tworzenia usługi sieci Web XML zaleca się zawsze uwzględnianie implikacji dla bezpieczeństwa. Aby uzyskać informacje dotyczące zabezpieczania usługi sieci Web XML, zobacz [Zabezpieczanie usług sieci Web XML utworzonych przy użyciu ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Aby utworzyć usługę sieci Web XML, która zwraca i zużywa zestaw danych  
  
1. Utwórz usługę sieci Web XML.  
  
     W tym przykładzie tworzona jest usługa sieci Web XML, która zwraca dane, w tym przypadku listę klientów z bazy danych **Northwind** i odbiera **zestaw danych** z aktualizacjami danych, które usługa sieci Web XML jest rozpoznawana z powrotem do oryginalnego źródła danych.  
  
     Usługa sieci Web XML udostępnia dwie metody: **GetCustomers**, aby zwrócić listę klientów i **UpdateCustomers**, aby rozwiązać aktualizacje z powrotem do źródła danych. Usługa sieci Web XML jest przechowywana w pliku na serwerze sieci Web o nazwie DataSetSample.asmx. Poniższy kod przedstawia zawartość DataSetSample.asmx.  
  
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
  
     W typowym scenariuszu **UpdateCustomers** metoda zostanie napisana, aby złapać naruszenia współbieżności optymistyczne. Dla uproszczenia przykład nie obejmuje tego. Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [Optymistyczna współbieżność](../optimistic-concurrency.md).  
  
2. Tworzenie serwera proxy usługi sieci Web XML.  
  
     Klienci usługi sieci Web XML wymagają serwera proxy PROTOKOŁU SOAP w celu korzystania z metod narażonych. Program Visual Studio może wygenerować ten serwer proxy. Ustawiając odwołanie do sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie zachowanie opisane w tym kroku odbywa się w sposób przezroczysty. Jeśli chcesz samodzielnie utworzyć klasę proxy, kontynuuj tę dyskusję. W większości przypadków jednak za pomocą programu Visual Studio do utworzenia klasy proxy dla aplikacji klienckiej jest wystarczająca.  
  
     Serwer proxy można utworzyć za pomocą narzędzia językowego opisu usług sieci Web. Jeśli na przykład usługa sieci Web XML `http://myserver/data/DataSetSample.asmx`jest widoczna pod adresem URL, należy wydać polecenie, takie jak poniższe, aby utworzyć serwer proxy Visual Basic .NET z obszarem nazw **webdata.DSSample** i zapisać go w pliku sample.vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Aby utworzyć serwer proxy języka C# w pliku sample.cs, należy wydać następujące polecenie.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Serwer proxy można następnie skompilować jako bibliotekę i zaimportować do klienta usługi sieci Web XML. Aby skompilować kod serwera proxy visual basic .NET przechowywany w pliku sample.vb jako plik sample.dll, należy wydać następujące polecenie.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Aby skompilować kod serwera proxy języka C# przechowywany w sample.cs jako plik sample.dll, należy wydać następujące polecenie.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Utwórz klienta usługi sieci Web XML.  
  
     Jeśli chcesz, aby program Visual Studio wygenerował dla Ciebie klasę serwera proxy usługi sieci Web, po prostu utwórz projekt klienta, a w oknie Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, kliknij polecenie **Dodaj odwołanie do sieci Web**i wybierz usługę sieci Web z listy dostępnych usług sieci Web (może to wymagać podania adresu punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępna w bieżącym rozwiązaniu lub na bieżącym komputerze). Jeśli serwer proxy usługi sieci Web XML zostanie utworzony samodzielnie (zgodnie z opisem w poprzednim kroku), można zaimportować go do kodu klienta i korzystać z metod usługi sieci Web XML. Poniższy przykładowy kod importuje bibliotekę proxy, wywołuje **GetCustomers,** aby uzyskać listę klientów, dodaje nowego klienta, a następnie zwraca **zestaw danych** z aktualizacjami **do UpdateCustomers**.  
  
     Należy zauważyć, że w przykładzie przekazuje **DataSet** zwracany przez **DataSet.GetChanges** do **UpdateCustomers,** ponieważ tylko zmodyfikowane wiersze muszą być przekazywane do **UpdateCustomers**. **UpdateCustomers** zwraca rozwiązany **DataSet**, który można następnie **scalić** do istniejącego **zestawu danych,** aby uwzględnić rozwiązane zmiany i wszelkie informacje o błędzie wiersza z aktualizacji. Poniższy kod zakłada, że program Visual Studio został użyty do utworzenia odwołania do sieci Web i że w oknie dialogowym Dodawanie odwołania do **sieci Web** zmieniono nazwę odwołania do sieci Web na dsSample.  
  
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
  
     Jeśli zdecydujesz się utworzyć klasę proxy samodzielnie, należy wykonać następujące dodatkowe kroki. Aby skompilować przykład, podaj bibliotekę proxy, która została utworzona (sample.dll) i powiązane biblioteki .NET. Aby skompilować wersję programu Visual Basic .NET próbki przechowywanej w pliku client.vb, wystawić następujące polecenie.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Aby skompilować wersję C# próbki, przechowywane w pliku client.cs, wydać następujące polecenie.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [ADO.NET](../index.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Elementy DataTable](datatables.md)
- [Wypełnianie zestawu danych z elementu DataAdapter](../populating-a-dataset-from-a-dataadapter.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapter](../updating-data-sources-with-dataadapters.md)
- [Parametry elementu DataAdapter](../dataadapter-parameters.md)
- [Narzędzie do opisu opisu usług sieci Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [Omówienie ADO.NET](../ado-net-overview.md)
