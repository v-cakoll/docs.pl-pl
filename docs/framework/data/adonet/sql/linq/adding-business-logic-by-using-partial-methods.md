---
title: Dodawanie logiki biznesowej przy użyciu metody częściowe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: db18c48d697ae79f8c33c1674544f81cdd1c426a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361454"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Dodawanie logiki biznesowej przy użyciu metody częściowe
Można dostosować Visual Basic i C# wygenerowany kod w Twojej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektów przy użyciu *metody częściowe*. Kod który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje definiuje podpisów w ramach jednej metody częściowej. Jeśli chcesz zaimplementować metodę, można dodać własne metody częściowej. Jeśli nie należy dodawać własną implementację, kompilator odrzuca podpis metody częściowe i wywołuje metody domyślnej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dodać weryfikacji i inne dostosowania do klas jednostek.  
  
 Na przykład domyślnego mapowania dla `Customer` klasa w bazie danych Northwind zawiera następujące metody częściowej:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Można zaimplementować własnej metody przez dodanie następującego kodu do własnych częściowego `Customer` klasy:  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Ta metoda jest zwykle używana w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do przesłonięcia metody domyślnej `Insert`, `Update`, `Delete`oraz zweryfikowanie właściwości podczas zdarzenia cyklu życia obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [metody częściowe](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) lub [partial — metoda () (odwołanie w C#)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono `ExampleClass` najpierw może być zdefiniowana przez narzędzie generowania kodu, takie jak SQLMetal, a następnie jak może zastosować tylko jeden z dwóch metod.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie użyto relacji między `Shipper` i `Order` jednostek. Należy zwrócić uwagę wśród metod metody częściowe `InsertShipper` i `DeleteShipper`. Te metody zastąpienie domyślnych metod częściowych dostarczonych przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapowania.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
