---
title: 'Porady: wywoływanie funkcji kanonicznych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 1a936c5374137dbe25e16ababfa8a4f0c86edbbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521773"
---
# <a name="how-to-call-canonical-functions"></a>Porady: wywoływanie funkcji kanonicznych
<xref:System.Data.Objects.EntityFunctions> Klasa zawiera metody, które udostępniają funkcje canonical do użycia w składniku LINQ do zapytań jednostki. Aby uzyskać informacje na temat funkcji kanonicznej Zobacz [funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> i <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metody <xref:System.Data.Objects.EntityFunctions> klasa ma odpowiedników kanonicznej funkcji.  
  
 Funkcje Canonical, wykonywanie obliczeń na zbiór wartości, które zwraca pojedynczą wartość (znany także jako funkcje agregujące canonical) może być wywoływany bezpośrednio. Inne funkcje canonical można wywołać tylko jako część zapytaniu składnika LINQ to Entities. Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji. Aby uzyskać więcej informacji zobacz drugi przykład poniżej.  
  
 Niektóre funkcje canonical można wywoływać za pomocą wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) metody w składniku LINQ do zapytań jednostki. Aby uzyskać listę metodach CLR, które mapowania kanonicznej funkcji, zobacz [metody mapowania kanonicznej funkcji CLR](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Kod w przykładzie wykonuje zapytaniu składnika LINQ to Entities używającej <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metodę, aby zwrócić wszystkie produkty, dla którego różnica między `SellEndDate` i `SellStartDate` jest mniejszy niż 365 dni:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832). Przykład wywołuje agregacji <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> bezpośrednio metodę i zwraca odchylenie standardowe `SalesOrderHeader` sum częściowych. Należy pamiętać, że <xref:System.Data.Objects.ObjectQuery%601> jest przekazywany do funkcji, co pozwala na można wywołać bez bycie częścią zapytaniu składnika LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
