---
title: <enforceFIPSPolicy>, element
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c13dd2f00e08539d2ba502058c74aa4a1525e3ff
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816115"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="31926-102">\<enforceFIPSPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="31926-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="31926-103">Określa, czy do wymuszania wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardów FIPS (Federal Information).</span><span class="sxs-lookup"><span data-stu-id="31926-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="31926-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="31926-104">\<configuration> Element</span></span>  
<span data-ttu-id="31926-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="31926-105">\<runtime> Element</span></span>  
<span data-ttu-id="31926-106">\<enforceFIPSPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="31926-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31926-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="31926-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31926-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="31926-108">Attributes and Elements</span></span>  
 <span data-ttu-id="31926-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="31926-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31926-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="31926-110">Attributes</span></span>  
  
|<span data-ttu-id="31926-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="31926-111">Attribute</span></span>|<span data-ttu-id="31926-112">Opis</span><span class="sxs-lookup"><span data-stu-id="31926-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31926-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="31926-113">enabled</span></span>|<span data-ttu-id="31926-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="31926-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="31926-115">Określa, czy włączyć wymuszanie wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodna z trybem FIPS.</span><span class="sxs-lookup"><span data-stu-id="31926-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="31926-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="31926-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="31926-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="31926-117">Value</span></span>|<span data-ttu-id="31926-118">Opis</span><span class="sxs-lookup"><span data-stu-id="31926-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="31926-119">Jeśli komputer jest skonfigurowany do wymagają algorytmów kryptograficznych jako zgodny ze standardem FIPS, wymóg ten jest wymuszany.</span><span class="sxs-lookup"><span data-stu-id="31926-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="31926-120">Jeśli klasa implementuje algorytm, który nie jest zgodna z trybem FIPS, konstruktory lub `Create` metody tej klasy zgłaszają wyjątki, gdy są uruchamiane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="31926-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="31926-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="31926-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="31926-122">Algorytmy kryptograficzne, które są używane przez aplikację nie są wymagane do zapewnienia zgodności ze standardem FIPS, niezależnie od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="31926-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31926-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="31926-123">Child Elements</span></span>  
 <span data-ttu-id="31926-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="31926-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31926-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="31926-125">Parent Elements</span></span>  
  
|<span data-ttu-id="31926-126">Element</span><span class="sxs-lookup"><span data-stu-id="31926-126">Element</span></span>|<span data-ttu-id="31926-127">Opis</span><span class="sxs-lookup"><span data-stu-id="31926-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="31926-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31926-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="31926-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="31926-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31926-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31926-130">Remarks</span></span>  
 <span data-ttu-id="31926-131">Począwszy od programu .NET Framework 2.0, tworzenie klas, które implementują algorytmy kryptograficzne, zależy od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="31926-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="31926-132">Jeśli komputer jest skonfigurowany do żądania algorytmów do zapewnienia zgodności ze standardem FIPS, a klasa implementuje algorytm, który nie jest zgodna z trybem FIPS, wszelkie próby utworzenia wystąpienia tej klasy zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="31926-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="31926-133">Konstruktory throw <xref:System.InvalidOperationException> wyjątek, i `Create` metod generują <xref:System.Reflection.TargetInvocationException> wyjątek z wewnętrznego <xref:System.InvalidOperationException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="31926-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="31926-134">Jeśli aplikacja działa na komputerach, na których konfiguracje wymagają zgodności z trybem FIPS, a Twoja aplikacja używa algorytmu, który nie jest zgodna z trybem FIPS, można użyć tego elementu w pliku konfiguracji aby zapobiec środowisko uruchomieniowe języka wspólnego (CLR) z Wymuszanie zgodności ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="31926-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="31926-135">Ten element został wprowadzony w .NET Framework 2.0 z dodatkiem Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="31926-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31926-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="31926-136">Example</span></span>  
 <span data-ttu-id="31926-137">Poniższy przykład pokazuje, jak uniemożliwić CLR Wymuszanie zgodności ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="31926-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="31926-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31926-138">See also</span></span>

- [<span data-ttu-id="31926-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="31926-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="31926-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="31926-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="31926-141">Model kryptografii</span><span class="sxs-lookup"><span data-stu-id="31926-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
