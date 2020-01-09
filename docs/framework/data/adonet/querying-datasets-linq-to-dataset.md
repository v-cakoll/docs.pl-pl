---
title: Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634784"
---
# <a name="querying-datasets-linq-to-dataset"></a>Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)
Po wypełnieniu <xref:System.Data.DataSet> obiektu za pomocą danych można rozpocząć wykonywanie zapytania. Formułowanie zapytań w LINQ to DataSet jest podobne do korzystania z funkcji CLR (Language-Integrated Query) dla innych źródeł danych obsługujących LINQ. Należy jednak pamiętać, że w przypadku korzystania z zapytań LINQ w obiekcie <xref:System.Data.DataSet> jest wysyłana kwerenda wyliczenia obiektów <xref:System.Data.DataRow> zamiast wyliczenia typu niestandardowego. Oznacza to, że można użyć dowolnego z elementów członkowskich klasy <xref:System.Data.DataRow> w zapytaniach LINQ. Dzięki temu można tworzyć rozbudowane, złożone zapytania.  
  
 Podobnie jak w przypadku innych implementacji LINQ, można utworzyć zapytania LINQ to DataSet w dwóch różnych formularzach: składni wyrażeń zapytania i składni zapytania opartego na metodzie. Można użyć składni wyrażeń zapytania lub składni zapytania opartej na metodzie, aby wykonywać zapytania dotyczące pojedynczych tabel w <xref:System.Data.DataSet>, w przypadku wielu tabel w <xref:System.Data.DataSet>lub w odniesieniu do tabel w określonym <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania jednotabelowe](single-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań pojedynczej tabeli.  
  
 [Zapytania wielotabelowe](cross-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań między tabelami.  
  
 [Wykonywanie zapytania do typizowanych zestawów danych](querying-typed-datasets.md)  
 Opisuje sposób wykonywania zapytań dotyczących wpisanych obiektów <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
