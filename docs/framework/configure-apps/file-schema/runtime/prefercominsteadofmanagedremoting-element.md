---
title: <PreferComInsteadOfManagedRemoting> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452256"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="b9083-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="b9083-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="b9083-103">Określa, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej dla wszystkich wywołań między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9083-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="b9083-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9083-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9083-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b9083-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b9083-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b9083-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9083-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9083-107">Attributes</span></span>  
  
|<span data-ttu-id="b9083-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b9083-108">Attribute</span></span>|<span data-ttu-id="b9083-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b9083-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b9083-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b9083-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b9083-111">Wskazuje, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9083-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b9083-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="b9083-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="b9083-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="b9083-113">Value</span></span>|<span data-ttu-id="b9083-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b9083-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b9083-115">Środowisko uruchomieniowe będzie używać komunikacji zdalnej między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9083-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="b9083-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b9083-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b9083-117">Środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM między granicami domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9083-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9083-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b9083-118">Child Elements</span></span>  
 <span data-ttu-id="b9083-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="b9083-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9083-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b9083-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b9083-121">Element</span><span class="sxs-lookup"><span data-stu-id="b9083-121">Element</span></span>|<span data-ttu-id="b9083-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b9083-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b9083-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9083-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b9083-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b9083-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9083-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9083-125">Remarks</span></span>  
 <span data-ttu-id="b9083-126">Po ustawieniu `enabled` atrybutu na `true` , środowisko uruchomieniowe zachowuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9083-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="b9083-127">Środowisko uruchomieniowe nie wywołuje [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , gdy interfejs [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) przechodzi do domeny za pomocą interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="b9083-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="b9083-128">Zamiast tego konstruuje [otokę w czasie wykonywania](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.</span><span class="sxs-lookup"><span data-stu-id="b9083-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="b9083-129">Środowisko uruchomieniowe zwraca E_NOINTERFACE, gdy odbierze `QueryInterface` wywołanie dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) dla dowolnej [otoki](../../../../standard/native-interop/com-callable-wrapper.md) CCW (com), która została utworzona w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="b9083-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="b9083-130">Te dwa zachowania zapewniają, że wszystkie wywołania przez interfejsy COM między obiektami zarządzanymi między domenami aplikacji korzystają z międzyoperacyjności modelu COM i modelu COM zamiast komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="b9083-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9083-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9083-131">Example</span></span>  
 <span data-ttu-id="b9083-132">Poniższy przykład pokazuje, jak określić, że środowisko uruchomieniowe ma używać międzyoperacyjności modelu COM w granicach izolacji:</span><span class="sxs-lookup"><span data-stu-id="b9083-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9083-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9083-133">See also</span></span>

- [<span data-ttu-id="b9083-134">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b9083-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b9083-135">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b9083-135">Configuration File Schema</span></span>](../index.md)
