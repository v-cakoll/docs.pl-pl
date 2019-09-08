---
title: 'Instrukcje: Ustaw nagłówki w żądaniu klienta (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 42987b1a855589954d45dae13b70ffc056c35f3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790468"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Instrukcje: Ustaw nagłówki w żądaniu klienta (Usługi danych programu WCF)
W przypadku korzystania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z biblioteki klienckiej w celu uzyskania dostępu do usługi danych [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], która obsługuje program, Biblioteka klienta automatycznie ustawia wymagane nagłówki HTTP w komunikatach żądania wysyłanych do usługi danych. Jednak Biblioteka kliencka nie wie, aby ustawić nagłówki komunikatów, które są wymagane w niektórych przypadkach, na przykład gdy usługa danych wymaga uwierzytelniania opartego na oświadczeniach lub plików cookie. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md#clientAuthentication). W takich przypadkach należy ręcznie ustawić nagłówki komunikatów w komunikacie żądania przed jego wysłaniem. W przykładzie w tym temacie pokazano, <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> jak obsłużyć zdarzenie, aby dodać nowy nagłówek do komunikatu żądania przed jego wysłaniem do usługi danych.  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md). Możesz również użyć [przykładowej usługi danych Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) opublikowanej w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witrynie sieci Web. Ta przykładowa usługa danych jest tylko do odczytu i próba zapisu spowoduje zwrócenie błędu. Przykładowe usługi danych w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witrynie sieci Web zezwalają na uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje procedurę obsługi dla <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenia, a następnie wykonuje zapytanie względem usługi danych.  
  
> [!NOTE]
> Gdy usługa danych wymaga ręcznego ustawienia nagłówka komunikatu dla każdego żądania, należy rozważyć zarejestrowanie procedury obsługi dla <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenia przez `OnContextCreated` zastąpienie metody częściowej w kontenerze jednostek, który reprezentuje usługę danych, która w w tym przypadku `NorthwindEntities`jest to.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Przykład  
 Następująca metoda obsługuje <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenie i dodaje nagłówek uwierzytelniania do żądania.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
