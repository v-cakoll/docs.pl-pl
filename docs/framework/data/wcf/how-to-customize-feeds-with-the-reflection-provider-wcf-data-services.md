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
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="18455-102">Instrukcje: Dostosowywanie kanałów informacyjnych za pomocą dostawcy odbicia (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="18455-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="18455-103">Usługi danych programu WCF umożliwia dostosowanie serializacji Atom w odpowiedzi usługi danych, tak aby właściwości jednostki mogły być mapowane do nieużywanych elementów, które są zdefiniowane w protokole AtomPub.</span><span class="sxs-lookup"><span data-stu-id="18455-103">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="18455-104">W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, który jest zdefiniowany przy użyciu dostawcy odbicia.</span><span class="sxs-lookup"><span data-stu-id="18455-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="18455-105">Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie kanału informacyjnego](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="18455-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="18455-106">Model danych dla tego przykładu został zdefiniowany w temacie [jak: Tworzenie usługi danych przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="18455-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="18455-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="18455-107">Example</span></span>  
 <span data-ttu-id="18455-108">W poniższym przykładzie obie właściwości typu `Order` są mapowane na istniejące elementy Atom.</span><span class="sxs-lookup"><span data-stu-id="18455-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="18455-109">Właściwość `Product` typu `Item` jest zamapowana na atrybut niestandardowego kanału informacyjnego w oddzielnym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="18455-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="18455-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="18455-110">Example</span></span>  
 <span data-ttu-id="18455-111">Poprzedni przykład zwraca następujący wynik dla identyfikatora URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="18455-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="18455-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18455-112">See also</span></span>

- [<span data-ttu-id="18455-113">Dostawca odbicia</span><span class="sxs-lookup"><span data-stu-id="18455-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
