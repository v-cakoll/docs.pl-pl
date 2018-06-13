---
title: Wykonywanie polecenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: 5ffa32b13330d61e450a42e35b933ce05d69b041
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765181"
---
# <a name="executing-a-command"></a>Wykonywanie polecenia
Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma własną obiektu polecenia, która dziedziczy <xref:System.Data.Common.DbCommand>. .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiekt dostawcy danych programu .NET Framework dla programu SQL Server zawiera <xref:System.Data.SqlClient.SqlCommand> obiekt dostawcy danych programu .NET Framework dla ODBC obejmuje <xref:System.Data.Odbc.OdbcCommand> obiektu i .NET Framework Dostawca danych dla Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiektu. Każdy z tych obiektów udostępnia metody wykonywania poleceń na podstawie typu polecenia i żądaną wartość zwracaną, zgodnie z opisem w poniższej tabeli.  
  
|Polecenie|Wartość zwracana|  
|-------------|------------------|  
|`ExecuteReader`|Zwraca `DataReader` obiektu.|  
|`ExecuteScalar`|Zwraca pojedynczą wartość skalarną.|  
|`ExecuteNonQuery`|Wykonuje polecenia, która nie zwraca żadnych wierszy.|  
|`ExecuteXMLReader`|Zwraca <xref:System.Xml.XmlReader>. Dostępne dla `SqlCommand` tylko obiekt.|  
  
 Każdy obiekt polecenia jednoznacznie obsługuje również <xref:System.Data.CommandType> wyliczenie określający, jak ciąg polecenia jest interpretowany, zgodnie z opisem w poniższej tabeli.  
  
|Obiekt CommandType|Opis|  
|-----------------|-----------------|  
|`Text`|Polecenie SQL definiujący instrukcje mają być wykonane w źródle danych.|  
|`StoredProcedure`|Nazwa procedury składowanej. Można użyć `Parameters` właściwości polecenia dostępu do parametrów wejściowych i wyjściowych i wartości zwracane, niezależnie od tego, który `Execute` metoda jest wywoływana. Korzystając z `ExecuteReader`, ani zwracać wartości i parametry wyjściowe nie są dostępne do `DataReader` jest zamknięty.|  
|`TableDirect`|Nazwa tabeli.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Data.SqlClient.SqlCommand> obiekt, aby wykonać procedurę składowaną przez ustawienie jej właściwości. A <xref:System.Data.SqlClient.SqlParameter> obiekt jest używany do określenia parametru wejściowego procedury składowanej. Polecenie zostanie wykonane przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> — metoda i dane wyjściowe z <xref:System.Data.SqlClient.SqlDataReader> jest wyświetlany w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Rozwiązywanie problemów z poleceń  
 .NET Framework Data Provider for SQL Server dodaje liczniki wydajności, które umożliwiają wykrywanie sporadyczne problemy związane z wykonania polecenia nie powiodło się. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Praca z DataReaders](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
