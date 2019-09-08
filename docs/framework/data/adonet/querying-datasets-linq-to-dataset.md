---
title: Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783048"
---
# <a name="querying-datasets-linq-to-dataset"></a>Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)
Po wypełnieniu <xref:System.Data.DataSet> obiektu danymi można rozpocząć wykonywanie zapytania. Formułowanie zapytań w LINQ to DataSet jest podobne do użycia [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] z innymi [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]źródłami danych. Należy jednak pamiętać, że w przypadku używania [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytań <xref:System.Data.DataSet> względem obiektu, który wykonuje <xref:System.Data.DataRow> zapytanie o Wyliczenie obiektów, zamiast wyliczania typu niestandardowego. Oznacza to, że można użyć dowolnego z elementów członkowskich <xref:System.Data.DataRow> klasy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] w zapytaniach. Pozwala to na tworzenie rozbudowanych, złożonych zapytań.  
  
 Podobnie jak w przypadku innych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]implementacji programu, można utworzyć zapytania LINQ to DataSet w dwóch różnych formularzach: składni wyrażeń zapytania i składni zapytania opartego na metodzie. Można użyć składni wyrażeń zapytania lub składni zapytania opartej na metodzie <xref:System.Data.DataSet>, aby wykonywać zapytania dotyczące pojedynczych tabel w, względem wielu tabel <xref:System.Data.DataSet>w, lub względem tabel w określonym typie <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania jednotabelowe](single-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań pojedynczej tabeli.  
  
 [Zapytania wielotabelowe](cross-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań między tabelami.  
  
 [Wykonywanie zapytania do typizowanych zestawów danych](querying-typed-datasets.md)  
 Opisuje sposób wykonywania zapytań względem <xref:System.Data.DataSet> wpisanych obiektów.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
