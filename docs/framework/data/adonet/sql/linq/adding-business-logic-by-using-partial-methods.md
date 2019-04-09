---
title: Dodawanie logiki biznesowej przy użyciu metod częściowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: ea7dbc4f760a446440cb7291413d69b1202f80e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162662"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Dodawanie logiki biznesowej przy użyciu metod częściowych
Można dostosować Visual Basic i C# wygenerowany kod w swojej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektów za pomocą *metod częściowych*. Kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje definiuje podpisów w ramach jednej metody częściowej. Jeśli chcesz wdrożyć metodę, można dodać własne metody częściowej. Jeśli nie dodasz Twojej własnej implementacji, kompilator odrzuca podpis metod częściowych i wywołania metody domyślną, w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dodać sprawdzanie poprawności i innych dostosowań do klas jednostek.  
  
 Na przykład do domyślnego mapowania dla `Customer` klasy w bazie danych Northwind obejmuje następujące metody częściowej:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Można zaimplementować własną metodę, dodając następujący kod do własnych częściowego `Customer` klasy:  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 To podejście jest zwykle używana w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przesłonić domyślne metody `Insert`, `Update`, `Delete`, a do sprawdzania poprawności właściwości podczas zdarzenia cyklu życia obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [metod częściowych](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) lub [partial (metoda) (C# odwołania)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono `ExampleClass` najpierw może być zdefiniowana przez narzędzie generowania kodu, takich jak program SQLMetal, a następnie implementacji tylko w jednej z dwóch metod.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie użyto relacji między `Shipper` i `Order` jednostek. Należy zauważyć jedną z metod metod częściowych `InsertShipper` i `DeleteShipper`. Te metody Przesłaniaj metody częściowej domyślne, dostarczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapowania.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
