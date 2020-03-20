---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149443"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="3c8f8-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="3c8f8-102">Oracle BFILEs</span></span>
<span data-ttu-id="3c8f8-103">Dostawca danych .NET Framework dla <xref:System.Data.OracleClient.OracleBFile> Oracle obejmuje klasę, która <xref:System.Data.OracleClient.OracleType.BFile> jest używana do pracy z typem danych Oracle.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="3c8f8-104">Typ danych Oracle **BFILE** to typ danych Oracle **LOB,** który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze 4 gigabajtów.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="3c8f8-105">Oracle **BFILE** różni się od innych typów danych Oracle **LOB** tym, że jego dane są przechowywane w pliku fizycznym w systemie operacyjnym, a nie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="3c8f8-106">Należy zauważyć, że typ danych **BFILE** zapewnia dostęp tylko do odczytu do danych.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="3c8f8-107">Inne cechy typu danych **BFILE,** które odróżniają go od typu danych **LOB,** to, że:</span><span class="sxs-lookup"><span data-stu-id="3c8f8-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="3c8f8-108">Zawiera dane nieustrukturyzowane.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="3c8f8-109">Obsługuje fragmentowanie po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="3c8f8-110">Używa semantyki kopii odwołań.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-110">Uses reference copy semantics.</span></span> <span data-ttu-id="3c8f8-111">Na przykład, jeśli wykonujesz operację kopiowania na **BFILE,** kopiowany jest tylko lokalizator **BFILE** (który jest odwołaniem do pliku).</span><span class="sxs-lookup"><span data-stu-id="3c8f8-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="3c8f8-112">Dane w pliku nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="3c8f8-113">Typ danych **BFILE** powinny służyć do odwoływania się do lobs, które są duże rozmiary i dlatego nie praktyczne do przechowywania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="3c8f8-114">Więcej klienta, serwera i komunikacji obciążenie jest zaangażowany podczas korzystania z typu danych **BFILE** w porównaniu z typem danych **LOB.**</span><span class="sxs-lookup"><span data-stu-id="3c8f8-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="3c8f8-115">Jest bardziej wydajny dostęp do **pliku BFILE,** jeśli wystarczy uzyskać niewielką ilość danych.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="3c8f8-116">Jest bardziej efektywny dostęp do lobs rezydenta bazy danych, jeśli trzeba uzyskać cały obiekt.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="3c8f8-117">Każdy obiekt **OracleBFile** innej niż NULL jest skojarzony z dwoma encjami, które definiują lokalizację bazowego pliku fizycznego:</span><span class="sxs-lookup"><span data-stu-id="3c8f8-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="3c8f8-118">Obiekt Oracle DIRECTORY, który jest aliasem bazy danych dla katalogu w systemie plików, oraz</span><span class="sxs-lookup"><span data-stu-id="3c8f8-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="3c8f8-119">Nazwa pliku źródłowego pliku fizycznego, który znajduje się w katalogu skojarzonym z obiektem DIRECTORY.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c8f8-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c8f8-120">Example</span></span>  
 <span data-ttu-id="3c8f8-121">Poniższy przykład języka C# pokazuje, jak można utworzyć **BFILE** w tabeli Oracle, a następnie pobrać go w postaci **obiektu OracleBFile.**</span><span class="sxs-lookup"><span data-stu-id="3c8f8-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="3c8f8-122">W przykładzie pokazano <xref:System.Data.OracleClient.OracleDataReader> przy użyciu obiektu i **OracleBFile** **Seek** i **Read** metody.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="3c8f8-123">Należy zauważyć, że aby użyć tego przykładu, należy najpierw\\utworzyć katalog o nazwie "c: \bfiles" i plik o nazwie "MyFile.jpg" na serwerze Oracle.</span><span class="sxs-lookup"><span data-stu-id="3c8f8-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c8f8-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c8f8-124">See also</span></span>

- [<span data-ttu-id="3c8f8-125">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c8f8-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="3c8f8-126">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c8f8-126">ADO.NET Overview</span></span>](ado-net-overview.md)
