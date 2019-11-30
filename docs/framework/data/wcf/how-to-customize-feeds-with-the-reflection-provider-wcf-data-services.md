---
title: 'Instrukcje: Dostosowywanie kanałów informacyjnych za pomocą dostawcy odbicia (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: d3e2d587978a4c82784c8cfc8a7acc17cf601c3a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569145"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Instrukcje: Dostosowywanie kanałów informacyjnych za pomocą dostawcy odbicia (Usługi danych programu WCF)
Usługi danych programu WCF umożliwia dostosowanie serializacji Atom w odpowiedzi usługi danych, tak aby właściwości jednostki mogły być mapowane do nieużywanych elementów, które są zdefiniowane w protokole AtomPub. W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, który jest zdefiniowany przy użyciu dostawcy odbicia. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie kanału informacyjnego](feed-customization-wcf-data-services.md).  
  
 Model danych dla tego przykładu został zdefiniowany w temacie [jak: Tworzenie usługi danych przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie obie właściwości typu `Order` są mapowane na istniejące elementy Atom. Właściwość `Product` typu `Item` jest zamapowana na atrybut niestandardowego kanału informacyjnego w oddzielnym obszarze nazw.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Przykład  
 Poprzedni przykład zwraca następujący wynik dla identyfikatora URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Zobacz także

- [Dostawca odbicia](reflection-provider-wcf-data-services.md)
