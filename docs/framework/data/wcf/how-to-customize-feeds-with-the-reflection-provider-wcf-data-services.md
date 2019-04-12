---
title: 'Instrukcje: Dostosowywanie źródła danych za pomocą dostawcy odbicia (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: f09c9827498dfd6b85a8476e824d06bfb481d1f8
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517203"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="32e1d-102">Instrukcje: Dostosowywanie źródła danych za pomocą dostawcy odbicia (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="32e1d-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="32e1d-103">Umożliwia dostosowanie Atom serializacji w odpowiedzi usługi danych, dzięki czemu właściwości jednostki mogą być mapowane do nieużywanych elementów, które są zdefiniowane w protokole AtomPub.</span><span class="sxs-lookup"><span data-stu-id="32e1d-103">enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="32e1d-104">W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, która jest zdefiniowana za pomocą dostawcy odbicia.</span><span class="sxs-lookup"><span data-stu-id="32e1d-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="32e1d-105">Aby uzyskać więcej informacji, zobacz [kanału informacyjnego dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="32e1d-105">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="32e1d-106">Model danych w tym przykładzie jest zdefiniowana w temacie [jak: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="32e1d-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="32e1d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="32e1d-107">Example</span></span>  
 <span data-ttu-id="32e1d-108">W poniższym przykładzie, obie właściwości `Order` typu są mapowane na istniejące elementy Atom.</span><span class="sxs-lookup"><span data-stu-id="32e1d-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="32e1d-109">`Product` Właściwość `Item` typu jest mapowany na atrybut niestandardowy kanału informacyjnego w oddzielnych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32e1d-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="32e1d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="32e1d-110">Example</span></span>  
 <span data-ttu-id="32e1d-111">Poprzedni przykład zwraca następujące wyniki dla identyfikatora URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="32e1d-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="32e1d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32e1d-112">See also</span></span>

- [<span data-ttu-id="32e1d-113">Dostawca odbicia</span><span class="sxs-lookup"><span data-stu-id="32e1d-113">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
