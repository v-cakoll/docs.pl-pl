---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 31d661f39f9e3de0f7012c7fa52d4964e7ee4a69
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="95461-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="95461-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="95461-103">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="95461-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="95461-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="95461-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="95461-105">&nbsp;&nbsp;**\<Routing >** </span><span class="sxs-lookup"><span data-stu-id="95461-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="95461-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="95461-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="95461-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="95461-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="95461-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95461-108">Attributes and elements</span></span>

<span data-ttu-id="95461-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95461-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="95461-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95461-110">Attributes</span></span>

<span data-ttu-id="95461-111">Brak</span><span class="sxs-lookup"><span data-stu-id="95461-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="95461-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95461-112">Child elements</span></span>

|     | <span data-ttu-id="95461-113">Opis</span><span class="sxs-lookup"><span data-stu-id="95461-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="95461-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="95461-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="95461-115">Definiuje mapowanie prefiksu przestrzeni nazw używany dla wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="95461-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="95461-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95461-116">Parent elements</span></span>

|     | <span data-ttu-id="95461-117">Opis</span><span class="sxs-lookup"><span data-stu-id="95461-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="95461-118">**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="95461-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="95461-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych, aby zdefiniować wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="95461-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="95461-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95461-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
