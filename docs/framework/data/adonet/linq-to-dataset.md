---
title: LINQ do DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 36335f90c7850fa00a15e7112b7473637250c656
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306235"
---
# <a name="linq-to-dataset"></a>LINQ do DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umożliwia łatwiejsze i szybsze zapytania przez dane buforowane w <xref:System.Data.DataSet> obiektu. W szczególności [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] upraszcza zapytań, dzięki czemu deweloperzy mogą pisać zapytania w języku programowania, a nie przy użyciu języka oddzielnego zapytania. Jest to szczególnie przydatne dla deweloperów programu Visual Studio, którzy mogą korzystać ze sprawdzania składni w czasie kompilacji, wpisując statycznych i IntelliSense pomoc techniczna jest świadczona przez program Visual Studio w zapytaniach.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] może również służyć do wykonywania zapytań względem danych, który został dołączony z co najmniej jedno źródło danych. Dzięki temu wiele scenariuszy, które wymagają elastyczność w sposób dane są reprezentowane i obsługiwane, takich jak zapytania lokalnie zagregowanych danych i warstwy środkowej buforowanie w aplikacjach sieci Web. W szczególności ogólne raportowanie, analiza i aplikacji analizy biznesowej wymagają tej metody do manipulowania.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcja jest widoczna przede wszystkim za pośrednictwem metody rozszerzające w <xref:System.Data.DataRowExtensions> i <xref:System.Data.DataTableExtensions> klasy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] opiera się na korzysta z istniejącej architektury ADO.NET i nie jest przeznaczona do zastąpienia ADO.NET w kodzie aplikacji. Istniejący kod ADO.NET będą w dalszym ciągu działać w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikacji. Relacje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ADO.NET i danych magazynu jest zilustrowany na poniższym diagramie.  
  
 ![Diagram przedstawiający, że LINQ to DataSet jest oparty na dostawcy ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie o języku zintegrowanym (LINQ) —C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Zapytanie o języku zintegrowanym (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ i ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
