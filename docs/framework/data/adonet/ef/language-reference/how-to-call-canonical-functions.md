---
title: 'Instrukcje: Wywoływanie funkcji kanonicznych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 33abf1a56750d6f13dabe773605ba1474ec75d45
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827308"
---
# <a name="how-to-call-canonical-functions"></a>Instrukcje: Wywoływanie funkcji kanonicznych
<xref:System.Data.Objects.EntityFunctions> Klasa zawiera metody, które udostępniają funkcje canonical do użycia w składniku LINQ do zapytań jednostki. Aby uzyskać informacje na temat funkcji kanonicznej Zobacz [funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> i <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody <xref:System.Data.Objects.EntityFunctions> klasa ma odpowiedników kanonicznej funkcji.  
  
 Funkcje Canonical, wykonywanie obliczeń na zbiór wartości, które zwraca pojedynczą wartość (znany także jako funkcje agregujące canonical) może być wywoływany bezpośrednio. Inne funkcje canonical można wywołać tylko jako część zapytaniu składnika LINQ to Entities. Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji. Aby uzyskać więcej informacji zobacz drugi przykład poniżej.  
  
 Niektóre funkcje canonical można wywoływać za pomocą wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) metody w składniku LINQ do zapytań jednostki. Aby uzyskać listę metodach CLR, które mapowania kanonicznej funkcji, zobacz [metody mapowania kanonicznej funkcji CLR](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples). Kod w przykładzie wykonuje zapytaniu składnika LINQ to Entities używającej <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metodę, aby zwrócić wszystkie produkty, dla którego różnica między `SellEndDate` i `SellStartDate` jest mniejszy niż 365 dni:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples). Przykład wywołuje agregacji <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> bezpośrednio metodę i zwraca odchylenie standardowe `SalesOrderHeader` sum częściowych. Należy pamiętać, że <xref:System.Data.Objects.ObjectQuery%601> jest przekazywany do funkcji, co pozwala na można wywołać bez bycie częścią zapytaniu składnika LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
