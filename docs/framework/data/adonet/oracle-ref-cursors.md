---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7cd29a6a20015c7ce4475b0211cb07f7ee78b530
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794874"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
.NET Framework Dostawca danych dla programu Oracle obsługuje typ danych **Cursor ref** firmy Oracle. Gdy dostawca danych jest używany do pracy z kursorami REF Oracle, należy wziąć pod uwagę następujące zachowania.  
  
> [!NOTE]
> Niektóre zachowania różnią się od tych Microsoft OLE DB Provider dla Oracle (MSDAORA I).  
  
- Ze względu na wydajność Dostawca danych dla programu Oracle nie wiąże się automatycznie z typem danych **kursora referencyjnego** , tak jak MSDAORA i, chyba że jawnie je określisz.  
  
- Dostawca danych nie obsługuje żadnych sekwencji unikowych ODBC, w tym kontrolki ucieczki {zestaw wyników} służącej do określania parametrów REF CURSOR.  
  
- Aby wykonać procedurę przechowywaną, która <xref:System.Data.OracleClient.OracleParameterCollection> zwraca kursory ref, należy zdefiniować parametry w <xref:System.Data.OracleClient.OracleType> z **kursorem** i <xref:System.Data.OracleClient.OracleParameter.Direction%2A> **a.** Dostawca danych obsługuje Powiązywanie kursorów REFERENCYJNych jako parametrów wyjściowych. Dostawca nie obsługuje REFERENCYJNych kursorów jako parametrów wejściowych.  
  
- <xref:System.Data.OracleClient.OracleDataReader> Uzyskanie z wartości parametru nie jest obsługiwane. Wartości są typu <xref:System.DBNull> po wykonaniu polecenia.  
  
- Jedyną wartością wyliczenia **CommandBehavior** , która działa z kursorami ref (na przykład gdy wywoływanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) jest **CloseConnection**; wszystkie pozostałe są ignorowane.  
  
- Kolejność kursorów REF w **OracleDataReader** zależy od kolejności parametrów w **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Właściwość jest ignorowana.  
  
- Typ danych **tabeli** pl/SQL nie jest obsługiwany. Jednak kursory REF są bardziej wydajne. Jeśli musisz użyć typu danych **tabeli** , użyj OLE DB .NET Dostawca danych z msdaora i.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykłady REF CURSOR](ref-cursor-examples.md)  
 Zawiera trzy przykłady, które demonstrują korzystanie z kursorów REF.  
  
 [Parametry kursora REF CURSOR w OracleDataReader](ref-cursor-parameters-in-an-oracledatareader.md)  
 Pokazuje, jak wykonać procedurę składowaną PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako **OracleDataReader**.  
  
 [Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](retrieving-data-from-multiple-ref-cursors.md)  
 Demonstruje sposób wykonywania procedury składowanej PL/SQL, która zwraca dwa parametry REF CURSOR i odczytuje wartości przy użyciu **OracleDataReader**.  
  
 [Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Demonstruje sposób wykonywania procedury składowanej pl/SQL, która zwraca dwa parametry kursora ref, i wypełnia <xref:System.Data.DataSet> z zwracanymi wierszami.  
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
