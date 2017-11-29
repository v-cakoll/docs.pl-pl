---
title: "&lt;oidentry —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 12c3b87f1cec72798ea92357f34ecc25b7e6edcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltoidentrygt-element"></a><span data-ttu-id="0a9b0-102">&lt;oidentry —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="0a9b0-102">&lt;oidEntry&gt; Element</span></span>
<span data-ttu-id="0a9b0-103">Mapuje ASN.1 identyfikatora obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="0a9b0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0a9b0-104">\<configuration></span></span>  
<span data-ttu-id="0a9b0-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="0a9b0-105">\<mscorlib></span></span>  
<span data-ttu-id="0a9b0-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="0a9b0-106">\<cryptographySettings></span></span>  
<span data-ttu-id="0a9b0-107">\<oidmap — ></span><span class="sxs-lookup"><span data-stu-id="0a9b0-107">\<oidMap></span></span>  
<span data-ttu-id="0a9b0-108">\<oidentry — ></span><span class="sxs-lookup"><span data-stu-id="0a9b0-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a9b0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a9b0-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a9b0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0a9b0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a9b0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a9b0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0a9b0-112">Attributes</span></span>  
  
|<span data-ttu-id="0a9b0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0a9b0-113">Attribute</span></span>|<span data-ttu-id="0a9b0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0a9b0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a9b0-115">**IDENTYFIKATOR OID**</span><span class="sxs-lookup"><span data-stu-id="0a9b0-115">**OID**</span></span>|<span data-ttu-id="0a9b0-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0a9b0-117">Określa identyfikator OID ASN.1 odpowiadający algorytm zaimplementowany przez klasę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="0a9b0-118">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="0a9b0-118">**name**</span></span>|<span data-ttu-id="0a9b0-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="0a9b0-120">Określa wartość **nazwa** atrybutu w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a9b0-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0a9b0-121">Child Elements</span></span>  
 <span data-ttu-id="0a9b0-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a9b0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0a9b0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0a9b0-124">Element</span><span class="sxs-lookup"><span data-stu-id="0a9b0-124">Element</span></span>|<span data-ttu-id="0a9b0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0a9b0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0a9b0-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0a9b0-127">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="0a9b0-128">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="0a9b0-129">Zawiera ASN.1 obiektu (OID), identyfikator mapowania do klasy.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a9b0-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a9b0-130">Remarks</span></span>  
 <span data-ttu-id="0a9b0-131">Identyfikatory obiektów ASN.1 zidentyfikować algorytmów w niektórych formatach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="0a9b0-132">Mapowanie identyfikatorów obiektów do przyjazne nazwy dla algorytmów, który chcesz zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a9b0-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a9b0-133">Example</span></span>  
 <span data-ttu-id="0a9b0-134">Poniższy przykład przedstawia użycie  **\<oidentry — >** element do mapowania identyfikator obiektu algorytmu wyznaczania wartości skrótu RIPEMD 160 implementację tego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="0a9b0-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a9b0-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a9b0-135">See Also</span></span>  
 [<span data-ttu-id="0a9b0-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0a9b0-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0a9b0-137">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="0a9b0-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="0a9b0-138">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="0a9b0-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="0a9b0-139">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="0a9b0-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="0a9b0-140">Mapowanie identyfikatorów obiektów na algorytmy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="0a9b0-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
