---
title: 'Jak: Ustawianie nagłówków w żądaniu klienta (usługi danych WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 9267f0e5b68823516764891a40e1435c1325b77f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174345"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Jak: Ustawianie nagłówków w żądaniu klienta (usługi danych WCF)
Podczas korzystania z biblioteki klienta usług danych WCF w celu uzyskania dostępu do usługi danych obsługującej protokół OData (Open Data Protocol) biblioteka klienta automatycznie ustawia wymagane nagłówki HTTP w komunikatach żądań wysyłanych do usługi danych. Jednak biblioteka klienta nie wie, aby ustawić nagłówki wiadomości, które są wymagane w niektórych przypadkach, na przykład gdy usługa danych wymaga uwierzytelniania opartego na oświadczeniach lub plików cookie. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usług danych WCF](securing-wcf-data-services.md#clientAuthentication). W takich przypadkach należy ręcznie ustawić nagłówki wiadomości w wiadomości żądania przed wysłaniem. W przykładzie w tym temacie <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> pokazano, jak obsługiwać zdarzenie, aby dodać nowy nagłówek do komunikatu żądania, zanim zostanie wysłany do usługi danych.  
  
 W przykładzie w tym temacie używa usługi danych przykład northwind i automatycznie generowane klas usług danych klienta. Ta usługa i klasy danych klienta są tworzone po zakończeniu [szybkiego startu usług danych WCF](quickstart-wcf-data-services.md). Można również użyć [usługi danych przykładowych Northwind,](https://services.odata.org/Northwind/Northwind.svc/) która jest publikowana w witrynie sieci Web OData; ta przykładowa usługa danych jest tylko do odczytu i próby zapisania zmian zwraca błąd. Przykładowe usługi danych w witrynie sieci Web OData umożliwiają uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje program <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> obsługi dla zdarzenia, a następnie wykonuje kwerendę względem usługi danych.  
  
> [!NOTE]
> Gdy usługa danych wymaga ręcznego ustawiania nagłówka wiadomości dla każdego <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> żądania, należy rozważyć `OnContextCreated` zarejestrowanie programu obsługi dla zdarzenia, zastępując metodę `NorthwindEntities`częściową w kontenerze jednostki reprezentującej usługę danych, która w tym przypadku jest .  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Przykład  
 Poniższa metoda obsługuje <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenie i dodaje nagłówek uwierzytelniania do żądania.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
