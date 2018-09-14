---
title: '&lt;Prefercominsteadofmanagedremoting —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c05e27226a58086c806e8977ba50a55873d1167e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508346"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="52acd-102">&lt;Prefercominsteadofmanagedremoting —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="52acd-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="52acd-103">Określa, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast komunikację zdalną dla wszystkich wywołań poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52acd-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="52acd-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="52acd-104">\<configuration></span></span>  
<span data-ttu-id="52acd-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="52acd-105">\<runtime></span></span>  
<span data-ttu-id="52acd-106">\<Prefercominsteadofmanagedremoting — ></span><span class="sxs-lookup"><span data-stu-id="52acd-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52acd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="52acd-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52acd-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="52acd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="52acd-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="52acd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52acd-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="52acd-110">Attributes</span></span>  
  
|<span data-ttu-id="52acd-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="52acd-111">Attribute</span></span>|<span data-ttu-id="52acd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="52acd-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="52acd-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="52acd-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="52acd-114">Wskazuje, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast komunikacji zdalnej poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52acd-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="52acd-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="52acd-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="52acd-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="52acd-116">Value</span></span>|<span data-ttu-id="52acd-117">Opis</span><span class="sxs-lookup"><span data-stu-id="52acd-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="52acd-118">Środowisko uruchomieniowe będzie używać komunikacji zdalnej poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52acd-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="52acd-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="52acd-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="52acd-120">Środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM, poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52acd-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52acd-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52acd-121">Child Elements</span></span>  
 <span data-ttu-id="52acd-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="52acd-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52acd-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52acd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="52acd-124">Element</span><span class="sxs-lookup"><span data-stu-id="52acd-124">Element</span></span>|<span data-ttu-id="52acd-125">Opis</span><span class="sxs-lookup"><span data-stu-id="52acd-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="52acd-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52acd-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="52acd-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="52acd-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52acd-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52acd-128">Remarks</span></span>  
 <span data-ttu-id="52acd-129">Po ustawieniu `enabled` atrybutu `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="52acd-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="52acd-130">Środowisko wykonawcze nie mogą wywoływać [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu, kiedy [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interfejs przejdzie domeny przy użyciu interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="52acd-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="52acd-131">Zamiast tego tworzy [wywoływana otoka środowiska uruchomieniowego](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="52acd-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="52acd-132">Środowisko wykonawcze zwraca E_NOINTERFACE po odebraniu `QueryInterface` wywołania dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu dla każdego [wywoływana otoka COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="52acd-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="52acd-133">Te dwa zachowania upewnij się, że wszystkie wywołania za pośrednictwem modelu COM interfejsy między zarządzanych obiektów między granic domeny aplikacji, użyj modelu COM i współdziałania z modelem COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="52acd-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52acd-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="52acd-134">Example</span></span>  
 <span data-ttu-id="52acd-135">Poniższy przykład pokazuje, jak określić, czy środowisko uruchomieniowe powinno używać COM międzyoperacyjnych w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="52acd-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52acd-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52acd-136">See Also</span></span>  
 [<span data-ttu-id="52acd-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="52acd-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="52acd-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="52acd-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
