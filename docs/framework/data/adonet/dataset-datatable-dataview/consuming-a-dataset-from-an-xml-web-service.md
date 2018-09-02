---
title: Korzystanie z zestawu danych z usługi sieci Web XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: ab96e8f3395a78c88184872a2c78b71fb2bf7b9e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403464"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Korzystanie z zestawu danych z usługi sieci Web XML
<xref:System.Data.DataSet> Została zaprojektowana z projektem bez połączenia, w części w celu ułatwienia wygodne transportu danych za pośrednictwem Internetu. **DataSet** jest "serializacji", może być określony jako dane wejściowe lub dane wyjściowe z usług XML sieci Web bez pisania dodatkowe wymagane do przesyłania strumieniowego zawartości **DataSet** z usługi XML sieci Web do klientów i z powrotem. **DataSet** niejawnie konwertowane na strumień XML przy użyciu formatu w formacie DiffGram, wysyłane przez sieć i następnie odtworzone strumień XML jako **DataSet** po stronie odbiorczej. Zapewnia to bardzo prosty i elastyczny metody przesyłania i zwraca dane relacyjne przy użyciu usług XML sieci Web. Aby uzyskać więcej informacji na temat formatu w formacie DiffGram zobacz [DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 Poniższy przykład przedstawia sposób tworzenia usługi XML sieci Web i klienta, który używał **DataSet** do przesyłania danych relacyjnych (w tym zmodyfikowanych danych) i rozwiązać wszelkie aktualizacje z powrotem do oryginalnego źródła danych.  
  
> [!NOTE]
>  Zaleca się, że należy zawsze należy wziąć pod uwagę skutki dla bezpieczeństwa podczas tworzenia usługi XML sieci Web. Aby uzyskać informacje na temat zabezpieczenia usługi sieci Web XML, zobacz [zabezpieczanie XML sieci Web usług utworzone za pomocą programu ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Do tworzenia usługi XML sieci Web, zwraca wartość, która korzysta z zestawu danych  
  
1.  Utwórz usługę sieci Web XML.  
  
     W przykładzie, usługi XML sieci Web zostanie utworzona, która zwraca dane, w tym przypadku listę klientów z **Northwind** bazy danych i odbiera **zestawu danych** dzięki aktualizacjom danych, które usługi sieci Web XML rozwiązuje do oryginalnego źródła danych.  
  
     Usługi sieci Web XML udostępnia dwie metody: **GetCustomers**, aby zwrócić listę klientów, a **UpdateCustomers**, aby rozpoznać aktualizacji źródła danych. Usługi sieci Web XML są przechowywane w pliku na serwerze sieci Web o nazwie DataSetSample.asmx. Poniższy kod przedstawia zawartość DataSetSample.asmx.  
  
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
  
     W typowym scenariuszu **UpdateCustomers** metody powinny być zapisane catch naruszeń optymistycznej współbieżności. Dla uproszczenia przykładu nie obejmuje to. Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [optymistycznej współbieżności](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Utwórz serwer proxy usługi sieci Web XML.  
  
     Klienci usługi XML sieci Web wymagają serwera proxy protokołu SOAP celu korzystania z metody narażone. Masz program Visual Studio, generowanie ten serwer proxy dla Ciebie. Ustawiając odwołanie sieci Web do istniejącej usługi sieci Web z poziomu programu Visual Studio, wszystkie zachowanie, które są opisane w tym kroku wykonywane w sposób przezroczysty. Jeśli chcesz utworzyć klasy proxy samodzielnie, przejdź do tej dyskusji. W większości przypadków jednak przy użyciu programu Visual Studio do utworzenia klasy serwera proxy dla aplikacji klienckiej jest wystarczająca.  
  
     Serwer proxy mogą być tworzone za pomocą narzędzia języka opisu usługi sieci Web. Na przykład, jeśli usługi XML sieci Web jest uwidaczniany pod adresem URL http://myserver/data/DataSetSample.asmx, należy wydać polecenie takich jak utworzyć serwer proxy programu Visual Basic .NET z przestrzeni nazw **WebData.DSSample** i zapisz go w sample.vb pliku.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Aby utworzyć serwer proxy C# w sample.cs pliku, należy wydać następujące polecenie.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Serwer proxy można być kompilowany jako biblioteka i importowane do klienta usług XML sieci Web. Aby skompilować kod serwera proxy programu Visual Basic .NET, które są przechowywane w sample.vb jako sample.dll, należy wydać następujące polecenie.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Aby skompilować kod C# proxy przechowywane w sample.cs jako sample.dll, należy wydać następujące polecenie.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Tworzenie klienta usługi XML sieci Web.  
  
     Jeśli chcesz program Visual Studio, Generowanie klasy serwera proxy usługi sieci Web dla Ciebie, po prostu utworzyć projekt klienta, a w oknie Eksploratora rozwiązań kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj odwołanie sieci Web**i wybierz usługę sieci Web z na liście dostępnych usług sieci Web (może to wymagać udostępnia adres punktu końcowego usługi sieci Web, jeśli usługa sieci Web nie jest dostępny w bieżącym rozwiązaniu lub na bieżącym komputerze.) Jeśli utworzysz serwer proxy usługi sieci Web XML, samodzielnie (zgodnie z opisem w poprzednim kroku), można zaimportować go do kodu klienta i korzystać z metody usługi sieci Web XML. Następujący przykładowy kod importuje biblioteki serwera proxy, wywołania **GetCustomers** można uzyskać listy klientów, dodaje nowego klienta, a następnie zwraca **zestawu danych** dzięki aktualizacjom **UpdateCustomers** .  
  
     Należy zauważyć, że w przykładzie **DataSet** zwrócone przez **DataSet.GetChanges** do **UpdateCustomers** ponieważ tylko zmodyfikowane wiersze, które muszą zostać przekazane do  **UpdateCustomers**. **UpdateCustomers** zwraca rozpoznać **zestawu danych**, który można następnie **scalania** się z istniejącymi **zestawu danych** zmiany rozwiązane i dowolne informacje o błędzie wiersza z aktualizacji. Poniższy kod zakłada korzystasz z programu Visual Studio można utworzyć odwołania sieci Web i nazwy odwołania sieci Web do DsSample w **Dodaj odwołanie sieci Web** okno dialogowe.  
  
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
  
     Jeśli zdecydujesz się utworzyć klasy proxy samodzielnie, należy wykonać następujące dodatkowe czynności. Aby skompilować przykład, należy podać biblioteki serwera proxy, który został utworzony (sample.dll) i powiązane biblioteki .NET. Skompilować wersji Visual Basic .NET, próbki, przechowywane w client.vb pliku, należy wydać następujące polecenie.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Skompilować wersji języka C# próbki, przechowywane w client.cs pliku, należy wydać następujące polecenie.  
  
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
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
