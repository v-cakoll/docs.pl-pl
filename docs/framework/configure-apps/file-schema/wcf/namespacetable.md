---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933173"
---
# <a name="namespacetable"></a><span data-ttu-id="0451e-101">\<Przestrzeń nazw ></span><span class="sxs-lookup"><span data-stu-id="0451e-101">\<namespaceTable></span></span>

<span data-ttu-id="0451e-102">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="0451e-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="0451e-103">**\<system.serviceModel>**  </span><span class="sxs-lookup"><span data-stu-id="0451e-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="0451e-104">&nbsp;&nbsp; **\<> routingu** </span><span class="sxs-lookup"><span data-stu-id="0451e-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="0451e-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<Przestrzeń nazw >**</span><span class="sxs-lookup"><span data-stu-id="0451e-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0451e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0451e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0451e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0451e-107">Attributes and elements</span></span>

<span data-ttu-id="0451e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0451e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0451e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0451e-109">Attributes</span></span>

<span data-ttu-id="0451e-110">Brak</span><span class="sxs-lookup"><span data-stu-id="0451e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0451e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0451e-111">Child elements</span></span>

|     | <span data-ttu-id="0451e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0451e-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0451e-113"> **\<Filtr >** </span><span class="sxs-lookup"><span data-stu-id="0451e-113">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="0451e-114">Definiuje mapowanie prefiksu przestrzeni nazw używane dla wyrażeń XPath.</span><span class="sxs-lookup"><span data-stu-id="0451e-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="0451e-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0451e-115">Parent elements</span></span>

|     | <span data-ttu-id="0451e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0451e-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0451e-117"> **\<> routingu**</span><span class="sxs-lookup"><span data-stu-id="0451e-117">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="0451e-118">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe Wysyłaj komunikaty do, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="0451e-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0451e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0451e-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
