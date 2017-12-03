---
title: '&lt;System.Runtime.serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a6eb2b152f2ab11bbe0e08ff1ad22f94d45057e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="551e2-102">&lt;System.Runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="551e2-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="551e2-103">Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="551e2-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="551e2-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="551e2-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="551e2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="551e2-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="551e2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="551e2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="551e2-107">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="551e2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="551e2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="551e2-108">Attributes</span></span>  
 <span data-ttu-id="551e2-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="551e2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="551e2-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="551e2-110">Child Elements</span></span>  
  
|<span data-ttu-id="551e2-111">Element</span><span class="sxs-lookup"><span data-stu-id="551e2-111">Element</span></span>|<span data-ttu-id="551e2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="551e2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="551e2-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="551e2-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="551e2-114">Umożliwia dodawanie ze znanych typów do użycia podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="551e2-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="551e2-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="551e2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="551e2-116">Element</span><span class="sxs-lookup"><span data-stu-id="551e2-116">Element</span></span>|<span data-ttu-id="551e2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="551e2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="551e2-118">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="551e2-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="551e2-119">Element najwyższego poziomu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="551e2-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="551e2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="551e2-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="551e2-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="551e2-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="551e2-122">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="551e2-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
