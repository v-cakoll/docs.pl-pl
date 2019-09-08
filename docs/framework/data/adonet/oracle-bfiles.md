---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 214140bb8fcf43154b014ea3db609d355a27af7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794626"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="19d55-102">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="19d55-102">Oracle BFILEs</span></span>
<span data-ttu-id="19d55-103">.NET Framework dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleBFile> klasę, która jest używana do pracy z typem danych Oracle. <xref:System.Data.OracleClient.OracleType.BFile></span><span class="sxs-lookup"><span data-stu-id="19d55-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="19d55-104">Typ danych Oracle **bInformacje** to typ danych **LOB** firmy Oracle, który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze wynoszącym 4 gigabajty.</span><span class="sxs-lookup"><span data-stu-id="19d55-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="19d55-105">Oprogramowanie Oracle **bInformacje** różni się od innych typów danych **LOB** Oracle w tym, że dane są przechowywane w pliku fizycznym w systemie operacyjnym, a nie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="19d55-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="19d55-106">Należy pamiętać, że typ danych **bInformacje** zapewnia dostęp tylko do odczytu do danych.</span><span class="sxs-lookup"><span data-stu-id="19d55-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="19d55-107">Inne cechy typu danych **bInformacje** odróżniające go od typu danych **LOB** to:</span><span class="sxs-lookup"><span data-stu-id="19d55-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="19d55-108">Zawiera dane bez struktury.</span><span class="sxs-lookup"><span data-stu-id="19d55-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="19d55-109">Obsługuje dzielenie fragmentów po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="19d55-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="19d55-110">Używa semantyki kopiowania odwołań.</span><span class="sxs-lookup"><span data-stu-id="19d55-110">Uses reference copy semantics.</span></span> <span data-ttu-id="19d55-111">Na przykład jeśli wykonujesz operację kopiowania w pliku **bInformacje**, kopiowane jest tylko lokalizator **plików bInformacje** (który jest odwołaniem do pliku).</span><span class="sxs-lookup"><span data-stu-id="19d55-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="19d55-112">Dane w pliku nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="19d55-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="19d55-113">Typ danych **bInformacje** powinien być używany w przypadku przywołujących się do LOB o dużych rozmiarach, dlatego nie jest to praktyczne do przechowywania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="19d55-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="19d55-114">W przypadku użycia typu danych " **bInformacje** " w porównaniu z typem danych **LOB** jest naliczana większa obciążenie klienta, serwera i komunikacji.</span><span class="sxs-lookup"><span data-stu-id="19d55-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="19d55-115">Aby uzyskać niewielką ilość danych, bardziej wydajne jest uzyskanie dostępu do klasy **bInformacje** .</span><span class="sxs-lookup"><span data-stu-id="19d55-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="19d55-116">W celu uzyskania całego obiektu bardziej wydajne jest uzyskanie dostępu do LOB rezydentów bazy danych.</span><span class="sxs-lookup"><span data-stu-id="19d55-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="19d55-117">Każdy obiekt **OracleBFile** o wartości innej niż null jest skojarzony z dwiema jednostkami, które definiują lokalizację bazowego pliku fizycznego:</span><span class="sxs-lookup"><span data-stu-id="19d55-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="19d55-118">Obiekt katalogu Oracle, który jest aliasem bazy danych dla katalogu w systemie plików i</span><span class="sxs-lookup"><span data-stu-id="19d55-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="19d55-119">Nazwa pliku podstawowego pliku, który znajduje się w katalogu skojarzonym z obiektem katalogu.</span><span class="sxs-lookup"><span data-stu-id="19d55-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19d55-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="19d55-120">Example</span></span>  
 <span data-ttu-id="19d55-121">W poniższym C# przykładzie pokazano, jak można utworzyć plik **bInformacje** w tabeli Oracle, a następnie pobrać go w postaci obiektu **OracleBFile** .</span><span class="sxs-lookup"><span data-stu-id="19d55-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="19d55-122">W przykładzie pokazano użycie <xref:System.Data.OracleClient.OracleDataReader> obiektu i metody **wyszukiwania** **OracleBFile** i **odczytu** .</span><span class="sxs-lookup"><span data-stu-id="19d55-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="19d55-123">Należy pamiętać, że w celu użycia tego przykładu należy najpierw utworzyć katalog o nazwie "c:\\\bfiles" i pliku o nazwie "Moje pliki. jpg" na serwerze Oracle.</span><span class="sxs-lookup"><span data-stu-id="19d55-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19d55-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19d55-124">See also</span></span>

- [<span data-ttu-id="19d55-125">Oracle i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19d55-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="19d55-126">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19d55-126">ADO.NET Overview</span></span>](ado-net-overview.md)
