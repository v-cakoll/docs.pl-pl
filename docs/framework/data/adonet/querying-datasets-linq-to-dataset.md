---
title: Podczas badania zestawów danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: ec4ee345835294499f7ac9f665a9b79e2efc0f64
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504661"
---
# <a name="querying-datasets-linq-to-dataset"></a>Podczas badania zestawów danych (LINQ to DataSet)
Po <xref:System.Data.DataSet> obiektu została wypełniona danymi, można rozpocząć, badając ją. Formułowanie zapytania za pomocą LINQ to DataSet jest podobne do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] względem innych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]— włączone źródeł danych. Należy jednak pamiętać, że gdy używasz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytań <xref:System.Data.DataSet> obiektu jest wykonywane zapytanie wyliczenie <xref:System.Data.DataRow> obiekty, zamiast wyliczenie typu niestandardowego. Oznacza to, że można użyć dowolnego z elementów członkowskich <xref:System.Data.DataRow> klasy w swojej [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania. Dzięki temu można tworzyć zaawansowane, złożone zapytania.  
  
 Podobnie jak w przypadku innych implementacji [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], możesz utworzyć LINQ do zapytań zestawu danych w dwóch różnych formach: składnia wyrażenia oraz składni zapytania oparte na metodzie zapytania. Można użyć składni wyrażeń zapytania lub składni zapytania oparte na metodzie do wykonania zapytania względem pojedynczej tabel w <xref:System.Data.DataSet>, dla wielu tabel w <xref:System.Data.DataSet>, lub dla tabel w typizowanych <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania jednotabelowe](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 W tym artykule opisano, jak wykonywać zapytania jednotabelowe.  
  
 [Zapytania wielotabelowe](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań między tabelami.  
  
 [Wykonywanie zapytania do typizowanych zestawów danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 W tym artykule opisano sposób tworzenia zapytań względem wpisane <xref:System.Data.DataSet> obiektów.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
