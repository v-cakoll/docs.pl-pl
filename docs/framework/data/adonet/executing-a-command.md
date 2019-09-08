---
title: Wykonywanie polecenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: f749ea37e1655f006e4de26e7cb279b778fe4faf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795108"
---
# <a name="executing-a-command"></a>Wykonywanie polecenia
Każdy dostawca danych .NET Framework dołączony do .NET Framework ma własny obiekt polecenia, który dziedziczy z <xref:System.Data.Common.DbCommand>. Dostawca danych .NET Framework dla OLE DB zawiera <xref:System.Data.OleDb.OleDbCommand> obiekt, .NET Framework dostawca danych dla SQL Server <xref:System.Data.SqlClient.SqlCommand> zawiera obiekt, .NET Framework dostawca danych dla ODBC zawiera <xref:System.Data.Odbc.OdbcCommand> obiekt i .NET Framework Dostawca danych dla programu Oracle zawiera <xref:System.Data.OracleClient.OracleCommand> obiekt. Każdy z tych obiektów uwidacznia metody wykonywania poleceń na podstawie typu polecenia i żądanej wartości zwracanej, zgodnie z opisem w poniższej tabeli.  
  
|Polecenie|Wartość zwracana|  
|-------------|------------------|  
|`ExecuteReader`|Zwraca `DataReader` obiektu.|  
|`ExecuteScalar`|Zwraca pojedynczą wartość skalarną.|  
|`ExecuteNonQuery`|Wykonuje polecenie, które nie zwraca żadnych wierszy.|  
|`ExecuteXMLReader`|Zwraca wartość <xref:System.Xml.XmlReader>. Dostępne tylko dla `SqlCommand` obiektu.|  
  
 Każdy obiekt polecenia o jednoznacznie określonym typie obsługuje <xref:System.Data.CommandType> również Wyliczenie, które określa sposób interpretacji ciągu polecenia, zgodnie z opisem w poniższej tabeli.  
  
|CommandType|Opis|  
|-----------------|-----------------|  
|`Text`|Polecenie SQL definiujące instrukcje do wykonania w źródle danych.|  
|`StoredProcedure`|Nazwa procedury składowanej. Można użyć `Parameters` właściwości polecenia, aby uzyskać dostęp do parametrów wejściowych i wyjściowych oraz zwracanych wartości, niezależnie od tego `Execute` , która metoda jest wywoływana. W przypadku `ExecuteReader`używania wartości zwracane i parametry wyjściowe nie będą dostępne `DataReader` do momentu zamknięcia.|  
|`TableDirect`|Nazwa tabeli.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób tworzenia <xref:System.Data.SqlClient.SqlCommand> obiektu do wykonania procedury składowanej przez ustawienie jej właściwości. <xref:System.Data.SqlClient.SqlParameter> Obiekt jest używany do określenia parametru wejściowego procedury składowanej. Polecenie jest wykonywane przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody, a dane wyjściowe z programu <xref:System.Data.SqlClient.SqlDataReader> są wyświetlane w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Rozwiązywanie problemów z poleceniami  
 .NET Framework Dostawca danych do SQL Server dodaje liczniki wydajności, aby umożliwić wykrywanie sporadycznych problemów związanych z operacjami zakończonymi niepowodzeniem. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](performance-counters.md).  
  
## <a name="see-also"></a>Zobacz także

- [Polecenia i parametry](commands-and-parameters.md)
- [Elementy DataAdapter i DataReaders](dataadapters-and-datareaders.md)
- [Omówienie ADO.NET](ado-net-overview.md)
