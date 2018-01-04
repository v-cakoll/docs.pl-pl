---
title: "&lt;Prefercominsteadofmanagedremoting —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad60d73e30bf02fd52f9c8f3bd707b571959bdd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="eb805-102">&lt;Prefercominsteadofmanagedremoting —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="eb805-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="eb805-103">Określa, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast usług zdalnych dla wszystkich wywołań poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb805-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="eb805-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="eb805-104">\<configuration></span></span>  
<span data-ttu-id="eb805-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="eb805-105">\<runtime></span></span>  
<span data-ttu-id="eb805-106">\<Prefercominsteadofmanagedremoting — ></span><span class="sxs-lookup"><span data-stu-id="eb805-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb805-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb805-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb805-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb805-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eb805-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb805-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb805-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb805-110">Attributes</span></span>  
  
|<span data-ttu-id="eb805-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eb805-111">Attribute</span></span>|<span data-ttu-id="eb805-112">Opis</span><span class="sxs-lookup"><span data-stu-id="eb805-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="eb805-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="eb805-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="eb805-114">Wskazuje, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast usług zdalnych poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb805-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="eb805-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="eb805-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="eb805-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="eb805-116">Value</span></span>|<span data-ttu-id="eb805-117">Opis</span><span class="sxs-lookup"><span data-stu-id="eb805-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="eb805-118">Środowisko wykonawcze będzie używać usług zdalnych poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb805-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="eb805-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="eb805-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="eb805-120">Środowisko wykonawcze będzie używać usługa międzyoperacyjna modelu COM poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb805-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb805-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb805-121">Child Elements</span></span>  
 <span data-ttu-id="eb805-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb805-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb805-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb805-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eb805-124">Element</span><span class="sxs-lookup"><span data-stu-id="eb805-124">Element</span></span>|<span data-ttu-id="eb805-125">Opis</span><span class="sxs-lookup"><span data-stu-id="eb805-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eb805-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb805-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="eb805-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="eb805-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb805-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb805-128">Remarks</span></span>  
 <span data-ttu-id="eb805-129">Podczas ustawiania `enabled` atrybutu `true`, środowisko uruchomieniowe działa w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="eb805-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="eb805-130">Środowisko uruchomieniowe nie wywołuje [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu, kiedy [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interfejs przejdzie domeny przy użyciu interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="eb805-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="eb805-131">Zamiast tego tworzy [wywoływana otoka środowiska uruchomieniowego](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="eb805-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="eb805-132">Środowisko uruchomieniowe zwraca E_NOINTERFACE, gdy odbierze `QueryInterface` wywołania dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu dla każdego [wywoływana otoka COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="eb805-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="eb805-133">Te dwie zachowania upewnij się, że wszystkie wywołania za pośrednictwem modelu COM interfejsy między obiektami zarządzanymi przez granice domeny aplikacji, użyj modelu COM i COM interop zamiast usług zdalnych.</span><span class="sxs-lookup"><span data-stu-id="eb805-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb805-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb805-134">Example</span></span>  
 <span data-ttu-id="eb805-135">Poniższy przykład przedstawia do określenia, że środowisko wykonawcze powinien używać COM interop poza granicami izolacji:</span><span class="sxs-lookup"><span data-stu-id="eb805-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb805-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb805-136">See Also</span></span>  
 [<span data-ttu-id="eb805-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="eb805-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="eb805-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eb805-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
