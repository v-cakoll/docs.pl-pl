---
title: 'Instrukcje: Pobieranie informacji jako tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: b98c5e6ea49695015eb566ca2176b23c5260017a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928714"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Instrukcje: Pobieranie informacji jako tylko do odczytu
Jeśli nie zamierzasz zmieniać danych, możesz zwiększyć wydajność zapytań, wyszukując wyniki tylko do odczytu.  
  
 Przetwarzanie w trybie tylko do odczytu jest implementowane `false`przez ustawienie <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> do.  
  
> [!NOTE]
> Gdy <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> jest ustawiona na `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> jest niejawnie ustawiona `false`na.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pobiera kolekcję dat zatrudnienia pracowników w trybie tylko do odczytu.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [Odroczone a bezpośrednie ładowanie](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
