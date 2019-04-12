---
title: 'Instrukcje: Wykonywanie asynchronicznych zapytań usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: f89a5004afeffe5aa9a28cb2d43374aede8a935e
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518165"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Instrukcje: Wykonywanie asynchronicznych zapytań usługi danych (WCF Data Services)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta asynchroniczne operacje można wykonywać klient serwer, takich jak wykonywanie zapytań i zapisywanie zmian. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  W aplikacji, gdy wywołanie zwrotne musi być wywoływany w określonym wątku, musisz jawnie zarządzać wykonywania <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można wykonać zapytania asynchroniczne, wywołując <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metodę, aby uruchomić zapytanie. Wbudowanej delegowanie wywołań <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metodę w celu wyświetlenia wyników zapytania.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
