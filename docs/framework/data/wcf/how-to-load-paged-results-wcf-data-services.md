---
title: "Porady: obciążenia stronicowanej wyników (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91414ac4d392b9c042c9e236d2bfb69b44ead4ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Porady: obciążenia stronicowanej wyników (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umożliwia usłudze danych ograniczyć liczbę jednostek, które są zwracane w pojedynczą odpowiedź źródła danych. W takim przypadku końcowy wpis w źródle danych zawiera łącze do następnej strony danych. Identyfikator URI do następnej strony danych można uzyskać przez wywołanie <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody <xref:System.Data.Services.Client.QueryOperationResponse%601>, który jest zwracany, gdy <xref:System.Data.Services.Client.DataServiceQuery%601> jest wykonywana. Identyfikator URI reprezentowany przez ten obiekt jest następnie używany do załadowania następnej strony wyników. Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `do…while` pętli załadować `Customers` jednostek z wyników stronicowania z usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Zwraca powiązane `Orders` jednostek z każdym `Customers` jednostki i używa `do…while` pętli załadować `Customers` strony jednostek i zagnieżdżoną `while` pętli do załadowania strony powiązane `Orders` jednostek z usługi danych .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Porady: ładowanie powiązanych jednostek](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
