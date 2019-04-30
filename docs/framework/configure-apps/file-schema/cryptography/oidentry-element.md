---
title: <oidEntry>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: c686d2b99ad66aec753a356b09fa3c7151193808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674756"
---
# <a name="oidentry-element"></a><span data-ttu-id="2b0d7-102">\<oidEntry> Element</span><span class="sxs-lookup"><span data-stu-id="2b0d7-102">\<oidEntry> Element</span></span>
<span data-ttu-id="2b0d7-103">Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="2b0d7-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="2b0d7-104">\<configuration></span></span>  
<span data-ttu-id="2b0d7-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="2b0d7-105">\<mscorlib></span></span>  
<span data-ttu-id="2b0d7-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="2b0d7-106">\<cryptographySettings></span></span>  
<span data-ttu-id="2b0d7-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="2b0d7-107">\<oidMap></span></span>  
<span data-ttu-id="2b0d7-108">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="2b0d7-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b0d7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b0d7-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b0d7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b0d7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b0d7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b0d7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b0d7-112">Attributes</span></span>  
  
|<span data-ttu-id="2b0d7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2b0d7-113">Attribute</span></span>|<span data-ttu-id="2b0d7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2b0d7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b0d7-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="2b0d7-115">**OID**</span></span>|<span data-ttu-id="2b0d7-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b0d7-117">Określa identyfikator OID ASN.1 odpowiadający algorytm implementowane przez klasy.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="2b0d7-118">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="2b0d7-118">**name**</span></span>|<span data-ttu-id="2b0d7-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b0d7-120">Określa wartość dla **nazwa** atrybutu w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b0d7-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b0d7-121">Child Elements</span></span>  
 <span data-ttu-id="2b0d7-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b0d7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b0d7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2b0d7-124">Element</span><span class="sxs-lookup"><span data-stu-id="2b0d7-124">Element</span></span>|<span data-ttu-id="2b0d7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2b0d7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b0d7-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="2b0d7-127">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="2b0d7-128">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="2b0d7-129">Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b0d7-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b0d7-130">Remarks</span></span>  
 <span data-ttu-id="2b0d7-131">Identyfikatory obiektów ASN.1 zidentyfikować algorytmów w niektórych formatach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="2b0d7-132">Mapowanie identyfikatorów obiektów na przyjazne nazwy dla algorytmów, który chcesz zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b0d7-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b0d7-133">Example</span></span>  
 <span data-ttu-id="2b0d7-134">Poniższy przykład pokazuje, jak używać  **\<oidentry — >** element do mapy identyfikator obiektu algorytmu wyznaczania wartości skrótu RIPEMD 160 implementacji tego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2b0d7-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b0d7-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b0d7-135">See also</span></span>

- [<span data-ttu-id="2b0d7-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2b0d7-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2b0d7-137">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="2b0d7-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="2b0d7-138">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="2b0d7-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="2b0d7-139">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="2b0d7-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="2b0d7-140">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="2b0d7-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
