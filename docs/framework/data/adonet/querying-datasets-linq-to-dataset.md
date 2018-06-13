---
title: Wykonywanie zapytania zestawów danych (LINQ do DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 18daed2ee4196a03af818dfbd0e65153ae43a840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361763"
---
# <a name="querying-datasets-linq-to-dataset"></a>Wykonywanie zapytania zestawów danych (LINQ do DataSet)
Po <xref:System.Data.DataSet> obiekt został wypełniony danymi, można rozpocząć, badając ją. Formułowania zapytań dotyczących [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] jest podobny do sposobu używania [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] względem innych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]— włączone źródeł danych. Należy jednak pamiętać, że gdy używasz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] odpytuje za pośrednictwem <xref:System.Data.DataSet> obiektu wyszukując wyliczenie <xref:System.Data.DataRow> obiektów zamiast wyliczenia typu niestandardowego. Oznacza to, że można użyć dowolnego z elementów członkowskich <xref:System.Data.DataRow> klasy w Twojej [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania. Dzięki temu można tworzyć zaawansowane, złożone kwerendy.  
  
 Tak jak w innych implementacjach [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], można utworzyć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania w dwóch różnych formularzach: wyrażenie składnia zapytania i metody zapytań. Aby uzyskać więcej informacji o tych dwóch form, zobacz [wprowadzenie do LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Za pomocą składni wyrażenia zapytania lub składnia zapytania oparte na metodzie do wykonania zapytania względem jednej tabel w <xref:System.Data.DataSet>, dla wielu tabel w <xref:System.Data.DataSet>, lub dla tabel w typizowanych <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania jednotabelowe](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań pojedynczej tabeli.  
  
 [Zapytania wielotabelowe](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Opisuje sposób wykonywania zapytań między tabelami.  
  
 [Wykonywanie zapytania do typizowanych zestawów danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Opisuje sposób tworzenia zapytań wpisany <xref:System.Data.DataSet> obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
