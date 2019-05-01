---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: ee7a0c23adca883af279addf9d1f221bd4056d00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772414"
---
# <a name="namespacetable"></a><span data-ttu-id="66e2b-101">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="66e2b-101">\<namespaceTable></span></span>

<span data-ttu-id="66e2b-102">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które następnie mogą być używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="66e2b-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="66e2b-103">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="66e2b-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="66e2b-104">&nbsp;&nbsp;**\<routing>** </span><span class="sxs-lookup"><span data-stu-id="66e2b-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="66e2b-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="66e2b-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="66e2b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="66e2b-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66e2b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66e2b-107">Attributes and elements</span></span>

<span data-ttu-id="66e2b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66e2b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="66e2b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66e2b-109">Attributes</span></span>

<span data-ttu-id="66e2b-110">Brak</span><span class="sxs-lookup"><span data-stu-id="66e2b-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="66e2b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66e2b-111">Child elements</span></span>

|     | <span data-ttu-id="66e2b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="66e2b-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="66e2b-113">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="66e2b-113">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="66e2b-114">Definiuje mapowanie prefiksu przestrzeni nazw używany dla wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="66e2b-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="66e2b-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66e2b-115">Parent elements</span></span>

|     | <span data-ttu-id="66e2b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="66e2b-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="66e2b-117">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="66e2b-117">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="66e2b-118">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="66e2b-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="66e2b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66e2b-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
