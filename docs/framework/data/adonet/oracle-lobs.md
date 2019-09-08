---
title: Oracle LOB
ms.date: 03/30/2017
ms.assetid: 272e8e1e-a31f-475a-8c2a-ae8e1286bdab
ms.openlocfilehash: a52203ad62e8761897f7b2bef90f1915db9433f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783332"
---
# <a name="oracle-lobs"></a><span data-ttu-id="f579e-102">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="f579e-102">Oracle LOBs</span></span>
<span data-ttu-id="f579e-103">.NET Framework dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleLob> klasę, która jest używana do pracy z typami danych **LOB** firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="f579e-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle **LOB** data types.</span></span>  
  
 <span data-ttu-id="f579e-104">**OracleLob** może być jednym z następujących <xref:System.Data.OracleClient.OracleType> typów danych:</span><span class="sxs-lookup"><span data-stu-id="f579e-104">An **OracleLob** may be one of these <xref:System.Data.OracleClient.OracleType> data types:</span></span>  
  
|<span data-ttu-id="f579e-105">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f579e-105">Data type</span></span>|<span data-ttu-id="f579e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f579e-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f579e-107">**Obiekt blob**</span><span class="sxs-lookup"><span data-stu-id="f579e-107">**Blob**</span></span>|<span data-ttu-id="f579e-108">Typ danych **obiektu BLOB** Oracle zawierający dane binarne o maksymalnym rozmiarze wynoszącym 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="f579e-108">An Oracle **BLOB** data type that contains binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="f579e-109">To mapuje do **tablicy** typu **Byte**.</span><span class="sxs-lookup"><span data-stu-id="f579e-109">This maps to an **Array** of type **Byte**.</span></span>|  
|<span data-ttu-id="f579e-110">**Clob**</span><span class="sxs-lookup"><span data-stu-id="f579e-110">**Clob**</span></span>|<span data-ttu-id="f579e-111">Typ danych Oracle **obiektów CLOB** , który zawiera dane znakowe, na podstawie domyślnego zestawu znaków na serwerze z maksymalnym rozmiarem wynoszącym 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="f579e-111">An Oracle **CLOB** data type that contains character data, based on the default character set on the server, with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="f579e-112">To mapuje na **ciąg**.</span><span class="sxs-lookup"><span data-stu-id="f579e-112">This maps to **String**.</span></span>|  
|<span data-ttu-id="f579e-113">**NClob**</span><span class="sxs-lookup"><span data-stu-id="f579e-113">**NClob**</span></span>|<span data-ttu-id="f579e-114">Typ danych Oracle **NCLOB** , który zawiera dane znakowe, oparte na Narodowym zestawie znaków na serwerze o maksymalnym rozmiarze wynoszącym 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="f579e-114">An Oracle **NCLOB** data type that contains character data, based on the national character set on the server with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="f579e-115">To mapuje na **ciąg**.</span><span class="sxs-lookup"><span data-stu-id="f579e-115">This maps to **String**.</span></span>|  
  
 <span data-ttu-id="f579e-116">**OracleLob** różni się od <xref:System.Data.OracleClient.OracleBFile> w tym, że dane są przechowywane na serwerze, a nie w pliku fizycznym w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="f579e-116">An **OracleLob** differs from an <xref:System.Data.OracleClient.OracleBFile> in that the data is stored on the server instead of in a physical file in the operating system.</span></span> <span data-ttu-id="f579e-117">Może być również obiektem do odczytu i zapisu, w przeciwieństwie do **OracleBFile**, który jest zawsze tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f579e-117">It can also be a read-write object, unlike an **OracleBFile**, which is always read-only.</span></span>  
  
## <a name="creating-retrieving-and-writing-to-a-lob"></a><span data-ttu-id="f579e-118">Tworzenie, pobieranie i zapisywanie do obiektu LOB</span><span class="sxs-lookup"><span data-stu-id="f579e-118">Creating, Retrieving, and Writing to a LOB</span></span>  
 <span data-ttu-id="f579e-119">Poniższy C# przykład demonstruje, jak można utworzyć LOB w tabeli Oracle, a następnie pobrać i zapisać do nich w postaci obiektów **OracleLob** .</span><span class="sxs-lookup"><span data-stu-id="f579e-119">The following C# example demonstrates how you can create LOBs in an Oracle table, and then retrieve and write to them in the form of **OracleLob** objects.</span></span> <span data-ttu-id="f579e-120">W przykładzie pokazano użycie <xref:System.Data.OracleClient.OracleDataReader> obiektu i metody **odczytu** i **zapisu** **OracleLob** .</span><span class="sxs-lookup"><span data-stu-id="f579e-120">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleLob** **Read** and **Write** methods.</span></span> <span data-ttu-id="f579e-121">W przykładzie są stosowane typy danych **obiektów BLOB**, **obiektów CLOB**i **NCLOB** firmy Oracle.</span><span class="sxs-lookup"><span data-stu-id="f579e-121">The example uses Oracle **BLOB**, **CLOB**, and **NCLOB** data types.</span></span>  
  
```csharp  
using System;  
using System.IO;              
using System.Text;             
using System.Data;              
using System.Data.OracleClient;  
  
// LobExample  
public class LobExample  
{  
   public static int Main(string[] args)  
   {  
      //Create a connection.  
      OracleConnection conn = new OracleConnection(  
         "Data Source=Oracle8i;Integrated Security=yes");  
      using(conn)  
      {  
         //Open a connection.  
         conn.Open();  
         OracleCommand cmd = conn.CreateCommand();  
  
         //Create the table and schema.  
         CreateTable(cmd);  
  
         //Read example.  
         ReadLobExample(cmd);  
  
         //Write example  
         WriteLobExample(cmd);  
      }  
  
      return 1;  
   }  
  
   // ReadLobExample  
   public static void ReadLobExample(OracleCommand cmd)  
   {  
      int actual = 0;  
  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      // Select some data.  
      cmd.CommandText = "SELECT * FROM tablewithlobs";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         //Obtain the first row of data.  
         reader.Read();  
  
         //Obtain the LOBs (all 3 varieties).  
         OracleLob blob = reader.GetOracleLob(1);  
         OracleLob clob = reader.GetOracleLob(2);  
         OracleLob nclob = reader.GetOracleLob(3);  
  
         //Example - Reading binary data (in chunks).  
         byte[] buffer = new byte[100];  
         while((actual = blob.Read(buffer, 0, buffer.Length)) >0)  
            Console.WriteLine(blob.LobType + ".Read(" + buffer + ", " +   
              buffer.Length + ") => " + actual);  
  
         // Example - Reading CLOB/NCLOB data (in chunks).  
         // Note: You can read character data as raw Unicode bytes   
         // (using OracleLob.Read as in the above example).  
         // However, because the OracleLob object inherits directly   
         // from the .NET stream object,   
         // all the existing classes that manipluate streams can   
         // also be used. For example, the   
         // .NET StreamReader makes it easier to convert the raw bytes   
         // into actual characters.  
         StreamReader streamreader =   
           new StreamReader(clob, Encoding.Unicode);  
         char[] cbuffer = new char[100];  
         while((actual = streamreader.Read(cbuffer,   
           0, cbuffer.Length)) >0)  
            Console.WriteLine(clob.LobType + ".Read(  
              " + new string(cbuffer, 0, actual) + ", " +   
              cbuffer.Length + ") => " + actual);  
  
         // Example - Reading data (all at once).  
         // You could use StreamReader.ReadToEnd to obtain   
         // all the string data, or simply  
         // call OracleLob.Value to obtain a contiguous allocation   
         // of all the data.  
         Console.WriteLine(nclob.LobType + ".Value => " + nclob.Value);  
      }  
   }  
  
   // WriteLobExample  
   public static void WriteLobExample(OracleCommand cmd)  
   {  
      //Note: Updating LOB data requires a transaction.  
      cmd.Transaction = cmd.Connection.BeginTransaction();  
  
      // Select some data.  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      cmd.CommandText = "SELECT * FROM tablewithlobs FOR UPDATE";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         // Obtain the first row of data.  
         reader.Read();  
  
         // Obtain a LOB.  
         OracleLob blob = reader.GetOracleLob(1/*0:based ordinal*/);  
  
         // Perform any desired operations on the LOB   
         // (read, position, and so on).  
  
         // Example - Writing binary data (directly to the backend).  
         // To write, you can use any of the stream classes, or write  
         // raw binary data using   
         // the OracleLob write method. Writing character vs. binary   
         // is the same;  
         // however note that character is always in terms of   
         // Unicode byte counts  
         // (for example, even number of bytes - 2 bytes for every  
         // Unicode character).  
         byte[] buffer = new byte[100];  
         buffer[0] = 0xCC;  
         buffer[1] = 0xDD;  
         blob.Write(buffer, 0, 2);  
         blob.Position = 0;  
         Console.WriteLine(blob.LobType + ".Write(  
           " + buffer + ", 0, 2) => " + blob.Value);  
  
         // Example - Obtaining a temp LOB and copying data   
         // into it from another LOB.  
         OracleLob templob = CreateTempLob(cmd, blob.LobType);  
         long actual = blob.CopyTo(templob);  
         Console.WriteLine(blob.LobType + ".CopyTo(  
            " + templob.Value + ") => " + actual);  
  
         // Commit the transaction now that everything succeeded.  
         // Note: On error, Transaction.Dispose is called   
         // (from the using statement)  
         // and will automatically roll back the pending transaction.  
         cmd.Transaction.Commit();  
      }  
   }  
  
   // CreateTempLob  
   public static OracleLob CreateTempLob(  
     OracleCommand cmd, OracleType lobtype)  
   {  
      //Oracle server syntax to obtain a temporary LOB.  
      cmd.CommandText = "DECLARE A " + lobtype + "; "+  
                     "BEGIN "+  
                        "DBMS_LOB.CREATETEMPORARY(A, FALSE); "+  
                        ":LOC := A; "+  
                     "END;";  
  
      //Bind the LOB as an output parameter.  
      OracleParameter p = cmd.Parameters.Add("LOC", lobtype);  
      p.Direction = ParameterDirection.Output;  
  
      //Execute (to receive the output temporary LOB).  
      cmd.ExecuteNonQuery();  
  
      //Return the temporary LOB.  
      return (OracleLob)p.Value;  
   }  
  
   // CreateTable  
   public static void CreateTable(OracleCommand cmd)  
   {  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      try  
      {  
         cmd.CommandText   = "DROP TABLE tablewithlobs";  
         cmd.ExecuteNonQuery();  
      }  
      catch(Exception)  
      {  
      }  
  
      cmd.CommandText =   
        "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText =   
        "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
## <a name="creating-a-temporary-lob"></a><span data-ttu-id="f579e-122">Tworzenie tymczasowego obiektu LOB</span><span class="sxs-lookup"><span data-stu-id="f579e-122">Creating a Temporary LOB</span></span>  
 <span data-ttu-id="f579e-123">W poniższym C# przykładzie pokazano, jak utworzyć tymczasowy obiekt LOB.</span><span class="sxs-lookup"><span data-stu-id="f579e-123">The following C# example demonstrates how to create a temporary LOB.</span></span>  
  
```csharp  
OracleConnection conn = new OracleConnection(  
  "server=test8172; integrated security=yes;");  
conn.Open();  
  
OracleTransaction tx = conn.BeginTransaction();  
  
OracleCommand cmd = conn.CreateCommand();  
cmd.Transaction = tx;  
cmd.CommandText =   
  "declare xx blob; begin dbms_lob.createtemporary(  
  xx, false, 0); :tempblob := xx; end;";  
cmd.Parameters.Add(new OracleParameter("tempblob",  
  OracleType.Blob)).Direction = ParameterDirection.Output;  
cmd.ExecuteNonQuery();  
OracleLob tempLob = (OracleLob)cmd.Parameters[0].Value;  
tempLob.BeginBatch(OracleLobOpenMode.ReadWrite);  
tempLob.Write(tempbuff,0,tempbuff.Length);  
tempLob.EndBatch();  
cmd.Parameters.Clear();  
cmd.CommandText = "myTable.myProc";  
cmd.CommandType = CommandType.StoredProcedure;    
cmd.Parameters.Add(new OracleParameter(  
  "ImportDoc", OracleType.Blob)).Value = tempLob;  
cmd.ExecuteNonQuery();  
  
tx.Commit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="f579e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f579e-124">See also</span></span>

- [<span data-ttu-id="f579e-125">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f579e-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="f579e-126">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f579e-126">ADO.NET Overview</span></span>](ado-net-overview.md)
