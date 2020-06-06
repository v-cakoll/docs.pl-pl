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
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088549"
---
# <a name="oidentry-element"></a><span data-ttu-id="a1868-102">\<oidEntry> Element</span><span class="sxs-lookup"><span data-stu-id="a1868-102">\<oidEntry> Element</span></span>
<span data-ttu-id="a1868-103">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="a1868-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="a1868-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1868-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1868-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a1868-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a1868-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a1868-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1868-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a1868-107">Attributes</span></span>  
  
|<span data-ttu-id="a1868-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a1868-108">Attribute</span></span>|<span data-ttu-id="a1868-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a1868-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1868-110">**OID**</span><span class="sxs-lookup"><span data-stu-id="a1868-110">**OID**</span></span>|<span data-ttu-id="a1868-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a1868-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a1868-112">Określa identyfikator OID ASN. 1 odpowiadający algorytmowi zaimplementowanemu przez klasę.</span><span class="sxs-lookup"><span data-stu-id="a1868-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="a1868-113">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="a1868-113">**name**</span></span>|<span data-ttu-id="a1868-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a1868-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a1868-115">Określa wartość atrybutu **name** w [\<nameEntry>](nameentry-element.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="a1868-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1868-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a1868-116">Child Elements</span></span>  
 <span data-ttu-id="a1868-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a1868-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1868-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a1868-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a1868-119">Element</span><span class="sxs-lookup"><span data-stu-id="a1868-119">Element</span></span>|<span data-ttu-id="a1868-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a1868-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a1868-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1868-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="a1868-122">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="a1868-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="a1868-123">Zawiera `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="a1868-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="a1868-124">Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.</span><span class="sxs-lookup"><span data-stu-id="a1868-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1868-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1868-125">Remarks</span></span>  
 <span data-ttu-id="a1868-126">Identyfikatory obiektu ASN. 1 identyfikują algorytmy w niektórych formatach kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="a1868-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="a1868-127">Mapuj identyfikatory obiektów na przyjazne nazwy dla algorytmów, które chcesz zidentyfikować.</span><span class="sxs-lookup"><span data-stu-id="a1868-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1868-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1868-128">Example</span></span>  
 <span data-ttu-id="a1868-129">Poniższy przykład pokazuje, jak używać **\<oidEntry>** elementu do mapowania identyfikatora obiektu dla algorytmu wyznaczania wartości skrótu RIPEMD-160 do implementacji algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a1868-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1868-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1868-130">See also</span></span>

- [<span data-ttu-id="a1868-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a1868-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a1868-132">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="a1868-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a1868-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="a1868-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="a1868-134">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="a1868-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="a1868-135">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="a1868-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
