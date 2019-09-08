---
title: 'Instrukcje: Określanie sprawdzania konfliktów współbieżności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: fd3db5eb5dc9b74d8ea33af56dd522cf2f3fecdb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781585"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a>Instrukcje: Określanie sprawdzania konfliktów współbieżności
Można określić, które kolumny bazy danych mają być sprawdzane pod kątem konfliktów współbieżności podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Aby uzyskać więcej informacji, zobacz [jak: Określ, które elementy członkowskie są testowane pod](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)kątem konfliktów współbieżności.  
  
## <a name="example"></a>Przykład  
 Poniższy kod określa, że `HomePage` element członkowski nigdy nie powinien być testowany podczas sprawdzania aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
