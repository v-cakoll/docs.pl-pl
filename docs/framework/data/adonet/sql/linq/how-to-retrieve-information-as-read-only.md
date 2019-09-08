---
title: 'Instrukcje: Pobieranie informacji jako tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793318"
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

- [Pojęcia dotyczące zapytań](query-concepts.md)
- [Wykonywanie zapytania w bazie danych](querying-the-database.md)
- [Odroczone a bezpośrednie ładowanie](deferred-versus-immediate-loading.md)
