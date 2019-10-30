---
title: Porównywanie identyfikatora GUID i wartości uniqueidentifier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 18f7ad8f6ef9cdf726bdf606ab108e2c5140aed7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040465"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Porównywanie identyfikatora GUID i wartości uniqueidentifier
Typ danych unikatowy identyfikator globalny (GUID) w SQL Server jest reprezentowany przez typ danych `uniqueidentifier`, który przechowuje 16-bajtową wartość binarną. Identyfikator GUID jest liczbą binarną, a jej głównym zastosowaniem jest jako identyfikator, który musi być unikatowy w sieci, która ma wiele komputerów w wielu lokacjach. Identyfikatory GUID można generować przez wywołanie funkcji NEWID języka Transact-SQL i gwarantuje, że będzie ona unikatowa na całym świecie. Aby uzyskać więcej informacji, zobacz [unikatowy identyfikator (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Praca z wartościami SqlGuid  
 Ponieważ wartości identyfikatorów GUID są długie i zasłaniane, nie są one znaczące dla użytkowników. W przypadku używania losowo generowanych identyfikatorów GUID dla wartości kluczy i wstawiania dużej liczby wierszy uzyskujesz losowe we/wy w indeksach, co może negatywnie wpłynąć na wydajność. Identyfikatory GUID są również stosunkowo duże w porównaniu z innymi typami danych. Ogólnie zalecamy korzystanie z identyfikatorów GUID tylko w przypadku bardzo wąskich scenariuszy, dla których nie jest odpowiedni inny typ danych.  
  
### <a name="comparing-guid-values"></a>Porównywanie wartości identyfikatora GUID  
 Operatory porównania mogą być używane z wartościami `uniqueidentifier`. Jednak porządkowanie nie jest zaimplementowane przez porównanie wzorców bitowych dwóch wartości. Jedyną operacją, która jest dozwolona dla wartości `uniqueidentifier` są porównania (=, < >, \<, >, \<=, > =) i sprawdzanie wartości NULL (IS NULL i IS NOT NULL). Nie są dozwolone żadne inne operatory arytmetyczne.  
  
 Zarówno <xref:System.Guid>, jak i <xref:System.Data.SqlTypes.SqlGuid> mają metodę `CompareTo` do porównywania różnych wartości identyfikatorów GUID. Jednak `System.Guid.CompareTo` i `SqlTypes.SqlGuid.CompareTo` są implementowane inaczej. <xref:System.Data.SqlTypes.SqlGuid> implementuje `CompareTo` przy użyciu zachowania SQL Server, w ciągu ostatnich sześciu bajtów wartości są najbardziej znaczące. <xref:System.Guid> oblicza wszystkie 16 bajtów. Poniższy przykład ilustruje tę różnicę zachowania. W pierwszej sekcji kodu są wyświetlane niesortowane <xref:System.Guid> wartości, a druga sekcja kodu pokazuje posortowane wartości <xref:System.Guid>. Trzecia sekcja zawiera posortowane wartości <xref:System.Data.SqlTypes.SqlGuid>. Dane wyjściowe są wyświetlane poniżej listy kodu.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Ten przykład generuje następujące wyniki.  
  
```output  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
