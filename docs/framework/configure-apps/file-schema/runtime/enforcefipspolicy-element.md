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
ms.openlocfilehash: f90abf9f6c2bc0aed2cf01558b2c0cca4e967e81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252643"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="f6de8-102">\<enforceFIPSPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="f6de8-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="f6de8-103">Określa, czy należy wymusić wymaganie konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne z FIPS (Federal Information Processing Standards).</span><span class="sxs-lookup"><span data-stu-id="f6de8-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
<span data-ttu-id="f6de8-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6de8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f6de8-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6de8-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f6de8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy>**</span><span class="sxs-lookup"><span data-stu-id="f6de8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6de8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6de8-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6de8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6de8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f6de8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6de8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6de8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6de8-110">Attributes</span></span>  
  
|<span data-ttu-id="f6de8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6de8-111">Attribute</span></span>|<span data-ttu-id="f6de8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f6de8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6de8-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="f6de8-113">enabled</span></span>|<span data-ttu-id="f6de8-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f6de8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f6de8-115">Określa, czy należy włączyć wymuszanie wymagania konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="f6de8-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f6de8-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="f6de8-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f6de8-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="f6de8-117">Value</span></span>|<span data-ttu-id="f6de8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f6de8-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="f6de8-119">Jeśli komputer jest skonfigurowany tak, aby wymagania algorytmów kryptograficznych były zgodne ze standardem FIPS, to wymaganie jest wymuszane.</span><span class="sxs-lookup"><span data-stu-id="f6de8-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="f6de8-120">Jeśli klasa implementuje algorytm, który nie jest zgodny z FIPS, konstruktory lub `Create` metody dla tej klasy generują wyjątki, gdy są uruchamiane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f6de8-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="f6de8-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="f6de8-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="f6de8-122">Algorytmy kryptograficzne używane przez aplikację nie są wymagane do zgodności ze standardem FIPS, niezależnie od konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="f6de8-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6de8-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6de8-123">Child Elements</span></span>  
 <span data-ttu-id="f6de8-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="f6de8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6de8-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6de8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f6de8-126">Element</span><span class="sxs-lookup"><span data-stu-id="f6de8-126">Element</span></span>|<span data-ttu-id="f6de8-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f6de8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f6de8-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6de8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f6de8-129">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f6de8-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6de8-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6de8-130">Remarks</span></span>  
 <span data-ttu-id="f6de8-131">Począwszy od .NET Framework 2,0, tworzenie klas implementujących algorytmy kryptograficzne jest kontrolowane przez konfigurację komputera.</span><span class="sxs-lookup"><span data-stu-id="f6de8-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="f6de8-132">Jeśli komputer jest skonfigurowany tak, aby wymagał zgodności algorytmów z FIPS, a Klasa implementuje algorytm, który nie jest zgodny ze standardem FIPS, każda próba utworzenia wystąpienia tej klasy zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f6de8-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="f6de8-133">Konstruktory zgłaszają `Create` <xref:System.Reflection.TargetInvocationException> <xref:System.InvalidOperationException> wyjątek, a metody zgłaszają wyjątek z wyjątkiem wewnętrznym. <xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="f6de8-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="f6de8-134">Jeśli aplikacja jest uruchamiana na komputerach, których konfiguracje wymagają zgodności ze standardem FIPS, a aplikacja używa algorytmu, który nie jest zgodny z FIPS, można użyć tego elementu w pliku konfiguracji, aby uniemożliwić środowisko uruchomieniowe języka wspólnego (CLR) z Wymuszanie zgodności ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="f6de8-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="f6de8-135">Ten element został wprowadzony w dodatku Service Pack 1 .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f6de8-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6de8-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6de8-136">Example</span></span>  
 <span data-ttu-id="f6de8-137">Poniższy przykład pokazuje, jak uniemożliwić środowisku CLR Wymuszanie zgodności ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="f6de8-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6de8-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6de8-138">See also</span></span>

- [<span data-ttu-id="f6de8-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f6de8-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f6de8-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f6de8-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f6de8-141">Model kryptografii</span><span class="sxs-lookup"><span data-stu-id="f6de8-141">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
