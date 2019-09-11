---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855093"
---
# <a name="namespacetable"></a><span data-ttu-id="d092e-101">\<Przestrzeń nazw ></span><span class="sxs-lookup"><span data-stu-id="d092e-101">\<namespaceTable></span></span>

<span data-ttu-id="d092e-102">Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.</span><span class="sxs-lookup"><span data-stu-id="d092e-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="d092e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d092e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d092e-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d092e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d092e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="d092e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="d092e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Przestrzeń nazw >**</span><span class="sxs-lookup"><span data-stu-id="d092e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d092e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d092e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d092e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d092e-108">Attributes and elements</span></span>

<span data-ttu-id="d092e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d092e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d092e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d092e-110">Attributes</span></span>

<span data-ttu-id="d092e-111">Brak</span><span class="sxs-lookup"><span data-stu-id="d092e-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d092e-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d092e-112">Child elements</span></span>

|     | <span data-ttu-id="d092e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d092e-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d092e-114"> **\<Filtr >** </span><span class="sxs-lookup"><span data-stu-id="d092e-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="d092e-115">Definiuje mapowanie prefiksu przestrzeni nazw używane dla wyrażeń XPath.</span><span class="sxs-lookup"><span data-stu-id="d092e-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="d092e-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d092e-116">Parent elements</span></span>

|     | <span data-ttu-id="d092e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d092e-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d092e-118"> **\<> routingu**</span><span class="sxs-lookup"><span data-stu-id="d092e-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="d092e-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe Wysyłaj komunikaty do, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="d092e-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d092e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d092e-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
