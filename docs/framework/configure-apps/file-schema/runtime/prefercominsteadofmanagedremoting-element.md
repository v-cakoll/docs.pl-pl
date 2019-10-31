---
title: <PreferComInsteadOfManagedRemoting> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 47c568a8d6e89a195414552b3db5953ee61d1e55
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116013"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="d5771-102">\<element > PreferComInsteadOfManagedRemoting</span><span class="sxs-lookup"><span data-stu-id="d5771-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="d5771-103">Określa, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej dla wszystkich wywołań między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5771-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="d5771-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d5771-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d5771-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d5771-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d5771-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting >**</span><span class="sxs-lookup"><span data-stu-id="d5771-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5771-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5771-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5771-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d5771-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d5771-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d5771-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5771-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d5771-110">Attributes</span></span>  
  
|<span data-ttu-id="d5771-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d5771-111">Attribute</span></span>|<span data-ttu-id="d5771-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d5771-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d5771-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d5771-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d5771-114">Wskazuje, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5771-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d5771-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d5771-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d5771-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5771-116">Value</span></span>|<span data-ttu-id="d5771-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d5771-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d5771-118">Środowisko uruchomieniowe będzie używać komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5771-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="d5771-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d5771-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d5771-120">Środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5771-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5771-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d5771-121">Child Elements</span></span>  
 <span data-ttu-id="d5771-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d5771-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5771-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d5771-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d5771-124">Element</span><span class="sxs-lookup"><span data-stu-id="d5771-124">Element</span></span>|<span data-ttu-id="d5771-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d5771-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d5771-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5771-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d5771-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d5771-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5771-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5771-128">Remarks</span></span>  
 <span data-ttu-id="d5771-129">Po ustawieniu atrybutu `enabled` na `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d5771-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="d5771-130">Środowisko uruchomieniowe nie wywołuje [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , gdy interfejs [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) przechodzi do domeny za pomocą interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="d5771-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="d5771-131">Zamiast tego konstruuje [otokę w czasie wykonywania](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5771-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="d5771-132">Środowisko uruchomieniowe zwraca E_NOINTERFACE, gdy odbierze wywołanie `QueryInterface` dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) dla dowolnego [otoki](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) modelu COM, który został utworzony w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="d5771-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="d5771-133">Te dwa zachowania zapewniają, że wszystkie wywołania przez interfejsy COM między obiektami zarządzanymi między domenami aplikacji korzystają z międzyoperacyjności modelu COM i modelu COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="d5771-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5771-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5771-134">Example</span></span>  
 <span data-ttu-id="d5771-135">Poniższy przykład pokazuje, jak określić, że środowisko uruchomieniowe ma używać międzyoperacyjności modelu COM w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="d5771-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5771-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5771-136">See also</span></span>

- [<span data-ttu-id="d5771-137">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d5771-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d5771-138">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d5771-138">Configuration File Schema</span></span>](../index.md)
