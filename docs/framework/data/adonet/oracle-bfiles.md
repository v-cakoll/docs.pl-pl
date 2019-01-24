---
title: Oracle bFile
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 825cb9eb4bdb54509c8ca3c20db4dade8b3ece73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677241"
---
# <a name="oracle-bfiles"></a>Oracle bFile
.NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleBFile> klasę, która zostanie użyta do pracy z bazą danych Oracle <xref:System.Data.OracleClient.OracleType.BFile> typu danych.  
  
 Oracle **BPLIK** ma typ danych Oracle **LOB** typ danych, który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze 4 gigabajty. Oracle **BPLIK** różni się od innych Oracle **LOB** typy danych, w tym jego dane są przechowywane w pliku fizycznego w systemie operacyjnym, a nie na serwerze. Należy pamiętać, że **BPLIK** — typ danych zapewnia dostęp do danych tylko do odczytu.  
  
 Pozostałe właściwości **BPLIK** typu danych, które odróżnia go od **LOB** typ danych to że:  
  
-   Zawiera dane bez określonej struktury.  
  
-   Obsługuje segmentu po stronie serwera.  
  
-   Zastosowań odwoływać się do kopiowania semantyki. Na przykład, jeśli operacja kopiowania na **BPLIK**, tylko **BPLIK** Lokalizator (jest to odwołanie do pliku) są kopiowane. Dane w pliku nie jest kopiowany.  
  
 **BPLIK** typu danych, należy użyć do odwoływania się do obiektów LOB, które są duże i dlatego nie jest to praktyczne do przechowywania w bazie danych. Większe koszty komunikacji, serwerów i klientów jest zaangażowana w przypadku korzystania z **BPLIK** typu danych w porównaniu z **LOB** typu danych. Jest bardziej wydajne, aby uzyskać dostęp do **BPLIK** Jeśli potrzebujesz uzyskać niewielką ilość danych. Jest bardziej efektywne i uzyskać dostęp do obiektów LOB rezydentne bazy danych, gdy trzeba uzyskać cały obiekt.  
  
 Każda inna niż NULL **OracleBFile** obiekt jest skojarzony z dwiema jednostkami, które określają lokalizację podstawowy plik fizyczny:  
  
1.  Obiekt bazy danych Oracle katalogu, który jest alias bazy dla katalogu w systemie plików, a  
  
2.  Nazwa pliku bazowego fizycznym pliku, który znajduje się w katalogu, który został skojarzony z obiektem katalogu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie C# pokazano, jak utworzyć **BPLIK** Oracle tabeli, a następnie pobrać jednego w formie **OracleBFile** obiektu. W przykładzie pokazano, za pomocą <xref:System.Data.OracleClient.OracleDataReader> obiektu i **OracleBFile** **Seek** i **odczytu** metody. Należy pamiętać, aby można było korzystać z tej próbki, należy najpierw utworzyć katalog o nazwie "c:\\\bfiles" oraz plik o nazwie "MyFile.jpg" na serwerze bazy danych Oracle.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
