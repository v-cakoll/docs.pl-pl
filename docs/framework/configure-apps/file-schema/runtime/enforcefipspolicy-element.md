---
title: <enforceFIPSPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114836"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="1b72e-102">\<enforceFIPSPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="1b72e-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="1b72e-103">Określa, czy do wymuszania wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardów FIPS (Federal Information).</span><span class="sxs-lookup"><span data-stu-id="1b72e-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="1b72e-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="1b72e-104">\<configuration> Element</span></span>  
<span data-ttu-id="1b72e-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="1b72e-105">\<runtime> Element</span></span>  
<span data-ttu-id="1b72e-106">\<enforceFIPSPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="1b72e-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b72e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b72e-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b72e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1b72e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1b72e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1b72e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b72e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b72e-110">Attributes</span></span>  
  
|<span data-ttu-id="1b72e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1b72e-111">Attribute</span></span>|<span data-ttu-id="1b72e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1b72e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b72e-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="1b72e-113">enabled</span></span>|<span data-ttu-id="1b72e-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1b72e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1b72e-115">Określa, czy włączyć wymuszanie wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodna z trybem FIPS.</span><span class="sxs-lookup"><span data-stu-id="1b72e-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1b72e-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1b72e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="1b72e-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="1b72e-117">Value</span></span>|<span data-ttu-id="1b72e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1b72e-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="1b72e-119">Jeśli komputer jest skonfigurowany do wymagają algorytmów kryptograficznych jako zgodny ze standardem FIPS, wymóg ten jest wymuszany.</span><span class="sxs-lookup"><span data-stu-id="1b72e-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="1b72e-120">Jeśli klasa implementuje algorytm, który nie jest zgodna z trybem FIPS, konstruktory lub `Create` metody tej klasy zgłaszają wyjątki, gdy są uruchamiane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1b72e-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="1b72e-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1b72e-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="1b72e-122">Algorytmy kryptograficzne, które są używane przez aplikację nie są wymagane do zapewnienia zgodności ze standardem FIPS, niezależnie od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="1b72e-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b72e-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b72e-123">Child Elements</span></span>  
 <span data-ttu-id="1b72e-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="1b72e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b72e-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b72e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1b72e-126">Element</span><span class="sxs-lookup"><span data-stu-id="1b72e-126">Element</span></span>|<span data-ttu-id="1b72e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="1b72e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1b72e-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b72e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1b72e-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1b72e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b72e-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b72e-130">Remarks</span></span>  
 <span data-ttu-id="1b72e-131">Począwszy od programu .NET Framework 2.0, tworzenie klas, które implementują algorytmy kryptograficzne, zależy od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="1b72e-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="1b72e-132">Jeśli komputer jest skonfigurowany do żądania algorytmów do zapewnienia zgodności ze standardem FIPS, a klasa implementuje algorytm, który nie jest zgodna z trybem FIPS, wszelkie próby utworzenia wystąpienia tej klasy zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1b72e-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="1b72e-133">Konstruktory throw <xref:System.InvalidOperationException> wyjątek, i `Create` metod generują <xref:System.Reflection.TargetInvocationException> wyjątek z wewnętrznego <xref:System.InvalidOperationException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1b72e-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="1b72e-134">Jeśli aplikacja działa na komputerach, na których konfiguracje wymagają zgodności z trybem FIPS, a Twoja aplikacja używa algorytmu, który nie jest zgodna z trybem FIPS, można użyć tego elementu w pliku konfiguracji aby zapobiec środowisko uruchomieniowe języka wspólnego (CLR) z Wymuszanie zgodności ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="1b72e-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="1b72e-135">Ten element został wprowadzony w [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b72e-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b72e-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b72e-136">Example</span></span>  
 <span data-ttu-id="1b72e-137">Poniższy przykład pokazuje, jak uniemożliwić CLR Wymuszanie zgodności ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="1b72e-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b72e-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b72e-138">See also</span></span>

- [<span data-ttu-id="1b72e-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1b72e-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="1b72e-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1b72e-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="1b72e-141">Model kryptografii</span><span class="sxs-lookup"><span data-stu-id="1b72e-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
