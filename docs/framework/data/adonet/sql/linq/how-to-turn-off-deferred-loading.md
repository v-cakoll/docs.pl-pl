---
title: "Porady: wyłączanie odroczonego ładowania"
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
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b0db2b178ba3c043ddadaeb650701ba144ed8e6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-turn-off-deferred-loading"></a>Porady: wyłączanie odroczonego ładowania
Można wyłączyć odroczonego ładowania ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`. Aby uzyskać więcej informacji, zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  Ładowanie odłożone jest wyłączone co za tym idzie, gdy obiekt śledzenie jest wyłączone. Aby uzyskać więcej informacji, zobacz [porady: pobieranie informacji jako tylko do odczytu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć odroczonego ładowania ustawiając <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> do `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
