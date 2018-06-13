---
title: 'Porady: Dostosowywanie źródła danych za pomocą dostawcy odbicia (usługi danych WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 984a4aac43689be0ec80e7f6c289e8d5229e9e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358011"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Porady: Dostosowywanie źródła danych za pomocą dostawcy odbicia (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia dostosowanie Atom serializacji w odpowiedzi usługi danych, dzięki czemu można zamapować właściwości jednostki do nieużywanych elementów, które są zdefiniowane w protokole AtomPub. W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, które zdefiniowano przy użyciu dostawcy odbicia. Aby uzyskać więcej informacji, zobacz [źródła danych dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Model danych w tym przykładzie jest zdefiniowana w temacie [porady: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie obie właściwości `Order` typu są mapowane na istniejące elementy Atom. `Product` Właściwość `Item` typ jest mapowany na niestandardowy atrybut źródła strumieniowego w oddzielnych przestrzeni nazw.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Przykład  
 Poprzedni przykład zwraca następujący wyników dla identyfikatora URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
