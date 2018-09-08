---
title: LINQ do DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 5e1644af7e07ad3395a30e56df52b7f85cefa77c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130672"
---
# <a name="linq-to-dataset"></a>LINQ do DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umożliwia łatwiejsze i szybsze zapytania przez dane buforowane w <xref:System.Data.DataSet> obiektu. W szczególności [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] upraszcza zapytań, dzięki czemu deweloperzy mogą pisać zapytania w języku programowania, a nie przy użyciu języka oddzielnego zapytania. Jest to szczególnie przydatne dla deweloperów programu Visual Studio, którzy mogą korzystać ze sprawdzania składni w czasie kompilacji, wpisując statycznych i IntelliSense pomoc techniczna jest świadczona przez program Visual Studio w zapytaniach.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] może również służyć do wykonywania zapytań względem danych, który został dołączony z co najmniej jedno źródło danych. Dzięki temu wiele scenariuszy, które wymagają elastyczność w sposób dane są reprezentowane i obsługiwane, takich jak zapytania lokalnie zagregowanych danych i warstwy środkowej buforowanie w aplikacjach sieci Web. W szczególności ogólne raportowanie, analiza i aplikacji analizy biznesowej wymagają tej metody do manipulowania.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcja jest widoczna przede wszystkim za pośrednictwem metody rozszerzające w <xref:System.Data.DataRowExtensions> i <xref:System.Data.DataTableExtensions> klasy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] opiera się na i wykorzystuje istniejące [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architektury, a nie jako zamiennik [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] w kodzie aplikacji. Istniejący kod ADO.NET w wersji 2.0 będzie w dalszym ciągu działać w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikacji. Relacje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] do [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] i magazyn danych zilustrowano na poniższym diagramie.  
  
 ![LINQ do zestawu danych zależy od dostawcy ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ i ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
