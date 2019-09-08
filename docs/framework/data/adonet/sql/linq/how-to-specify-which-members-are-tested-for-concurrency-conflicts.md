---
title: 'Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: de7109e0fed0eb7c1975ad7360a7588ef9b294ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793141"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności
Zastosuj jeden z trzech typów wyliczeniowych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, które składowe mają być uwzględnione w testach aktualizacji w celu wykrywania optymistycznych konfliktów współbieżności.  
  
 Właściwość (zamapowana w czasie projektowania) jest używana razem z funkcjami współbieżności w czasie wykonywania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w systemie. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Pierwotne wartości elementów członkowskich są porównywane z bieżącym stanem bazy danych, o ile nie `IsVersion=true`wyznaczono żadnego elementu członkowskiego. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Aby zawsze używać tego elementu członkowskiego do wykrywania konfliktów  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. `Always`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Aby nigdy nie używać tego elementu członkowskiego do wykrywania konfliktów  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. `Never`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Aby użyć tego elementu członkowskiego do wykrywania konfliktów tylko wtedy, gdy aplikacja zmieniła wartość elementu członkowskiego  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. `WhenChanged`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości na.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie określono, `HomePage` że obiekty nigdy nie powinny być testowane podczas sprawdzania aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
