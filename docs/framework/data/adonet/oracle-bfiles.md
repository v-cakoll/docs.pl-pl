---
title: Oracle BFILEs
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: bb0a7dad2b7919130097ddd689739b8d17557ea1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758415"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="c19f0-102">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="c19f0-102">Oracle BFILEs</span></span>
<span data-ttu-id="c19f0-103">.NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleBFile> klasy, która jest używana do pracy z bazą danych Oracle <xref:System.Data.OracleClient.OracleType.BFile> — typ danych.</span><span class="sxs-lookup"><span data-stu-id="c19f0-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="c19f0-104">Oracle **BPLIK** ma typ danych Oracle **LOB** typ danych, który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="c19f0-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="c19f0-105">Oracle **BPLIK** różni się od innych Oracle **LOB** typy danych, ponieważ jego dane są przechowywane w pliku fizycznego w systemie operacyjnym, a nie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c19f0-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="c19f0-106">Należy pamiętać, że **BPLIK** — typ danych zapewnia dostęp do danych tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c19f0-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="c19f0-107">Inne właściwości **BPLIK** typ danych, który odróżniający go od **LOB** jego są — typ danych:</span><span class="sxs-lookup"><span data-stu-id="c19f0-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="c19f0-108">Zawiera dane bez struktury.</span><span class="sxs-lookup"><span data-stu-id="c19f0-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="c19f0-109">Obsługuje podziału po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="c19f0-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="c19f0-110">Używa odwoływać się do kopiowania semantyki.</span><span class="sxs-lookup"><span data-stu-id="c19f0-110">Uses reference copy semantics.</span></span> <span data-ttu-id="c19f0-111">Na przykład, jeśli operacja kopiowania na **BPLIK**, tylko **BPLIK** jest kopiowany Lokalizator (która jest odwołanie do pliku).</span><span class="sxs-lookup"><span data-stu-id="c19f0-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="c19f0-112">Dane w pliku nie zostaną skopiowane.</span><span class="sxs-lookup"><span data-stu-id="c19f0-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="c19f0-113">**BPLIK** typ danych powinien być używany dla odwołania do obiektów LOB, które są duże, dlatego nie praktyczne mają być przechowywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="c19f0-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="c19f0-114">Uczestniczy większe obciążenie klienta, serwera i komunikację, korzystając z **BPLIK** — typ danych w porównaniu z **LOB** — typ danych.</span><span class="sxs-lookup"><span data-stu-id="c19f0-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="c19f0-115">Bardziej wydajny dostęp do **BPLIK** Jeśli należy uzyskać niewielką ilość danych.</span><span class="sxs-lookup"><span data-stu-id="c19f0-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="c19f0-116">Jest bardziej wydajne dostępu obiektów LOB rezydentne bazy danych, gdy trzeba uzyskać całego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c19f0-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="c19f0-117">Każdy z systemem innym niż NULL **OracleBFile** obiekt jest skojarzony z dwoma obiektami, które określają lokalizację pliku fizycznego:</span><span class="sxs-lookup"><span data-stu-id="c19f0-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="c19f0-118">Obiekt Oracle katalogu, który jest alias bazy danych dla katalogu w systemie plików, a</span><span class="sxs-lookup"><span data-stu-id="c19f0-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="c19f0-119">Nazwa pliku źródłowego pliku fizycznego znajduje się w katalogu skojarzone z obiektu katalogu.</span><span class="sxs-lookup"><span data-stu-id="c19f0-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c19f0-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="c19f0-120">Example</span></span>  
 <span data-ttu-id="c19f0-121">W poniższym przykładzie C# pokazano, jak utworzyć **BPLIK** w oprogramowaniu Oracle tabeli, a następnie pobrać go w formie **OracleBFile** obiektu.</span><span class="sxs-lookup"><span data-stu-id="c19f0-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="c19f0-122">W przykładzie pokazano, za pomocą <xref:System.Data.OracleClient.OracleDataReader> obiektu i **OracleBFile** **wyszukiwania** i **odczytu** metody.</span><span class="sxs-lookup"><span data-stu-id="c19f0-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="c19f0-123">Należy pamiętać, aby można było korzystać z tej próbki, należy najpierw utworzyć katalog o nazwie "c:\\\bfiles" i plik o nazwie "MyFile.jpg" na serwerze programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="c19f0-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c19f0-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c19f0-124">See Also</span></span>  
 [<span data-ttu-id="c19f0-125">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c19f0-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="c19f0-126">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="c19f0-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
