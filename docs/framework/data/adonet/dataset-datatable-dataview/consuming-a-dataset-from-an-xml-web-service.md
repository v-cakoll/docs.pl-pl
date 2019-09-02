---
title: Korzystanie z elementu DataSet w usłudze internetowej XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 962163b51507647fd975815c214891a6d692e66c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203948"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Korzystanie z elementu DataSet w usłudze internetowej XML
<xref:System.Data.DataSet> Został zaprojektowany z rozłączonym projektem, w części aby ułatwić wygodne przesyłanie danych przez Internet. **Zestaw danych** jest "możliwy do serializacji" w tym, że może być określony jako dane wejściowe lub wyjściowe z usług sieci Web XML bez dodatkowego kodowania wymaganego do przesyłania strumieniowego zawartości **zestawu danych** z usługi sieci Web XML do klienta i z powrotem. **Zestaw danych** jest niejawnie konwertowany na strumień XML przy użyciu formatu DiffGram, wysyłanego przez sieć, a następnie ponownie skonstruowany ze strumienia XML jako **zestaw danych** na końcu odbiorczej. Zapewnia to prostą i elastyczną metodę przesyłania i zwracania danych relacyjnych za pomocą usług sieci Web XML. Aby uzyskać więcej informacji na temat formatu DiffGram, zobacz [DiffGrams](diffgrams.md).  
  
 Poniższy przykład pokazuje, jak utworzyć usługę sieci Web XML i klienta, który używa **zestawu danych** do transportowania danych relacyjnych (w tym zmodyfikowanych danych) i rozwiązać wszelkie aktualizacje z powrotem do oryginalnego źródła danych.  
  
> [!NOTE]
> Zalecamy, aby podczas tworzenia usługi sieci Web XML zawsze uwzględnić implikacje związane z bezpieczeństwem. Aby uzyskać informacje na temat zabezpieczania usługi sieci Web XML, zobacz [Zabezpieczanie usług sieci Web XML utworzonych za pomocą ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Aby utworzyć usługę sieci Web XML, która zwraca i zużywa zestaw danych  
  
1. Utwórz usługę sieci Web XML.  
  
     W tym przykładzie zostanie utworzona usługa sieci Web XML, która zwraca dane, w tym przypadku listę klientów z bazy danych **Northwind** i otrzymuje **zestaw danych** z aktualizacjami danych, które usługa sieci Web XML rozpoznaje z powrotem do oryginalnego źródła danych.  
  
     Usługa sieci Web XML uwidacznia dwie metody: **GetCustomers**, aby zwrócić listę klientów i **UpdateCustomers**, aby rozwiązać aktualizacje z powrotem do źródła danych. Usługa sieci Web XML jest przechowywana w pliku na serwerze sieci Web o nazwie DataSetSample. asmx. Poniższy kod przedstawia zawartość DataSetSample. asmx.  
  
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
  
     W typowym scenariuszu Metoda **UpdateCustomers** jest zapisywana w celu przechwytywania optymistycznych naruszeń współbieżności. Dla uproszczenia nie obejmuje to przykładu. Aby uzyskać więcej informacji na temat współbieżności optymistycznej, zobacz [optymistyczne współbieżność](../optimistic-concurrency.md).  
  
2. Utwórz serwer proxy usługi sieci Web XML.  
  
     Klienci usługi sieci Web XML wymagają serwera proxy protokołu SOAP, aby można było korzystać z uwidocznionych metod. Program Visual Studio może generować ten serwer proxy. Przez ustawienie odwołania sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie zachowania opisane w tym kroku są wykonywane w sposób przezroczysty. Jeśli chcesz samodzielnie utworzyć klasę proxy, przejdź do tej dyskusji. Jednak w większości przypadków użycie programu Visual Studio do utworzenia klasy proxy dla aplikacji klienckiej jest wystarczające.  
  
     Serwer proxy można utworzyć za pomocą narzędzia Web Services Description Language. Jeśli na przykład usługa sieci Web XML jest uwidoczniona pod adresem URL `http://myserver/data/DataSetSample.asmx`, należy wydać następujące polecenie, aby utworzyć serwer proxy Visual Basic .NET z przestrzenią nazw webdata **. DSSample** i zapisać go w pliku Sample. vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Aby utworzyć C# serwer proxy w pliku Sample.cs, wydaj następujące polecenie.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Serwer proxy może być następnie skompilowany jako biblioteka i zaimportowany do klienta usługi sieci Web XML. Aby skompilować kod serwera proxy programu Visual Basic .NET przechowywany w pliku Sample. vb jako Sample. dll, wydaj następujące polecenie.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Aby skompilować kod C# serwera proxy przechowywany w Sample.cs jako Sample. dll, wydaj następujące polecenie.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Utwórz klienta usługi sieci Web XML.  
  
     Jeśli chcesz, aby program Visual Studio wygenerował klasę proxy usługi sieci Web, po prostu Utwórz projekt klienta, a następnie w oknie Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, kliknij polecenie **Dodaj odwołanie sieci Web**, a następnie wybierz usługę sieci Web z listy dostępnych sieci Web usługi (mogą wymagać podania adresu punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępna w ramach bieżącego rozwiązania lub na bieżącym komputerze). Jeśli utworzysz serwer proxy usługi sieci Web XML samodzielnie (zgodnie z opisem w poprzednim kroku), możesz zaimportować go do kodu klienta i korzystać z metod usługi sieci Web XML. Poniższy przykładowy kod importuje bibliotekę proxy, wywołuje metodę **GetCustomers** , aby uzyskać listę klientów, dodaje nowego klienta, a następnie zwraca **zestaw danych** z aktualizacjami do **UpdateCustomers**.  
  
     Należy zauważyć, że przykład przekazuje **zestaw danych** zwrócony przez **DataSet.** GetChanges to **UpdateCustomers** , ponieważ tylko zmodyfikowane wiersze muszą być przekazywane do **UpdateCustomers**. **UpdateCustomers** zwraca rozpoznany **zestaw danych**, który można następnie **scalić** z istniejącym **zestawem danych** , aby uwzględnić rozwiązane zmiany i informacje o błędzie wiersza z aktualizacji. Poniższy kod zakłada, że program Visual Studio został użyty do utworzenia odwołania sieci Web i że zmieniono nazwę odwołania sieci Web na DsSample w oknie dialogowym **Dodaj odwołanie sieci Web** .  
  
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
  
     Jeśli zdecydujesz się samodzielnie utworzyć klasę proxy, musisz wykonać następujące dodatkowe czynności. Aby skompilować przykład, należy podać bibliotekę proxy, która została utworzona (Sample. dll) i powiązane biblioteki .NET. Aby skompilować wersję próbną programu Visual Basic .NET, która jest przechowywana w pliku Client. vb, wydaj następujące polecenie.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Aby skompilować C# wersję przykładu przechowywaną w pliku Client.cs, wydaj następujące polecenie.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../index.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Elementy DataTable](datatables.md)
- [Wypełnianie zestawu danych z elementu DataAdapter](../populating-a-dataset-from-a-dataadapter.md)
- [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../updating-data-sources-with-dataadapters.md)
- [Parametry elementu DataAdapter](../dataadapter-parameters.md)
- [Narzędzie Web Services Description Language (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
