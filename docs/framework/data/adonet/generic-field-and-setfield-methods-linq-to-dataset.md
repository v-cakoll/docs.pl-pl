---
title: Ogólne metody pola i pola setfield (LINQ do DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249106"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>Ogólne metody pola i pola setfield (LINQ do DataSet)
LINQ do DataSet udostępnia <xref:System.Data.DataRow> metody rozszerzenia do klasy <xref:System.Data.DataRowExtensions.Field%2A> dostępu do <xref:System.Data.DataRowExtensions.SetField%2A> wartości kolumn: metoda i metoda. Te metody zapewniają łatwiejszy dostęp do wartości kolumn dla deweloperów, szczególnie w odniesieniu do wartości null. Używa <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType> do reprezentowania wartości null, podczas gdy <xref:System.Nullable> <xref:System.Nullable%601> LINQ używa i typów. Za pomocą istniejącego akcesora kolumny w <xref:System.Data.DataRow> wymaga rzutu obiektu zwracany do odpowiedniego typu. Jeśli określone pole <xref:System.Data.DataRow> w może być null, należy jawnie sprawdzić <xref:System.DBNull.Value?displayProperty=nameWithType> wartość null, ponieważ zwracanie i <xref:System.InvalidCastException>niejawnie rzutowanie go do innego typu zgłasza . W poniższym przykładzie, jeśli <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> metoda nie została użyta do sprawdzenia wartości null, <xref:System.DBNull.Value?displayProperty=nameWithType> wyjątek zostanie zgłoszony, jeśli indeksator zwrócił i próbował przerzucić go na . <xref:System.String>  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 Metoda <xref:System.Data.DataRowExtensions.Field%2A> zapewnia dostęp do wartości <xref:System.Data.DataRow> kolumn <xref:System.Data.DataRowExtensions.SetField%2A> a i ustawia <xref:System.Data.DataRow>wartości kolumn w . Zarówno <xref:System.Data.DataRowExtensions.Field%2A> metoda, <xref:System.Data.DataRowExtensions.SetField%2A> jak i metoda obsługują typy wartości nullable, więc nie trzeba jawnie sprawdzić wartości null, jak w poprzednim przykładzie. Obie metody są metody ogólne, również, więc nie trzeba rzutować typu zwracania.  
  
 W poniższym przykładzie użyto <xref:System.Data.DataRowExtensions.Field%2A> metody.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Należy zauważyć, że typ danych `T` określony <xref:System.Data.DataRowExtensions.Field%2A> w <xref:System.Data.DataRowExtensions.SetField%2A> parametrze ogólnym metody i metody musi odpowiadać typowi wartości podstawowej. W przeciwnym <xref:System.InvalidCastException> razie zostanie zgłoszony wyjątek. Określona nazwa kolumny musi również odpowiadać <xref:System.Data.DataSet>nazwie kolumny <xref:System.ArgumentException> w , lub zostanie rzucona. W obu przypadkach wyjątek jest zgłaszany w czasie wykonywania podczas wyliczania danych podczas wykonywania kwerendy.  
  
 Sama <xref:System.Data.DataRowExtensions.SetField%2A> metoda nie wykonuje żadnych konwersji typu. Nie oznacza to jednak, że konwersja typu nie nastąpi. Metoda <xref:System.Data.DataRowExtensions.SetField%2A> udostępnia zachowanie ADO.NET <xref:System.Data.DataRow> klasy. Konwersja typu może być <xref:System.Data.DataRow> wykonana przez obiekt, a przekonwertowana wartość zostanie następnie zapisana w <xref:System.Data.DataRow> obiekcie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataRowExtensions>
