---
title: 'Instrukcje: Ustawianie nagłówków w żądaniu klienta (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: bbf306b31dd2bc9cfcfb877351205970fc63706f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788781"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Instrukcje: Ustawianie nagłówków w żądaniu klienta (WCF Data Services)
Kiedy używasz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienckiej dostęp do usługi danych, która obsługuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], Biblioteka klienta automatycznie ustawia wymagane nagłówki HTTP w komunikatach żądań wysyłanych do usługi danych. Jednak biblioteka klienta nie wiadomo, do ustawiania nagłówków wiadomości, które są wymagane w niektórych przypadkach, np. gdy usługa danych wymaga uwierzytelniania opartego na oświadczeniach lub pliki cookie. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). W takich przypadkach należy ręcznie ustawić nagłówki wiadomości w komunikacie żądania, przed ich wysłaniem. W przykładzie w tym temacie pokazano sposób obsługi <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenie, aby dodać nowy nagłówek komunikatu żądania, przed wysłaniem ich do usługi danych.  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Można również użyć [Northwind przykładowe dane usługi](https://go.microsoft.com/fwlink/?LinkId=187426) opublikowaną w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web; te przykładowe dane usługi jest tylko do odczytu, a następnie próby zapisania zmiany zwraca błąd. Przykładowe dane usługi w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web umożliwia uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje program obsługi <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzeń, a następnie wykonuje zapytanie względem usługi danych.  
  
> [!NOTE]
>  Gdy usługa danych wymaga ręcznie ustawić nagłówek wiadomości dla każdego żądania, należy wziąć pod uwagę rejestrowanie programu obsługi dla <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzeń przez zastąpienie `OnContextCreated` usługi metody częściowej w kontenerze jednostki, który reprezentuje dane, które w Ten przypadek jest `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Przykład  
 Następujące obsługuje metody <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzeń i dodaje nagłówek uwierzytelnienia do żądania.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
