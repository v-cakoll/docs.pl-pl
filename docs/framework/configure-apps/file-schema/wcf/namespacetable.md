---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855093"
---
# \<namespaceTable>

<span data-ttu-id="5ec8d-101">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="5ec8d-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ec8d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ec8d-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5ec8d-103">Attributes and elements</span></span>

<span data-ttu-id="5ec8d-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ec8d-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ec8d-105">Attributes</span></span>

<span data-ttu-id="5ec8d-106">Brak</span><span class="sxs-lookup"><span data-stu-id="5ec8d-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ec8d-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5ec8d-107">Child elements</span></span>

|     | <span data-ttu-id="5ec8d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5ec8d-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="5ec8d-109">Definiuje mapowanie prefiksu przestrzeni nazw używane dla wyrażeń XPath.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="5ec8d-110">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5ec8d-110">Parent elements</span></span>

|     | <span data-ttu-id="5ec8d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5ec8d-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="5ec8d-112">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="5ec8d-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="5ec8d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ec8d-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
