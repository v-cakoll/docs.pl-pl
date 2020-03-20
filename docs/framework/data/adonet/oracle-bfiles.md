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
# <a name="oracle-bfiles"></a>Oracle BFILE
Dostawca danych .NET Framework dla <xref:System.Data.OracleClient.OracleBFile> Oracle obejmuje klasę, która <xref:System.Data.OracleClient.OracleType.BFile> jest używana do pracy z typem danych Oracle.  
  
 Typ danych Oracle **BFILE** to typ danych Oracle **LOB,** który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze 4 gigabajtów. Oracle **BFILE** różni się od innych typów danych Oracle **LOB** tym, że jego dane są przechowywane w pliku fizycznym w systemie operacyjnym, a nie na serwerze. Należy zauważyć, że typ danych **BFILE** zapewnia dostęp tylko do odczytu do danych.  
  
 Inne cechy typu danych **BFILE,** które odróżniają go od typu danych **LOB,** to, że:  
  
- Zawiera dane nieustrukturyzowane.  
  
- Obsługuje fragmentowanie po stronie serwera.  
  
- Używa semantyki kopii odwołań. Na przykład, jeśli wykonujesz operację kopiowania na **BFILE,** kopiowany jest tylko lokalizator **BFILE** (który jest odwołaniem do pliku). Dane w pliku nie są kopiowane.  
  
 Typ danych **BFILE** powinny służyć do odwoływania się do lobs, które są duże rozmiary i dlatego nie praktyczne do przechowywania w bazie danych. Więcej klienta, serwera i komunikacji obciążenie jest zaangażowany podczas korzystania z typu danych **BFILE** w porównaniu z typem danych **LOB.** Jest bardziej wydajny dostęp do **pliku BFILE,** jeśli wystarczy uzyskać niewielką ilość danych. Jest bardziej efektywny dostęp do lobs rezydenta bazy danych, jeśli trzeba uzyskać cały obiekt.  
  
 Każdy obiekt **OracleBFile** innej niż NULL jest skojarzony z dwoma encjami, które definiują lokalizację bazowego pliku fizycznego:  
  
1. Obiekt Oracle DIRECTORY, który jest aliasem bazy danych dla katalogu w systemie plików, oraz  
  
2. Nazwa pliku źródłowego pliku fizycznego, który znajduje się w katalogu skojarzonym z obiektem DIRECTORY.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład języka C# pokazuje, jak można utworzyć **BFILE** w tabeli Oracle, a następnie pobrać go w postaci **obiektu OracleBFile.** W przykładzie pokazano <xref:System.Data.OracleClient.OracleDataReader> przy użyciu obiektu i **OracleBFile** **Seek** i **Read** metody. Należy zauważyć, że aby użyć tego przykładu, należy najpierw\\utworzyć katalog o nazwie "c: \bfiles" i plik o nazwie "MyFile.jpg" na serwerze Oracle.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
