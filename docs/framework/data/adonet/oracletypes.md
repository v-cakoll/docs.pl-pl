---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 1fea43260cce2a3b284dd2297f48f43453002cb3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512076"
---
# <a name="oracletypes"></a><span data-ttu-id="db723-102">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="db723-102">OracleTypes</span></span>
<span data-ttu-id="db723-103">.NET Framework Data Provider for Oracle obejmuje kilka struktur, które można użyć do pracy z typami danych Oracle.</span><span class="sxs-lookup"><span data-stu-id="db723-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="db723-104">Obejmują one <xref:System.Data.OracleClient.OracleNumber> i <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="db723-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db723-105">Aby uzyskać pełną listę tych struktur, zobacz <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="db723-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="db723-106">W poniższych C# przykładach:</span><span class="sxs-lookup"><span data-stu-id="db723-106">The following C# examples:</span></span>  
  
-   <span data-ttu-id="db723-107">Tworzenie tabeli bazy danych Oracle i załaduj go z danymi.</span><span class="sxs-lookup"><span data-stu-id="db723-107">Create an Oracle table and load it with data.</span></span>  
  
-   <span data-ttu-id="db723-108">Użyj <xref:System.Data.OracleClient.OracleDataReader> do uzyskania dostępu do danych i korzystać z kilku <xref:System.Data.OracleClient.OracleType> struktur, aby wyświetlić dane.</span><span class="sxs-lookup"><span data-stu-id="db723-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="db723-109">Tworzenie tabeli programu Oracle</span><span class="sxs-lookup"><span data-stu-id="db723-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="db723-110">W tym przykładzie tworzy tabelę bazy danych Oracle i ładuje je z danymi.</span><span class="sxs-lookup"><span data-stu-id="db723-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="db723-111">W tym przykładzie należy uruchomić przed uruchomieniem w następnym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="db723-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="db723-112">Trwa pobieranie danych z tabeli bazy danych Oracle</span><span class="sxs-lookup"><span data-stu-id="db723-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="db723-113">W tym przykładzie użyto **Element OracleDataReader** dostępu do danych i wykorzystuje kilka **typu OracleType** struktur, aby wyświetlić dane.</span><span class="sxs-lookup"><span data-stu-id="db723-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =   
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =   
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =   
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =   
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =   
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="db723-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db723-114">See Also</span></span>  
 [<span data-ttu-id="db723-115">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="db723-115">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="db723-116">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="db723-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
