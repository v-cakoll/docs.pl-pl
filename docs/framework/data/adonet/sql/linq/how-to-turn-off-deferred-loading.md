---
title: 'Instrukcje: Wyłączanie odroczonego ładowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938676"
---
# <a name="how-to-turn-off-deferred-loading"></a>Instrukcje: Wyłączanie odroczonego ładowania
Można wyłączyć odroczone ładowanie według ustawienia <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do. `false` Aby uzyskać więcej informacji, zobacz odroczone względem [natychmiastowego ładowania](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Ładowanie odroczone jest wyłączone przez implikację, gdy śledzenie obiektów jest wyłączone. Aby uzyskać więcej informacji, zobacz [jak: Pobierz informacje jako tylko](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć odroczone ładowanie przez ustawienie <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do. `false`  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
