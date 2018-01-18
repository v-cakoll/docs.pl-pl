---
title: LINQ do DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cdd3f21d8b02c24db24d2efd08487ef1a290e022
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-dataset"></a>LINQ do DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]umożliwia łatwiejsze i szybsze zapytania za pośrednictwem danych w pamięci podręcznej <xref:System.Data.DataSet> obiektu. W szczególności [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] upraszcza zapytań umożliwia deweloperom pisać zapytania od języka programowania, a nie przy użyciu języka osobne zapytania. Jest to szczególnie przydatne w przypadku [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] deweloperów, którzy mogą teraz wykorzystać sprawdzanie składni kompilacji, wpisując statycznych, i obsługę funkcji IntelliSense udostępniane przez [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] w swoich zapytań.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]może również służyć do zapytanie dotyczące danych, które zostały skonsolidowane z jednego lub więcej źródeł danych. Dzięki temu wiele scenariuszy, które wymagają elastyczność jak dane są reprezentowane i obsługi, takie jak wykonywanie kwerend lokalnie zagregowanych danych i warstwy środkowej buforowanie w aplikacjach sieci Web. W szczególności ogólnego raportowania, analizy i aplikacji analizy biznesowej wymagają tej metody manipulacji.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcji jest uwidaczniana, przede wszystkim za pośrednictwem metody rozszerzenia w <xref:System.Data.DataRowExtensions> i <xref:System.Data.DataTableExtensions> klasy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]oparty na i wykorzystuje istniejące [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architektury, a nie jako zamiennik [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] w kodzie aplikacji. Istniejący kod ADO.NET 2.0 będą nadal działać w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikacji. Relacja z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] do [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] i magazynu danych przedstawiono na poniższym diagramie.  
  
 ![LINQ do DataSet jest oparta na dostawcy ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ i ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
