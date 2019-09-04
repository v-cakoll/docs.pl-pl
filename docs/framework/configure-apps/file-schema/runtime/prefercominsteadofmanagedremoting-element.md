---
title: <PreferComInsteadOfManagedRemoting>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d793c8d84a15f554ada78f3c0dd1f0e936893fd4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252407"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="91183-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="91183-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="91183-103">Określa, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej dla wszystkich wywołań między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91183-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="91183-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91183-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91183-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="91183-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="91183-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting>**</span><span class="sxs-lookup"><span data-stu-id="91183-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91183-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="91183-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91183-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="91183-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91183-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="91183-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91183-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="91183-110">Attributes</span></span>  
  
|<span data-ttu-id="91183-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="91183-111">Attribute</span></span>|<span data-ttu-id="91183-112">Opis</span><span class="sxs-lookup"><span data-stu-id="91183-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="91183-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="91183-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="91183-114">Wskazuje, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91183-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="91183-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="91183-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="91183-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="91183-116">Value</span></span>|<span data-ttu-id="91183-117">Opis</span><span class="sxs-lookup"><span data-stu-id="91183-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="91183-118">Środowisko uruchomieniowe będzie używać komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91183-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="91183-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="91183-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="91183-120">Środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91183-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91183-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="91183-121">Child Elements</span></span>  
 <span data-ttu-id="91183-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="91183-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91183-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="91183-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91183-124">Element</span><span class="sxs-lookup"><span data-stu-id="91183-124">Element</span></span>|<span data-ttu-id="91183-125">Opis</span><span class="sxs-lookup"><span data-stu-id="91183-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91183-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91183-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="91183-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="91183-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91183-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91183-128">Remarks</span></span>  
 <span data-ttu-id="91183-129">Po ustawieniu `enabled` atrybutu na `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="91183-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="91183-130">Środowisko uruchomieniowe nie wywołuje [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , gdy interfejs [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) przechodzi do domeny za pomocą interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="91183-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="91183-131">Zamiast tego konstruuje [otokę w czasie wykonywania](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="91183-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="91183-132">Środowisko uruchomieniowe zwraca E_NOINTERFACE, gdy odbierze `QueryInterface` wywołanie dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) dla dowolnego [otoki](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) modelu COM, który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="91183-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="91183-133">Te dwa zachowania zapewniają, że wszystkie wywołania przez interfejsy COM między obiektami zarządzanymi między domenami aplikacji korzystają z międzyoperacyjności modelu COM i modelu COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="91183-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91183-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="91183-134">Example</span></span>  
 <span data-ttu-id="91183-135">Poniższy przykład pokazuje, jak określić, że środowisko uruchomieniowe ma używać międzyoperacyjności modelu COM w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="91183-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91183-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91183-136">See also</span></span>

- [<span data-ttu-id="91183-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="91183-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="91183-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="91183-138">Configuration File Schema</span></span>](../index.md)
