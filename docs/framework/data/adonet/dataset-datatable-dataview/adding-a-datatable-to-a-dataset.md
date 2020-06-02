---
title: Dodawanie elementu DataTable do elementu DataSet
description: Zapoznaj się z tym przykładowym kodem, aby dowiedzieć się, jak utworzyć obiekty DataTable i dodać je do istniejącego zestawu danych w ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 42bd36b394de560884a2ec607f4cbc65d1171e4e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286963"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Dodawanie elementu DataTable do elementu DataSet
ADO.NET umożliwia tworzenie <xref:System.Data.DataTable> obiektów i dodawanie ich do istniejącej <xref:System.Data.DataSet> . Można ustawić informacje o ograniczeniach dla elementu przy <xref:System.Data.DataTable> użyciu <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataColumn.Unique%2A> właściwości i.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataSet> , dodaje nowy <xref:System.Data.DataTable> obiekt do <xref:System.Data.DataSet> , a następnie dodaje trzy <xref:System.Data.DataColumn> obiekty do tabeli. Na koniec kod ustawia jedną kolumnę jako kolumnę klucza podstawowego.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozróżnianie wielkości liter  
 Co najmniej dwie tabele lub relacje o tej samej nazwie, ale różne wielkości liter, mogą znajdować się w <xref:System.Data.DataSet> . W takich przypadkach odwołania według nazwy do tabel i relacji uwzględniają wielkość liter. Na przykład, jeśli <xref:System.Data.DataSet> **zestaw danych** zawiera tabele **Tabela1** i **Tabela1**, należy odwołać się do **Tabela1** według nazwy jako **DataSet. tabele ["Tabela1"]** i **Tabela1** jako **DataSet. Tables ["Tabela1"]**. Próba odwołująca się do jednej z tabel jako **DataSet. tabele ["Tabela1"]** wygenerują wyjątek.  
  
 Zachowanie z rozróżnianiem wielkości liter nie ma zastosowania, jeśli tylko jedna tabela lub relacja ma określoną nazwę. Na przykład, jeśli <xref:System.Data.DataSet> ma tylko **Tabela1**, można odwoływać się do niego przy użyciu **zestawu danych. tabele ["Tabela1"]**.  
  
> [!NOTE]
> <xref:System.Data.DataSet.CaseSensitive%2A>Właściwość nie <xref:System.Data.DataSet> ma wpływu na to zachowanie. <xref:System.Data.DataSet.CaseSensitive%2A>Właściwość ma zastosowanie do danych w <xref:System.Data.DataSet> i ma wpływ na sortowanie, wyszukiwanie, filtrowanie, wymuszanie ograniczeń itd.  
  
## <a name="namespace-support"></a>Obsługa przestrzeni nazw  
 W wersjach programu ADO.NET starszej niż 2,0, dwie tabele nie mogły mieć takiej samej nazwy, nawet jeśli znajdują się w różnych przestrzeniach nazw. To ograniczenie zostało usunięte w ADO.NET 2,0. <xref:System.Data.DataSet>Może zawierać dwie tabele, które mają taką samą <xref:System.Data.DataTable.TableName%2A> wartość właściwości, ale różne <xref:System.Data.DataTable.Namespace%2A> wartości właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
