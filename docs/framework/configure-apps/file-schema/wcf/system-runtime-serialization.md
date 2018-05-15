---
title: '&lt;System.Runtime.serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 6ffd4057028adcd123086173a05164eb5d2622f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="10cd0-102">&lt;System.Runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="10cd0-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="10cd0-103">Reprezentuje element główny <xref:System.Runtime.Serialization> sekcji przestrzeni nazw i zawiera elementy dla opcji ustawienia obiektu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="10cd0-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="10cd0-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="10cd0-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10cd0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="10cd0-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10cd0-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="10cd0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="10cd0-107">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="10cd0-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10cd0-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="10cd0-108">Attributes</span></span>  
 <span data-ttu-id="10cd0-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="10cd0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10cd0-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="10cd0-110">Child Elements</span></span>  
  
|<span data-ttu-id="10cd0-111">Element</span><span class="sxs-lookup"><span data-stu-id="10cd0-111">Element</span></span>|<span data-ttu-id="10cd0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="10cd0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10cd0-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="10cd0-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="10cd0-114">Umożliwia dodawanie ze znanych typów do użycia podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="10cd0-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10cd0-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="10cd0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="10cd0-116">Element</span><span class="sxs-lookup"><span data-stu-id="10cd0-116">Element</span></span>|<span data-ttu-id="10cd0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="10cd0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10cd0-118">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="10cd0-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="10cd0-119">Element najwyższego poziomu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="10cd0-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10cd0-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10cd0-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="10cd0-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="10cd0-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="10cd0-122">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="10cd0-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
