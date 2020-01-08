---
title: 'Instrukcje: Ustawianie nagłówków w żądaniu klienta (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: af158fa525f1f83c081ab293bfdbfb4177caf5a6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348376"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Instrukcje: Ustawianie nagłówków w żądaniu klienta (Usługi danych programu WCF)
W przypadku korzystania z biblioteki klienta Usługi danych programu WCF w celu uzyskania dostępu do usługi danych, która obsługuje protokół Open Data Protocol (OData), Biblioteka klienta automatycznie ustawia wymagane nagłówki HTTP w komunikatach żądania wysyłanych do usługi danych. Jednak Biblioteka kliencka nie wie, aby ustawić nagłówki komunikatów, które są wymagane w niektórych przypadkach, na przykład gdy usługa danych wymaga uwierzytelniania opartego na oświadczeniach lub plików cookie. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md#clientAuthentication). W takich przypadkach należy ręcznie ustawić nagłówki komunikatów w komunikacie żądania przed jego wysłaniem. W przykładzie w tym temacie pokazano, jak obsłużyć zdarzenie <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, aby dodać nowy nagłówek do komunikatu żądania przed jego wysłaniem do usługi danych.  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md). Możesz również użyć [przykładowej usługi danych Northwind](https://services.odata.org/Northwind/Northwind.svc/) opublikowanej w witrynie sieci Web OData. Ta przykładowa usługa danych jest tylko do odczytu i próba zapisu spowoduje zwrócenie błędu. Przykładowe usługi danych w witrynie sieci Web OData umożliwiają uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje procedurę obsługi dla zdarzenia <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, a następnie wykonuje zapytanie względem usługi danych.  
  
> [!NOTE]
> Gdy usługa danych wymaga ręcznego ustawienia nagłówka komunikatu dla każdego żądania, należy rozważyć zarejestrowanie procedury obsługi dla zdarzenia <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>, zastępując metodę `OnContextCreated` częściową w kontenerze jednostek, który reprezentuje usługę danych, która w tym przypadku jest `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Przykład  
 Następująca metoda obsługuje zdarzenie <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> i dodaje nagłówek uwierzytelniania do żądania.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
