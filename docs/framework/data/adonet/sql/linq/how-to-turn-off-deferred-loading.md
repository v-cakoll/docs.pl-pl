---
title: 'Instrukcje: Wyłączanie odroczonego ładowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 9878ec468333ba79d0171d0bf96235d48273e03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669539"
---
# <a name="how-to-turn-off-deferred-loading"></a>Instrukcje: Wyłączanie odroczonego ładowania
Można wyłączyć odroczonego ładowania, ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`. Aby uzyskać więcej informacji, zobacz [odroczone a ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  Odroczonego ładowania jest wyłączona przez domniemanie, gdy obiekt śledzenie jest wyłączone. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie informacji jako tylko do odczytu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączanie odroczonego ładowania, ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
