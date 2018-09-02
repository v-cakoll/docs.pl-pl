---
title: Oracle bFile
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 683b4a9be826e1d0d4ee354fada10168d833e3d7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398793"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="13362-102">Oracle bFile</span><span class="sxs-lookup"><span data-stu-id="13362-102">Oracle BFILEs</span></span>
<span data-ttu-id="13362-103">.NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleBFile> klasę, która zostanie użyta do pracy z bazą danych Oracle <xref:System.Data.OracleClient.OracleType.BFile> typu danych.</span><span class="sxs-lookup"><span data-stu-id="13362-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="13362-104">Oracle **BPLIK** ma typ danych Oracle **LOB** typ danych, który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="13362-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="13362-105">Oracle **BPLIK** różni się od innych Oracle **LOB** typy danych, w tym jego dane są przechowywane w pliku fizycznego w systemie operacyjnym, a nie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="13362-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="13362-106">Należy pamiętać, że **BPLIK** — typ danych zapewnia dostęp do danych tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="13362-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="13362-107">Pozostałe właściwości **BPLIK** typu danych, które odróżnia go od **LOB** typ danych to że:</span><span class="sxs-lookup"><span data-stu-id="13362-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="13362-108">Zawiera dane bez określonej struktury.</span><span class="sxs-lookup"><span data-stu-id="13362-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="13362-109">Obsługuje segmentu po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="13362-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="13362-110">Zastosowań odwoływać się do kopiowania semantyki.</span><span class="sxs-lookup"><span data-stu-id="13362-110">Uses reference copy semantics.</span></span> <span data-ttu-id="13362-111">Na przykład, jeśli operacja kopiowania na **BPLIK**, tylko **BPLIK** Lokalizator (jest to odwołanie do pliku) są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="13362-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="13362-112">Dane w pliku nie jest kopiowany.</span><span class="sxs-lookup"><span data-stu-id="13362-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="13362-113">**BPLIK** typu danych, należy użyć do odwoływania się do obiektów LOB, które są duże i dlatego nie jest to praktyczne do przechowywania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="13362-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="13362-114">Większe koszty komunikacji, serwerów i klientów jest zaangażowana w przypadku korzystania z **BPLIK** typu danych w porównaniu z **LOB** typu danych.</span><span class="sxs-lookup"><span data-stu-id="13362-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="13362-115">Jest bardziej wydajne, aby uzyskać dostęp do **BPLIK** Jeśli potrzebujesz uzyskać niewielką ilość danych.</span><span class="sxs-lookup"><span data-stu-id="13362-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="13362-116">Jest bardziej efektywne i uzyskać dostęp do obiektów LOB rezydentne bazy danych, gdy trzeba uzyskać cały obiekt.</span><span class="sxs-lookup"><span data-stu-id="13362-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="13362-117">Każda inna niż NULL **OracleBFile** obiekt jest skojarzony z dwiema jednostkami, które określają lokalizację podstawowy plik fizyczny:</span><span class="sxs-lookup"><span data-stu-id="13362-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="13362-118">Obiekt bazy danych Oracle katalogu, który jest alias bazy dla katalogu w systemie plików, a</span><span class="sxs-lookup"><span data-stu-id="13362-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="13362-119">Nazwa pliku bazowego fizycznym pliku, który znajduje się w katalogu, który został skojarzony z obiektem katalogu.</span><span class="sxs-lookup"><span data-stu-id="13362-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13362-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="13362-120">Example</span></span>  
 <span data-ttu-id="13362-121">W poniższym przykładzie C# pokazano, jak utworzyć **BPLIK** Oracle tabeli, a następnie pobrać jednego w formie **OracleBFile** obiektu.</span><span class="sxs-lookup"><span data-stu-id="13362-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="13362-122">W przykładzie pokazano, za pomocą <xref:System.Data.OracleClient.OracleDataReader> obiektu i **OracleBFile** **Seek** i **odczytu** metody.</span><span class="sxs-lookup"><span data-stu-id="13362-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="13362-123">Należy pamiętać, aby można było korzystać z tej próbki, należy najpierw utworzyć katalog o nazwie "c:\\\bfiles" oraz plik o nazwie "MyFile.jpg" na serwerze bazy danych Oracle.</span><span class="sxs-lookup"><span data-stu-id="13362-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13362-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13362-124">See Also</span></span>  
 [<span data-ttu-id="13362-125">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="13362-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="13362-126">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="13362-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
