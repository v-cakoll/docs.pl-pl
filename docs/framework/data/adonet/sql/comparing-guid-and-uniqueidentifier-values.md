---
title: Porównywanie identyfikatora GUID i wartości uniqueidentifier
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 7d982b73332a2629ccd32c409e0de6fe1ce6eb98
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201910"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Porównywanie identyfikatora GUID i wartości uniqueidentifier
Typ danych Unikatowy identyfikator globalny (GUID) w programie SQL Server jest reprezentowany przez `uniqueidentifier` typ danych, który przechowuje 16-bajtową wartość binarną. Identyfikator GUID jest liczbą binarną, i głównie jest jako identyfikator, który musi być unikatowa w sieci, który ma wiele komputerów w wielu lokacjach. Identyfikatorów GUID mogą być generowane przez wywołanie funkcji NEWID języka Transact-SQL i musi być unikatowa na całym świecie. Aby uzyskać więcej informacji, zobacz [uniqueidentifier (Transact-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql).  
  
## <a name="working-with-sqlguid-values"></a>Praca z wartościami SqlGuid  
 Identyfikatory GUID są długie i zasłoniętej, dlatego nie są zrozumiałe dla użytkowników. Jeśli losowo wygenerowane GUIDs są używane dla wartości klucza i wstawić wiele wierszy, otrzymasz losowych operacji We/Wy do indeksów, które może niekorzystnie wpłynąć na wydajność. Identyfikatory GUID są również stosunkowo dużej ilości, w porównaniu z innymi typami danych. Ogólnie rzecz biorąc zaleca się tylko na potrzeby scenariuszy bardzo małym, dla których żadne inne dane typu jest odpowiednia przy użyciu identyfikatorów GUID.  
  
### <a name="comparing-guid-values"></a>Porównanie wartości identyfikatora GUID  
 Operatory porównania mogą być używane z `uniqueidentifier` wartości. Jednak kolejność nie jest zaimplementowana przez porównanie wzorców bitowych z dwóch wartości. Jedyne operacje, które są dozwolone przed `uniqueidentifier` wartości są porównania (= <>, \<, >, \<=, > =) i sprawdzanie wartości NULL (IS NULL i IS NOT NULL). Inne operatory arytmetyczne są dozwolone.  
  
 Zarówno <xref:System.Guid> i <xref:System.Data.SqlTypes.SqlGuid> mają `CompareTo` metodę porównywania różnych wartości identyfikatora GUID. Jednak `System.Guid.CompareTo` i `SqlTypes.SqlGuid.CompareTo` są implementowane w inny sposób. <xref:System.Data.SqlTypes.SqlGuid> implementuje `CompareTo` przy użyciu działania programu SQL Server w ostatnich sześć bajtów wartości są najbardziej znaczące. <xref:System.Guid> ocenia wszystkie 16 bajtów. W poniższym przykładzie pokazano różnicę zachowań. Pierwsza sekcja kodu Wyświetla nieposortowane <xref:System.Guid> wartości, a druga sekcja kodu pokazuje sortowany <xref:System.Guid> wartości. Trzecia sekcja pokazuje sortowany <xref:System.Data.SqlTypes.SqlGuid> wartości. Dane wyjściowe jest wyświetlana poniżej przykładowy kod.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Ten przykład generuje następujące wyniki.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  

[Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)  
[Omówienie ADO.NET](../ado-net-overview.md)  
