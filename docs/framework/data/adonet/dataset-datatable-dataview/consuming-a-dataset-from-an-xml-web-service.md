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
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Korzystanie z zestawu danych z usługi sieci Web XML
<xref:System.Data.DataSet> Została zaprojektowana z projektem bez połączenia, w części w celu ułatwienia wygodny transportu danych za pośrednictwem Internetu. **DataSet** jest "serializacji" można określić jako dane wejściowe lub dane wyjściowe z usług XML sieci Web bez dodatkowy kod wymagany do strumienia zawartości **DataSet** z usługi XML sieci Web do klienta i z powrotem. **DataSet** jest niejawnie przekonwertować na strumień XML przy użyciu formatu elementu DiffGram wysyłane za pośrednictwem sieci i następnie odtworzyć strumienia XML jako **DataSet** po stronie odbiorczej. Zapewnia to bardzo prosty i elastyczny — metoda przekazywania i zwracający dane relacyjne przy użyciu usług XML sieci Web. Aby uzyskać więcej informacji na temat formatu elementu DiffGram, zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 Poniższy przykład przedstawia sposób tworzenia usługi XML sieci Web i klienta, który używał **DataSet** do przesyłania danych relacyjnych (włącznie z danymi zmodyfikowanego) i rozwiązać wszelkie aktualizacje z powrotem do oryginalnego źródła danych.  
  
> [!NOTE]
>  Firma Microsoft zaleca zawsze rozważ wpływ na bezpieczeństwo podczas tworzenia usługi XML sieci Web. Aby uzyskać informacje na temat zabezpieczenia usługi XML sieci Web, zobacz [zabezpieczanie XML sieci Web usług utworzone za pomocą programu ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Aby utworzyć usługi XML sieci Web, która zwraca i korzysta z zestawu danych  
  
1.  Tworzenie usługi XML sieci Web.  
  
     W tym przykładzie usługi XML sieci Web utworzono, która zwraca dane, w tym przypadku listę klientów z **Northwind** bazy danych i odbiera **DataSet** z aktualizacjami danych, które usługi XML sieci Web rozpoznaje wstecz do oryginalnego źródła danych.  
  
     Usługa XML sieci Web udostępnia dwie metody: **GetCustomers**, aby zwrócić listę klientów, a **UpdateCustomers**, aby rozpoznać aktualizacji źródła danych. Usługa XML sieci Web są przechowywane w pliku na serwerze sieci Web o nazwie DataSetSample.asmx. Poniższy kod przedstawia zawartość DataSetSample.asmx.  
  
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
  
     W typowym scenariuszu **UpdateCustomers** metody powinny być zapisane catch naruszeń optymistycznej współbieżności. Dla uproszczenia przykładzie nie obejmuje to. Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [optymistycznej współbieżności](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Utwórz serwer proxy usługi XML sieci Web.  
  
     Klienci usługi XML sieci Web wymagają serwera proxy protokołu SOAP aby można było korzystać z metod uwidocznione. Może mieć Visual Studio Generowanie ten serwer proxy dla Ciebie. Ustawiając odwołanie sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie działania opisane w tym kroku wykonywane w sposób przezroczysty. Jeśli chcesz samodzielnie utworzyć klasy proxy kontynuować tej dyskusji. W większości przypadków jednak można utworzyć klasy proxy dla aplikacji klienta przy użyciu programu Visual Studio jest wystarczająca.  
  
     Serwer proxy można utworzyć za pomocą narzędzia języka opisu usługi sieci Web. Na przykład jeśli usługa XML sieci Web jest narażony na http://myserver/data/DataSetSample.asmx adres URL, należy wydać polecenie podobne do poniższych utworzyć proxy Visual Basic .NET z przestrzenią nazw z **WebData.DSSample** i zapisze go w pliku Sample.VB.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Aby utworzyć serwer proxy C# w pliku sample.cs, należy wydać następujące polecenie.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Serwer proxy można następnie skompilowany jako biblioteki i importowane do klienta usługi XML sieci Web. Aby skompilować kod serwera proxy Visual Basic .NET, które są przechowywane w sample.vb jako sample.dll, należy wydać następujące polecenie.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Aby skompilować kod serwera proxy C# przechowywane w sample.cs jako sample.dll, należy wydać następujące polecenie.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Tworzenie klienta usługi XML sieci Web.  
  
     Jeśli chcesz, aby program Visual Studio Generowanie klasy serwera proxy usługi sieci Web, po prostu utworzyć projekt klienta i, w oknie Solution Explorer, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj odwołanie sieci Web**i wybierz usługę sieci Web z na liście dostępnych usług sieci Web (może to wymagać podając adres punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępny w bieżącym rozwiązaniu lub na bieżącym komputerze.) Jeśli serwer proxy usługi XML sieci Web samodzielnie utworzony (zgodnie z opisem w poprzednim kroku), można go zaimportować do kodu klienta i korzystać z metod usługi XML sieci Web. Następujący przykładowy kod importuje biblioteki serwera proxy, wywołania **GetCustomers** w celu uzyskania listy klientów, dodaje nowego klienta, a następnie zwraca **DataSet** z aktualizacjami do **UpdateCustomers** .  
  
     Należy zauważyć, że przekazuje przykładzie **DataSet** zwrócony przez **DataSet.GetChanges** do **UpdateCustomers** ponieważ tylko zmodyfikowanych wierszy musi zostać przekazane do  **UpdateCustomers**. **UpdateCustomers** zwraca rozpoznać **zestawu danych**, które można następnie **scalania** do istniejącego **DataSet** uwzględnienie rozpoznać zmiany i wszystkie informacje o błędzie wiersza z aktualizacji. Poniższy kod założono użycie programu Visual Studio można utworzyć odwołania sieci Web i nazwy odwołania sieci Web do DsSample w **Dodaj odwołanie sieci Web** okno dialogowe.  
  
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
  
     Jeśli użytkownik zdecyduje się samodzielnie utworzyć klasy proxy, należy wykonać następujące dodatkowe czynności. Aby skompilować próbki, podaj biblioteki serwera proxy, który został utworzony (sample.dll) i powiązane bibliotek .NET. Do skompilowania programu Visual Basic .NET w wersji próbki przechowywane w client.vb pliku należy wydać następujące polecenie.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Do skompilowania wersji języka C# próbki przechowywane w client.cs pliku, należy wydać następujące polecenie.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Parametry elementu DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Narzędzia języka opisu usługi sieci Web (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
