---
title: Typizowane zbiory danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6ede928352c9e0f02f6ad4c27ce8f5347b868986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="typed-datasets"></a>Typizowane zbiory danych
Wraz z późne powiązania dostęp do wartości za pośrednictwem słabo zmienne typu <xref:System.Data.DataSet> zapewnia dostęp do danych za pośrednictwem jednoznacznie metaphor. Tabele i kolumny, które są częścią **DataSet** można uzyskać dostęp za pomocą nazw przyjaznych dla użytkownika i silnie typizowane zmiennych.  
  
 Typizowany **DataSet** jest klasą pochodną **zestawu danych**. W efekcie dziedziczy wszystkie metody, zdarzeń i właściwości **zestawu danych**. Ponadto maszynowy **DataSet** udostępnia silnie typizowane metody, zdarzeń i właściwości. Oznacza to, że są dostępne tabele i kolumny według nazwy, zamiast za pomocą metody opartej na kolekcji. Jako uzupełnienie Ulepszona czytelność kodu, typu **DataSet** umożliwia również kodu programu Visual Studio .NET edytora automatycznie wypełnić wierszy podczas pisania.  
  
 Ponadto silnie typizowaną **DataSet** zapewnia dostęp do wartości jako poprawnego typu w czasie kompilacji. Z silnie typizowaną **DataSet**, błędy niezgodności typów są przechwytywane, gdy kod jest skompilowany, a nie w czasie wykonywania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie silnie typizowanych elementów DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 Opisuje sposób tworzenia i używania silnie typizowaną **zestawu danych**.  
  
 [Dodawanie adnotacji do typizowanych elementów DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 Opisuje, jak dodawać adnotacje schematu języka (XSD) definicja schematu XML służący do generowania silnie typizowaną do **DataSet**, aby zapewnić **zestawu danych** przyjaznych nazw elementów bez zmiany podstawowego schematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
