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
ms.openlocfilehash: 013994e36c4c63410a753967cbac92c38783ae62
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659588"
---
# <a name="oidentry-element"></a><span data-ttu-id="c0563-102">\<oidEntry, element ></span><span class="sxs-lookup"><span data-stu-id="c0563-102">\<oidEntry> Element</span></span>
<span data-ttu-id="c0563-103">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="c0563-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="c0563-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0563-104">\<configuration></span></span>  
<span data-ttu-id="c0563-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="c0563-105">\<mscorlib></span></span>  
<span data-ttu-id="c0563-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="c0563-106">\<cryptographySettings></span></span>  
<span data-ttu-id="c0563-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="c0563-107">\<oidMap></span></span>  
<span data-ttu-id="c0563-108">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="c0563-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0563-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0563-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0563-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c0563-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0563-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c0563-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0563-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0563-112">Attributes</span></span>  
  
|<span data-ttu-id="c0563-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c0563-113">Attribute</span></span>|<span data-ttu-id="c0563-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c0563-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0563-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="c0563-115">**OID**</span></span>|<span data-ttu-id="c0563-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c0563-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0563-117">Określa identyfikator OID ASN. 1 odpowiadający algorytmowi zaimplementowanemu przez klasę.</span><span class="sxs-lookup"><span data-stu-id="c0563-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="c0563-118">**name**</span><span class="sxs-lookup"><span data-stu-id="c0563-118">**name**</span></span>|<span data-ttu-id="c0563-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c0563-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0563-120">Określa wartość atrybutu **name** w [ \<tagu > nameEntry](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c0563-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0563-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c0563-121">Child Elements</span></span>  
 <span data-ttu-id="c0563-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0563-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0563-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0563-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c0563-124">Element</span><span class="sxs-lookup"><span data-stu-id="c0563-124">Element</span></span>|<span data-ttu-id="c0563-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c0563-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c0563-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0563-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c0563-127">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="c0563-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="c0563-128">`cryptographySettings` Zawiera element.</span><span class="sxs-lookup"><span data-stu-id="c0563-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="c0563-129">Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.</span><span class="sxs-lookup"><span data-stu-id="c0563-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0563-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0563-130">Remarks</span></span>  
 <span data-ttu-id="c0563-131">Identyfikatory obiektu ASN. 1 identyfikują algorytmy w niektórych formatach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="c0563-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="c0563-132">Mapuj identyfikatory obiektów na przyjazne nazwy dla algorytmów, które chcesz zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="c0563-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0563-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0563-133">Example</span></span>  
 <span data-ttu-id="c0563-134">Poniższy przykład pokazuje,  **\<** jak używać elementu oidEntry > do mapowania identyfikatora obiektu dla algorytmu wyznaczania wartości skrótu RIPEMD-160 do implementacji algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c0563-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0563-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0563-135">See also</span></span>

- [<span data-ttu-id="c0563-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0563-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c0563-137">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="c0563-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c0563-138">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="c0563-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="c0563-139">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="c0563-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="c0563-140">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="c0563-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
