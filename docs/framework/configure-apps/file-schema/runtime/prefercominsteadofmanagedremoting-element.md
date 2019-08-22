---
title: <PreferComInsteadOfManagedRemoting>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a71c2b87d0bcb488e4e8fa4de928a103a8e9dabd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663541"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="dd04e-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="dd04e-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="dd04e-103">Określa, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej dla wszystkich wywołań między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd04e-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="dd04e-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dd04e-104">\<configuration></span></span>  
<span data-ttu-id="dd04e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="dd04e-105">\<runtime></span></span>  
<span data-ttu-id="dd04e-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="dd04e-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd04e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd04e-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd04e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dd04e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dd04e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dd04e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd04e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dd04e-110">Attributes</span></span>  
  
|<span data-ttu-id="dd04e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dd04e-111">Attribute</span></span>|<span data-ttu-id="dd04e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dd04e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="dd04e-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="dd04e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="dd04e-114">Wskazuje, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd04e-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dd04e-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="dd04e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="dd04e-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="dd04e-116">Value</span></span>|<span data-ttu-id="dd04e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="dd04e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="dd04e-118">Środowisko uruchomieniowe będzie używać komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd04e-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="dd04e-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="dd04e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="dd04e-120">Środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd04e-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd04e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dd04e-121">Child Elements</span></span>  
 <span data-ttu-id="dd04e-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="dd04e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd04e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd04e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dd04e-124">Element</span><span class="sxs-lookup"><span data-stu-id="dd04e-124">Element</span></span>|<span data-ttu-id="dd04e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="dd04e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dd04e-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd04e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dd04e-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dd04e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd04e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd04e-128">Remarks</span></span>  
 <span data-ttu-id="dd04e-129">Po ustawieniu `enabled` atrybutu na `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dd04e-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="dd04e-130">Środowisko uruchomieniowe nie wywołuje [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , gdy interfejs [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) przechodzi do domeny za pomocą interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="dd04e-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="dd04e-131">Zamiast tego konstruuje otokę w [czasie wykonywania](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="dd04e-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="dd04e-132">Środowisko uruchomieniowe zwraca E_NOINTERFACE, gdy odbierze `QueryInterface` wywołanie dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) dla dowolnego otoki (CCW) [modelu COM](../../../../../docs/standard/native-interop/com-callable-wrapper.md) , który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="dd04e-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="dd04e-133">Te dwa zachowania zapewniają, że wszystkie wywołania przez interfejsy COM między obiektami zarządzanymi między domenami aplikacji korzystają z międzyoperacyjności modelu COM i modelu COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="dd04e-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd04e-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd04e-134">Example</span></span>  
 <span data-ttu-id="dd04e-135">Poniższy przykład pokazuje, jak określić, że środowisko uruchomieniowe ma używać międzyoperacyjności modelu COM w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="dd04e-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd04e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd04e-136">See also</span></span>

- [<span data-ttu-id="dd04e-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="dd04e-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dd04e-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dd04e-138">Configuration File Schema</span></span>](../index.md)
