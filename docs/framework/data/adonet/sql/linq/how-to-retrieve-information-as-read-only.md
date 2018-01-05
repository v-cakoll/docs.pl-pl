---
title: 'Porady: pobieranie informacji jako tylko do odczytu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 04a20a06cd8ed8785b37bdc604a817b475f93873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a>Porady: pobieranie informacji jako tylko do odczytu
Jeśli nie chcesz zmienić dane, można zwiększyć wydajność kwerend przez wyszukiwanie wyniki tylko do odczytu.  
  
 Implementowanie przetwarzania tylko do odczytu, ustawiając <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> do `false`.  
  
> [!NOTE]
>  Gdy <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ustawiono `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> niejawnie ustawiono `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pobiera kolekcji tylko do odczytu, dat pracownika.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [Odroczone a bezpośrednie ładowanie](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
