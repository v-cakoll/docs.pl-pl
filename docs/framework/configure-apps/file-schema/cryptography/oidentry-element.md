---
title: <oidEntry> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: eed2a4d06906d2928be62aed20a75484c3eea946
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699768"
---
# <a name="oidentry-element"></a><span data-ttu-id="55468-102">\<oidEntry > elementu</span><span class="sxs-lookup"><span data-stu-id="55468-102">\<oidEntry> Element</span></span>
<span data-ttu-id="55468-103">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="55468-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
[<span data-ttu-id="55468-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="55468-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="55468-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="55468-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="55468-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="55468-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="55468-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="55468-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="55468-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 **\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="55468-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55468-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="55468-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55468-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55468-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55468-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55468-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55468-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55468-112">Attributes</span></span>  
  
|<span data-ttu-id="55468-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="55468-113">Attribute</span></span>|<span data-ttu-id="55468-114">Opis</span><span class="sxs-lookup"><span data-stu-id="55468-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55468-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="55468-115">**OID**</span></span>|<span data-ttu-id="55468-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="55468-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="55468-117">Określa identyfikator OID ASN. 1 odpowiadający algorytmowi zaimplementowanemu przez klasę.</span><span class="sxs-lookup"><span data-stu-id="55468-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="55468-118">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="55468-118">**name**</span></span>|<span data-ttu-id="55468-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="55468-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="55468-120">Określa wartość atrybutu **name** w tagu [\<nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="55468-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55468-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55468-121">Child Elements</span></span>  
 <span data-ttu-id="55468-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="55468-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55468-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55468-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55468-124">Element</span><span class="sxs-lookup"><span data-stu-id="55468-124">Element</span></span>|<span data-ttu-id="55468-125">Opis</span><span class="sxs-lookup"><span data-stu-id="55468-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55468-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55468-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="55468-127">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="55468-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="55468-128">Zawiera element `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="55468-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="55468-129">Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.</span><span class="sxs-lookup"><span data-stu-id="55468-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55468-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55468-130">Remarks</span></span>  
 <span data-ttu-id="55468-131">Identyfikatory obiektu ASN. 1 identyfikują algorytmy w niektórych formatach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="55468-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="55468-132">Mapuj identyfikatory obiektów na przyjazne nazwy dla algorytmów, które chcesz zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="55468-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55468-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="55468-133">Example</span></span>  
 <span data-ttu-id="55468-134">Poniższy przykład pokazuje, jak używać elementu **\<oidEntry >** do mapowania identyfikatora obiektu dla algorytmu wyznaczania wartości skrótu RIPEMD-160 do implementacji algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="55468-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55468-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55468-135">See also</span></span>

- [<span data-ttu-id="55468-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55468-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="55468-137">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="55468-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55468-138">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="55468-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="55468-139">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="55468-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="55468-140">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="55468-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
