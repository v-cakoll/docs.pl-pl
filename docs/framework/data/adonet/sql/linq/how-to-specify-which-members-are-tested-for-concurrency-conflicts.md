---
title: 'Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: a690e95cadad4ed089fe1bb3ba6fea541a57411f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076305"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności
Zastosuj jedną z trzech typów wyliczeniowych do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, które elementy członkowskie, które mają być uwzględniane w ramach aktualizacji sprawdza, czy wykrywanie konfliktów optymistycznej współbieżności.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Mapowane w czasie projektowania) jest używana w połączeniu z funkcjami współbieżności środowiska wykonawczego w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Oryginalne wartości elementów członkowskich są porównywane z bieżącym stanem bazy danych, tak długo, jak żadnego elementu członkowskiego jest wyznaczony jako `IsVersion=true`. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Aby zawsze używać tego elementu członkowskiego do wykrywania konfliktów  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartość właściwości `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Aby nigdy nie używaj tego elementu członkowskiego do wykrywania konfliktów  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartość właściwości `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Do użycia tego elementu członkowskiego na potrzeby wykrywania konfliktów, tylko wtedy, gdy aplikacja została zmieniona wartość elementu członkowskiego  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartość właściwości `WhenChanged`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa, że `HomePage` obiektów nigdy nie powinny być badane podczas sprawdzania aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
