---
title: 'Instrukcje: Pobieranie informacji jako tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 131562e9ee0fbfde8c94f580bcb6d452918f42ee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148983"
---
# <a name="how-to-retrieve-information-as-read-only"></a>Instrukcje: Pobieranie informacji jako tylko do odczytu
Jeśli nie zamierzasz zmienić dane, możesz zwiększyć wydajność zapytań przez wyszukiwanie wyników tylko do odczytu.  
  
 Implementowanie przetwarzania tylko do odczytu, ustawiając <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> do `false`.  
  
> [!NOTE]
>  Gdy <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ustawiono `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> niejawnie ustawiono `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pobiera kolekcję tylko do odczytu dat zatrudnienia pracownika.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [Odroczone a bezpośrednie ładowanie](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
