---
title: LINQ do DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783790"
---
# <a name="linq-to-dataset"></a>LINQ do DataSet
LINQ to DataSet ułatwia i przyspiesza wykonywanie zapytań dotyczących danych w pamięci podręcznej <xref:System.Data.DataSet> w obiekcie. W LINQ to DataSet upraszczają zapytania, umożliwiając deweloperom Pisanie zapytań w języku programowania, a nie za pomocą oddzielnego języka zapytań. Jest to szczególnie przydatne w przypadku deweloperów programu Visual Studio, którzy mogą teraz korzystać z sprawdzania składni w czasie kompilacji, pisania statycznego i obsługi technologii IntelliSense dostarczonych przez program Visual Studio w swoich zapytaniach.  
  
 LINQ to DataSet można również użyć do wykonywania zapytań dotyczących danych, które zostały skonsolidowane z co najmniej jednego źródła danych. Pozwala to na wiele scenariuszy, które wymagają elastyczności w zakresie reprezentowania i obsługi danych, takich jak wykonywanie zapytań dotyczących danych zagregowanych lokalnie i buforowanie warstwy środkowej w aplikacjach sieci Web. W szczególności, ogólne raporty, analizy i aplikacje analizy biznesowej wymagają tej metody manipulowania.  
  
 Funkcje LINQ to DataSet są udostępniane głównie przez metody rozszerzające w <xref:System.Data.DataRowExtensions> klasach i. <xref:System.Data.DataTableExtensions> LINQ to DataSet kompiluje na platformie i używa istniejącej architektury ADO.NET i nie jest przeznaczony do zastępowania ADO.NET w kodzie aplikacji. Istniejący kod ADO.NET będzie nadal działać w aplikacji LINQ to DataSet. Relacja LINQ to DataSet do ADO.NET i magazyn danych przedstawiono na poniższym diagramie.  
  
 ![Diagram przedstawiający, że LINQ to DataSet jest oparty na dostawcy ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](getting-started-linq-to-dataset.md)  
  
 [Przewodnik programowania](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Zobacz także

- [Language-Integrated Query (LINQ) —C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ i ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)
