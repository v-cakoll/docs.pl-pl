---
title: <PreferComInsteadOfManagedRemoting>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b0a394500dbea0d557a33ea8d2e169c2c6561f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674028"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="bf28f-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="bf28f-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="bf28f-103">Określa, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast komunikację zdalną dla wszystkich wywołań poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf28f-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="bf28f-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bf28f-104">\<configuration></span></span>  
<span data-ttu-id="bf28f-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="bf28f-105">\<runtime></span></span>  
<span data-ttu-id="bf28f-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="bf28f-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf28f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf28f-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf28f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf28f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bf28f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf28f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf28f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf28f-110">Attributes</span></span>  
  
|<span data-ttu-id="bf28f-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf28f-111">Attribute</span></span>|<span data-ttu-id="bf28f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bf28f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bf28f-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="bf28f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf28f-114">Wskazuje, czy środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM zamiast komunikacji zdalnej poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf28f-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bf28f-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="bf28f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bf28f-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="bf28f-116">Value</span></span>|<span data-ttu-id="bf28f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="bf28f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bf28f-118">Środowisko uruchomieniowe będzie używać komunikacji zdalnej poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf28f-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="bf28f-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="bf28f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="bf28f-120">Środowisko uruchomieniowe będzie używać usługa międzyoperacyjna modelu COM, poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf28f-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf28f-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf28f-121">Child Elements</span></span>  
 <span data-ttu-id="bf28f-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf28f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf28f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf28f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf28f-124">Element</span><span class="sxs-lookup"><span data-stu-id="bf28f-124">Element</span></span>|<span data-ttu-id="bf28f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bf28f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf28f-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf28f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bf28f-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bf28f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf28f-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf28f-128">Remarks</span></span>  
 <span data-ttu-id="bf28f-129">Po ustawieniu `enabled` atrybutu `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bf28f-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="bf28f-130">Środowisko wykonawcze nie mogą wywoływać [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu, kiedy [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interfejs przejdzie domeny przy użyciu interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="bf28f-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="bf28f-131">Zamiast tego tworzy [wywoływana otoka środowiska uruchomieniowego](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="bf28f-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="bf28f-132">Środowisko wykonawcze zwraca E_NOINTERFACE po odebraniu `QueryInterface` wywołania dla [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interfejsu dla każdego [wywoływana otoka COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="bf28f-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="bf28f-133">Te dwa zachowania upewnij się, że wszystkie wywołania za pośrednictwem modelu COM interfejsy między zarządzanych obiektów między granic domeny aplikacji, użyj modelu COM i współdziałania z modelem COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="bf28f-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf28f-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf28f-134">Example</span></span>  
 <span data-ttu-id="bf28f-135">Poniższy przykład pokazuje, jak określić, czy środowisko uruchomieniowe powinno używać COM międzyoperacyjnych w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="bf28f-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf28f-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf28f-136">See also</span></span>

- [<span data-ttu-id="bf28f-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bf28f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="bf28f-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bf28f-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
