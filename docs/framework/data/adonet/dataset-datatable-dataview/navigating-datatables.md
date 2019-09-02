---
title: Nawigowanie w elementach DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: b5837d647b72f8dd17c4a6d3664faf8976243d36
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204556"
---
# <a name="navigating-datatables"></a>Nawigowanie w elementach DataTable
Uzyskuje zawartość co najmniej jednego <xref:System.Data.DataTable> obiektu w postaci co najmniej jednego zestawu wyników tylko do odczytu. <xref:System.Data.DataTableReader>  
  
 Obiekt <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzony przy <xref:System.Data.DataSet.CreateDataReader%2A> użyciu metody. Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> Metoda przesuwa kursor do następnego zestawu wyników. Jest to proces tylko do przesyłania dalej. Nie można powrócić do poprzedniego zestawu wyników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `TestConstructor` Metoda tworzy dwa <xref:System.Data.DataTable> wystąpienia. Aby przedstawić ten Konstruktor dla <xref:System.Data.DataTableReader> klasy, przykład tworzy nowy **DataTableReader** na podstawie tablicy zawierającej dwie tabele DataTables i wykonuje prostą operację, drukując zawartość z pierwszych kilku kolumny do okna konsoli.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataTableReader](datatablereaders.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
