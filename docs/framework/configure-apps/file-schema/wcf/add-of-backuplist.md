---
title: <add> dla <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850551"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="f75db-102">\<Dodawanie > \<backupList ></span><span class="sxs-lookup"><span data-stu-id="f75db-102">\<add> of \<backupList></span></span>
<span data-ttu-id="f75db-103">Reprezentuje element konfiguracji, który definiuje kopię zapasową elementu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f75db-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
<span data-ttu-id="f75db-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f75db-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f75db-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f75db-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f75db-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="f75db-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="f75db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="f75db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="f75db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupList >** ](backuplist.md)</span><span class="sxs-lookup"><span data-stu-id="f75db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)</span></span>\
<span data-ttu-id="f75db-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="f75db-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f75db-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f75db-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f75db-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f75db-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f75db-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f75db-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f75db-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f75db-113">Attributes</span></span>  
  
|<span data-ttu-id="f75db-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f75db-114">Attribute</span></span>|<span data-ttu-id="f75db-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f75db-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f75db-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="f75db-116">name</span></span>|<span data-ttu-id="f75db-117">Ciąg określający nazwę punktu końcowego kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="f75db-117">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f75db-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f75db-118">Child Elements</span></span>  
 <span data-ttu-id="f75db-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="f75db-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f75db-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f75db-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f75db-121">Element</span><span class="sxs-lookup"><span data-stu-id="f75db-121">Element</span></span>|<span data-ttu-id="f75db-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f75db-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f75db-123">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="f75db-123">\<routing></span></span>](routing.md)|<span data-ttu-id="f75db-124">Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="f75db-124">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f75db-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f75db-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
