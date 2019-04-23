---
title: Typizowane elementy DataSet
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 92ed3f8fd392238785fd2d205668f14fe477f2b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098660"
---
# <a name="typed-datasets"></a>Typizowane elementy DataSet
Wraz z dostępu do wartości za pomocą ze słabą kontrolą typów zmiennych <xref:System.Data.DataSet> zapewnia dostęp do danych za pośrednictwem metaphor silnie typizowanych. Tabele i kolumny, które są częścią **DataSet** można uzyskać dostęp za pomocą nazw przyjaznych dla użytkownika i silnie typizowane zmiennych.  
  
 Wpisane **DataSet** to klasa, która jest pochodną **zestawu danych**. W efekcie dziedziczy wszystkie metody, zdarzenia i właściwości **zestawu danych**. Ponadto wpisane **DataSet** udostępnia silnie typizowane metody, zdarzenia i właściwości. Oznacza to, że ma dostęp do tabel i kolumn, według nazwy, zamiast korzystać z metody oparte na kolekcji. Oprócz lepszej czytelności kodu z kontrolą typów **DataSet** umożliwia także kodu programu Visual Studio .NET automatycznego zakończenia wierszy podczas wpisywania w edytorze.  
  
 Ponadto silnie typizowaną **DataSet** zapewnia dostęp do wartości jako poprawnego typu w czasie kompilacji. Za pomocą silnie typizowanej **DataSet**, błędy niezgodności wpisywania są wyłapywane, gdy kod jest kompilowany, a nie w czasie wykonywania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie silnie typizowanych elementów DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 Opisuje sposób tworzenia i używania silnie typizowaną **zestawu danych**.  
  
 [Dodawanie adnotacji do typizowanych elementów DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 Opisuje, jak dodawać adnotacje do schematu języka (XSD) definicji schematu XML, używany do generowania silnie typizowanej **zestawu danych**, aby zapewnić **zestawu danych** przyjaznych nazw elementów bez zmiany podstawowego schematu.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
