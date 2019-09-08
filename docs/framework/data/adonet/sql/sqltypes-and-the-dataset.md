---
title: Właściwość SqlTypes i zestaw danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791500"
---
# <a name="sqltypes-and-the-dataset"></a>Właściwość SqlTypes i zestaw danych
`DataSet` W<xref:System.Data.SqlTypes> systemie ADO.NET 2,0 wprowadzono rozszerzoną obsługę typów w przestrzeni nazw. Typy w programie <xref:System.Data.SqlTypes> zaprojektowano w celu zapewnienia typów danych z tą samą semantyką i dokładnością jako typami danych w bazie danych SQL Server. Każdy typ danych w <xref:System.Data.SqlTypes> ma odpowiedni typ danych w SQL Server, z tą samą reprezentacją danych.  
  
 Użycie <xref:System.Data.SqlTypes> bezpośrednio<xref:System.Data.DataSet> w przystawce przydaje kilka korzyści podczas pracy z SQL Server typami danych. <xref:System.Data.SqlTypes>obsługuje te same semantykę co SQL Server natywne typy danych. Określanie jednej z <xref:System.Data.SqlTypes> w definicji a <xref:System.Data.DataColumn> eliminuje utratę dokładności, która może wystąpić podczas konwertowania dziesiętnych lub liczbowych typów danych na jeden z typów danych środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataTable> obiekt, jawnie <xref:System.Data.DataColumn> definiując typy danych przy użyciu <xref:System.Data.SqlTypes> zamiast typów CLR. Kod wypełnia <xref:System.Data.DataTable> dane z tabeli Sales. SalesOrderDetail w bazie danych AdventureWorks w SQL Server. Dane wyjściowe wyświetlane w oknie konsoli programu pokazują typ danych każdej kolumny i wartości pobrane z SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
