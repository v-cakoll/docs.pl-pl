---
title: "Porady: Dostosowywanie źródła danych za pomocą dostawcy odbicia (usługi danych WCF)"
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
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 26a7d3f0316a62f1e3fd655e6b00ca23297c8d7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Porady: Dostosowywanie źródła danych za pomocą dostawcy odbicia (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umożliwia dostosowanie Atom serializacji w odpowiedzi usługi danych, dzięki czemu można zamapować właściwości jednostki do nieużywanych elementów, które są zdefiniowane w protokole AtomPub. W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, które zdefiniowano przy użyciu dostawcy odbicia. Aby uzyskać więcej informacji, zobacz [źródła danych dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
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
