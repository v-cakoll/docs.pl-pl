---
title: '&lt;PreferComInsteadOfManagedRemoting&gt; Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9292a0973df100acbffa341d7c0ca2604455f7fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522339"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="c518b-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span><span class="sxs-lookup"><span data-stu-id="c518b-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="c518b-103">Określa, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast komunikację zdalną dla wszystkich wywołań poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c518b-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="c518b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c518b-104">\<configuration></span></span>  
<span data-ttu-id="c518b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="c518b-105">\<runtime></span></span>  
<span data-ttu-id="c518b-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="c518b-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c518b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c518b-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c518b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c518b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c518b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c518b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c518b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c518b-110">Attributes</span></span>  
  
|<span data-ttu-id="c518b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c518b-111">Attribute</span></span>|<span data-ttu-id="c518b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c518b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c518b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c518b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c518b-114">Wskazuje, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast komunikacji zdalnej poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c518b-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c518b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="c518b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c518b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="c518b-116">Value</span></span>|<span data-ttu-id="c518b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c518b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c518b-118">Środowisko uruchomieniowe będzie używać komunikacji zdalnej poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c518b-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="c518b-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="c518b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c518b-120">Środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM, poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c518b-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c518b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c518b-121">Child Elements</span></span>  
 <span data-ttu-id="c518b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="c518b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c518b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c518b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c518b-124">Element</span><span class="sxs-lookup"><span data-stu-id="c518b-124">Element</span></span>|<span data-ttu-id="c518b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c518b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c518b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c518b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c518b-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c518b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c518b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c518b-128">Remarks</span></span>  
 <span data-ttu-id="c518b-129">Po ustawieniu `enabled` atrybutu `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c518b-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="c518b-130">Środowisko wykonawcze nie mogą wywoływać [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu, kiedy [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interfejs przejdzie domeny przy użyciu interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="c518b-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="c518b-131">Zamiast tego tworzy [wywoływana otoka środowiska uruchomieniowego](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="c518b-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="c518b-132">Środowisko wykonawcze zwraca E_NOINTERFACE po odebraniu `QueryInterface` wywołania dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu dla każdego [wywoływana otoka COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="c518b-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="c518b-133">Te dwa zachowania upewnij się, że wszystkie wywołania za pośrednictwem modelu COM interfejsy między zarządzanych obiektów między granic domeny aplikacji, użyj modelu COM i współdziałania z modelem COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="c518b-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c518b-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="c518b-134">Example</span></span>  
 <span data-ttu-id="c518b-135">Poniższy przykład pokazuje, jak określić, czy środowisko uruchomieniowe powinno używać COM międzyoperacyjnych w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="c518b-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c518b-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c518b-136">See also</span></span>
- [<span data-ttu-id="c518b-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c518b-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="c518b-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c518b-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
