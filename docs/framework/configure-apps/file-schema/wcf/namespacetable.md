---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: fb2b324a2c128b470f1a9a21343408280c5e1862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743247"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="42484-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="42484-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="42484-103">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="42484-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="42484-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="42484-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="42484-105">&nbsp;&nbsp;**\<Routing >** </span><span class="sxs-lookup"><span data-stu-id="42484-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="42484-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="42484-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="42484-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="42484-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42484-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="42484-108">Attributes and elements</span></span>

<span data-ttu-id="42484-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="42484-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="42484-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="42484-110">Attributes</span></span>

<span data-ttu-id="42484-111">Brak</span><span class="sxs-lookup"><span data-stu-id="42484-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="42484-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="42484-112">Child elements</span></span>

|     | <span data-ttu-id="42484-113">Opis</span><span class="sxs-lookup"><span data-stu-id="42484-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="42484-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="42484-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="42484-115">Definiuje mapowanie prefiksu przestrzeni nazw używany dla wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="42484-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="42484-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="42484-116">Parent elements</span></span>

|     | <span data-ttu-id="42484-117">Opis</span><span class="sxs-lookup"><span data-stu-id="42484-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="42484-118">**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="42484-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="42484-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="42484-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="42484-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42484-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
