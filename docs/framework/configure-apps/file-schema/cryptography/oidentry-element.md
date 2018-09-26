---
title: '&lt;oidentry —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c5be6ef95693f274e5cb2002e5642d5e58a7661a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206180"
---
# <a name="ltoidentrygt-element"></a><span data-ttu-id="f399f-102">&lt;oidentry —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="f399f-102">&lt;oidEntry&gt; Element</span></span>
<span data-ttu-id="f399f-103">Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="f399f-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="f399f-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f399f-104">\<configuration></span></span>  
<span data-ttu-id="f399f-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="f399f-105">\<mscorlib></span></span>  
<span data-ttu-id="f399f-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="f399f-106">\<cryptographySettings></span></span>  
<span data-ttu-id="f399f-107">\<oidmap — ></span><span class="sxs-lookup"><span data-stu-id="f399f-107">\<oidMap></span></span>  
<span data-ttu-id="f399f-108">\<oidentry — ></span><span class="sxs-lookup"><span data-stu-id="f399f-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f399f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f399f-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f399f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f399f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f399f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f399f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f399f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f399f-112">Attributes</span></span>  
  
|<span data-ttu-id="f399f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f399f-113">Attribute</span></span>|<span data-ttu-id="f399f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f399f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f399f-115">**IDENTYFIKATOR OID**</span><span class="sxs-lookup"><span data-stu-id="f399f-115">**OID**</span></span>|<span data-ttu-id="f399f-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f399f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f399f-117">Określa identyfikator OID ASN.1 odpowiadający algorytm implementowane przez klasy.</span><span class="sxs-lookup"><span data-stu-id="f399f-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="f399f-118">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f399f-118">**name**</span></span>|<span data-ttu-id="f399f-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f399f-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="f399f-120">Określa wartość dla **nazwa** atrybutu w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="f399f-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f399f-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f399f-121">Child Elements</span></span>  
 <span data-ttu-id="f399f-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="f399f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f399f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f399f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f399f-124">Element</span><span class="sxs-lookup"><span data-stu-id="f399f-124">Element</span></span>|<span data-ttu-id="f399f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f399f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f399f-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f399f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f399f-127">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="f399f-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="f399f-128">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="f399f-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="f399f-129">Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.</span><span class="sxs-lookup"><span data-stu-id="f399f-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f399f-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f399f-130">Remarks</span></span>  
 <span data-ttu-id="f399f-131">Identyfikatory obiektów ASN.1 zidentyfikować algorytmów w niektórych formatach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="f399f-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="f399f-132">Mapowanie identyfikatorów obiektów na przyjazne nazwy dla algorytmów, który chcesz zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="f399f-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f399f-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f399f-133">Example</span></span>  
 <span data-ttu-id="f399f-134">Poniższy przykład pokazuje, jak używać  **\<oidentry — >** element do mapy identyfikator obiektu algorytmu wyznaczania wartości skrótu RIPEMD 160 implementacji tego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="f399f-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f399f-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f399f-135">See Also</span></span>  
 [<span data-ttu-id="f399f-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f399f-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f399f-137">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="f399f-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="f399f-138">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="f399f-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="f399f-139">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="f399f-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="f399f-140">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="f399f-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
