---
title: 'Instrukcje: Ustawianie nagłówków w żądaniu klienta (Usługi danych programu WCF)'
description: Dowiedz się, jak obsłużyć zdarzenie SendingRequest, aby dodać nowy nagłówek do komunikatu żądania przed jego wysłaniem do usługi danych w Usługi danych programu WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: fab1fcfdf92d275f51f433845aa0c253a00ec99d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247768"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Instrukcje: Ustawianie nagłówków w żądaniu klienta (Usługi danych programu WCF)
W przypadku korzystania z biblioteki klienta Usługi danych programu WCF w celu uzyskania dostępu do usługi danych, która obsługuje protokół Open Data Protocol (OData), Biblioteka klienta automatycznie ustawia wymagane nagłówki HTTP w komunikatach żądania wysyłanych do usługi danych. Jednak Biblioteka kliencka nie wie, aby ustawić nagłówki komunikatów, które są wymagane w niektórych przypadkach, na przykład gdy usługa danych wymaga uwierzytelniania opartego na oświadczeniach lub plików cookie. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md#clientAuthentication). W takich przypadkach należy ręcznie ustawić nagłówki komunikatów w komunikacie żądania przed jego wysłaniem. W przykładzie w tym temacie pokazano, jak obsłużyć <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenie, aby dodać nowy nagłówek do komunikatu żądania przed jego wysłaniem do usługi danych.  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md). Możesz również użyć [przykładowej usługi danych Northwind](https://services.odata.org/Northwind/Northwind.svc/) opublikowanej w witrynie sieci Web OData. Ta przykładowa usługa danych jest tylko do odczytu i próba zapisu spowoduje zwrócenie błędu. Przykładowe usługi danych w witrynie sieci Web OData umożliwiają uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje procedurę obsługi dla <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenia, a następnie wykonuje zapytanie względem usługi danych.  
  
> [!NOTE]
> Gdy usługa danych wymaga ręcznego ustawienia nagłówka komunikatu dla każdego żądania, należy rozważyć zarejestrowanie procedury obsługi dla <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenia przez zastąpienie `OnContextCreated` metody częściowej w kontenerze jednostek, który reprezentuje usługę danych, która w tym przypadku jest `NorthwindEntities` .  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Przykład  
 Następująca metoda obsługuje <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenie i dodaje nagłówek uwierzytelniania do żądania.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
