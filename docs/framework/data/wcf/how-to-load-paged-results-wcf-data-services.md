---
title: 'Instrukcje: Załaduj stronicowane wyniki (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: e718aad904a43d118a243afafc17834cba31f028
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790457"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Instrukcje: Załaduj stronicowane wyniki (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia usłudze danych ograniczenie liczby jednostek, które są zwracane w ramach pojedynczego źródła odpowiedzi. W takim przypadku końcowy wpis w kanale informacyjnym zawiera link do następnej strony danych. Identyfikator URI następnej strony danych jest uzyskiwany przez wywołanie <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody <xref:System.Data.Services.Client.QueryOperationResponse%601>, <xref:System.Data.Services.Client.DataServiceQuery%601> która jest zwracana, gdy jest wykonywane. Identyfikator URI reprezentowany przez ten obiekt jest następnie używany do załadowania następnej strony wyników. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano `do…while` pętlę w celu załadowania `Customers` jednostek z wyników ze strony z usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Przykład  
 Ten przykład zwraca powiązane `Orders` jednostki z każdą `Customers` jednostką i używa `do…while` pętli do załadowania `Customers` stron jednostek i zagnieżdżonej `while` pętli w celu załadowania `Orders` stron powiązanych jednostek z usługi danych .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Zobacz także

- [Ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md)
- [Instrukcje: Załaduj jednostki powiązane](how-to-load-related-entities-wcf-data-services.md)
