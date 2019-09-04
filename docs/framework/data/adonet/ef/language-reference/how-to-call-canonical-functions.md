---
title: 'Instrukcje: Wywoływanie funkcji Canonical'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 3ad4576a5c7a3f2be4b68e4060df191932ceeb19
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250828"
---
# <a name="how-to-call-canonical-functions"></a>Instrukcje: Wywoływanie funkcji Canonical
<xref:System.Data.Objects.EntityFunctions> Klasa zawiera metody, które uwidaczniają funkcje kanoniczne do użycia w zapytaniach LINQ to Entities. Aby uzyskać informacje o funkcjach kanonicznych, zobacz [funkcje kanoniczne](canonical-functions.md).  
  
> [!NOTE]
> Metody <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> i <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> w<xref:System.Data.Objects.EntityFunctions> klasie nie mają odpowiedników funkcji kanonicznych.  
  
 Funkcje kanoniczne, które wykonują obliczenia na zestawie wartości i zwracają pojedynczą wartość (znaną również jako zagregowane funkcje kanoniczne), mogą być wywoływane bezpośrednio. Inne funkcje kanoniczne można wywołać tylko jako część zapytania LINQ to Entities. Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji. Aby uzyskać więcej informacji, zobacz drugi przykład poniżej.  
  
 Niektóre funkcje kanoniczne można wywołać przy użyciu metod środowiska uruchomieniowego języka wspólnego (CLR) w LINQ to Entities zapytaniach. Aby zapoznać się z listą metod CLR, które mapują na funkcje kanoniczne, zobacz [Mapowanie funkcji CLR na funkcję kanoniczną](clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). Przykład wykonuje kwerendę LINQ to Entities, która używa <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metody, aby zwrócić wszystkie produkty, dla których różnica między `SellEndDate` i `SellStartDate` jest mniejsza niż 365 dni:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). Przykład wywołuje metodę Aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> bezpośrednio, aby zwracała odchylenie `SalesOrderHeader` standardowe sum częściowych. Należy zauważyć, <xref:System.Data.Objects.ObjectQuery%601> że do funkcji jest przenoszona funkcja, która umożliwia jej wywoływanie bez części zapytania LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
