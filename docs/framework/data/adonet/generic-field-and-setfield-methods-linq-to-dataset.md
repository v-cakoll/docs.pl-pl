---
title: "Ogólny pól i metod SetField (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58c2126c97d68fbe33d53b9d9ffa81fcc1aec8a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Ogólny pól i metod SetField (LINQ do DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]udostępnia metody rozszerzenia dla <xref:System.Data.DataRow> klasy do uzyskiwania dostępu do wartości w kolumnie: <xref:System.Data.DataRowExtensions.Field%2A> — metoda i <xref:System.Data.DataRowExtensions.SetField%2A> metody. Te metody zapewniają łatwiejszy dostęp do wartości w kolumnie dla deweloperów, szczególnie w odniesieniu do wartości null. <xref:System.Data.DataSet> Używa <xref:System.DBNull.Value> do reprezentowania wartości null, podczas gdy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] używa obsługi typ dopuszczający wartość null, wprowadzone w systemie [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Przy użyciu istniejącego akcesor kolumny w <xref:System.Data.DataRow> wymaga zwracany obiekt do odpowiedniego typu rzutowania. Jeśli w określonym polu <xref:System.Data.DataRow> może mieć wartości null, musisz jawnie sprawdzić wartość null, ponieważ zwracanie <xref:System.DBNull.Value> i niejawnie rzutowania go na inny typ zgłasza <xref:System.InvalidCastException>. W poniższym przykładzie Jeśli <xref:System.Data.DataRow.IsNull%2A> nie użyto metody do sprawdzenia wartości null, wyjątek może zostać zgłoszony, gdy zwracany indeksatora <xref:System.DBNull.Value> i próbował rzutować obiekt <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda zapewnia dostęp do wartości kolumny <xref:System.Data.DataRow> i <xref:System.Data.DataRowExtensions.SetField%2A> ustawia wartości w kolumnie w <xref:System.Data.DataRow>. Zarówno <xref:System.Data.DataRowExtensions.Field%2A> — metoda i <xref:System.Data.DataRowExtensions.SetField%2A> metody obsługi typów dopuszczających wartości zerowe, dzięki czemu nie trzeba jawnie sprawdziła wartości null, co w poprzednim przykładzie. Obie metody metody ogólne są również, dzięki czemu nie trzeba Rzutowanie na typ zwracany.  
  
 W poniższym przykładzie użyto <xref:System.Data.DataRowExtensions.Field%2A> metody.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Należy pamiętać, że typ danych określony w parametrze ogólnym `T` z <xref:System.Data.DataRowExtensions.Field%2A> — metoda i <xref:System.Data.DataRowExtensions.SetField%2A> metody musi odpowiadać typowi wartości podstawowej. W przeciwnym razie <xref:System.InvalidCastException> zostanie wygenerowany wyjątek. Określona nazwa kolumny musi również zgodna z nazwą kolumny <xref:System.Data.DataSet>, lub <xref:System.ArgumentException> zostanie wygenerowany. W obu przypadkach wyjątku w czasie wykonywania podczas wyliczania danych podczas wykonywania zapytania.  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> Metody nie przeprowadza jakiejkolwiek konwersji typu. Oznacza to, jednak nie nastąpi konwersji typu. <xref:System.Data.DataRowExtensions.SetField%2A> Ujawnia metody [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] zachowanie <xref:System.Data.DataRow> klasy. Konwersja typów może zostać wykonana przez <xref:System.Data.DataRow> obiekt i skonwertowana wartość następnie zostaną zapisane w <xref:System.Data.DataRow> obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataRowExtensions>
