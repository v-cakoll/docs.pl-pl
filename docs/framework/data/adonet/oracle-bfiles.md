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
# <a name="oracle-bfiles"></a>Oracle BFILE
.NET Framework dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleBFile> klasę, która jest używana do pracy z typem danych Oracle. <xref:System.Data.OracleClient.OracleType.BFile>  
  
 Typ danych Oracle **bInformacje** to typ danych **LOB** firmy Oracle, który zawiera odwołanie do danych binarnych o maksymalnym rozmiarze wynoszącym 4 gigabajty. Oprogramowanie Oracle **bInformacje** różni się od innych typów danych **LOB** Oracle w tym, że dane są przechowywane w pliku fizycznym w systemie operacyjnym, a nie na serwerze. Należy pamiętać, że typ danych **bInformacje** zapewnia dostęp tylko do odczytu do danych.  
  
 Inne cechy typu danych **bInformacje** odróżniające go od typu danych **LOB** to:  
  
- Zawiera dane bez struktury.  
  
- Obsługuje dzielenie fragmentów po stronie serwera.  
  
- Używa semantyki kopiowania odwołań. Na przykład jeśli wykonujesz operację kopiowania w pliku **bInformacje**, kopiowane jest tylko lokalizator **plików bInformacje** (który jest odwołaniem do pliku). Dane w pliku nie są kopiowane.  
  
 Typ danych **bInformacje** powinien być używany w przypadku przywołujących się do LOB o dużych rozmiarach, dlatego nie jest to praktyczne do przechowywania w bazie danych. W przypadku użycia typu danych " **bInformacje** " w porównaniu z typem danych **LOB** jest naliczana większa obciążenie klienta, serwera i komunikacji. Aby uzyskać niewielką ilość danych, bardziej wydajne jest uzyskanie dostępu do klasy **bInformacje** . W celu uzyskania całego obiektu bardziej wydajne jest uzyskanie dostępu do LOB rezydentów bazy danych.  
  
 Każdy obiekt **OracleBFile** o wartości innej niż null jest skojarzony z dwiema jednostkami, które definiują lokalizację bazowego pliku fizycznego:  
  
1. Obiekt katalogu Oracle, który jest aliasem bazy danych dla katalogu w systemie plików i  
  
2. Nazwa pliku podstawowego pliku, który znajduje się w katalogu skojarzonym z obiektem katalogu.  
  
## <a name="example"></a>Przykład  
 W poniższym C# przykładzie pokazano, jak można utworzyć plik **bInformacje** w tabeli Oracle, a następnie pobrać go w postaci obiektu **OracleBFile** . W przykładzie pokazano użycie <xref:System.Data.OracleClient.OracleDataReader> obiektu i metody **wyszukiwania** **OracleBFile** i **odczytu** . Należy pamiętać, że w celu użycia tego przykładu należy najpierw utworzyć katalog o nazwie "c:\\\bfiles" i pliku o nazwie "Moje pliki. jpg" na serwerze Oracle.  
  
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

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
