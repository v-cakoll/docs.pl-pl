---
title: <nameEntry>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 9270552245b3867f0f09741ded3f9da6a8b6c135
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664269"
---
# <a name="nameentry-element"></a><span data-ttu-id="600cd-102">\<nameEntry, element ></span><span class="sxs-lookup"><span data-stu-id="600cd-102">\<nameEntry> Element</span></span>
<span data-ttu-id="600cd-103">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="600cd-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="600cd-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="600cd-104">\<configuration></span></span>  
<span data-ttu-id="600cd-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="600cd-105">\<mscorlib></span></span>  
<span data-ttu-id="600cd-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="600cd-106">\<cryptographySettings></span></span>  
<span data-ttu-id="600cd-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="600cd-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="600cd-108">\<nameEntry></span><span class="sxs-lookup"><span data-stu-id="600cd-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600cd-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="600cd-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="600cd-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="600cd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="600cd-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="600cd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="600cd-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="600cd-112">Attributes</span></span>  
  
|<span data-ttu-id="600cd-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="600cd-113">Attribute</span></span>|<span data-ttu-id="600cd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="600cd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="600cd-115">**name**</span><span class="sxs-lookup"><span data-stu-id="600cd-115">**name**</span></span>|<span data-ttu-id="600cd-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="600cd-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="600cd-117">Określa przyjazną nazwę algorytmu, który implementuje Klasa kryptografii.</span><span class="sxs-lookup"><span data-stu-id="600cd-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="600cd-118">**class**</span><span class="sxs-lookup"><span data-stu-id="600cd-118">**class**</span></span>|<span data-ttu-id="600cd-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="600cd-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="600cd-120">Określa wartość atrybutu **name** w [ \<elemencie cryptoClass >](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="600cd-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="600cd-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="600cd-121">Child Elements</span></span>  
 <span data-ttu-id="600cd-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="600cd-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="600cd-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="600cd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="600cd-124">Element</span><span class="sxs-lookup"><span data-stu-id="600cd-124">Element</span></span>|<span data-ttu-id="600cd-125">Opis</span><span class="sxs-lookup"><span data-stu-id="600cd-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="600cd-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="600cd-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="600cd-127">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="600cd-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="600cd-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="600cd-128">Remarks</span></span>  
 <span data-ttu-id="600cd-129">Atrybut **name** może być nazwą jednej z klas abstrakcyjnych znalezionych w <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="600cd-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="600cd-130">Po wywołaniu metody **Create** dla abstrakcyjnej klasy kryptograficznej, nazwa klasy abstrakcyjnej jest przenoszona do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="600cd-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="600cd-131">Funkcja "nofrom" zwraca wystąpienie typu wskazane przez atrybut **Class** .</span><span class="sxs-lookup"><span data-stu-id="600cd-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="600cd-132">Jeśli atrybut **name** jest krótką nazwą, taką jak RSA, można użyć tej nazwy podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="600cd-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="600cd-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="600cd-133">Example</span></span>  
 <span data-ttu-id="600cd-134">Poniższy przykład pokazuje,  **\<** jak używać elementu nameEntry >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="600cd-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="600cd-135">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="600cd-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="600cd-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="600cd-136">See also</span></span>

- [<span data-ttu-id="600cd-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="600cd-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="600cd-138">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="600cd-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="600cd-139">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="600cd-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="600cd-140">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="600cd-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
