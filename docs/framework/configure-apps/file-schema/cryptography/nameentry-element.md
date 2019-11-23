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
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699779"
---
# <a name="nameentry-element"></a><span data-ttu-id="05fb2-102">\<element > nameEntry</span><span class="sxs-lookup"><span data-stu-id="05fb2-102">\<nameEntry> Element</span></span>
<span data-ttu-id="05fb2-103">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="05fb2-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[<span data-ttu-id="05fb2-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="05fb2-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="05fb2-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="05fb2-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="05fb2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="05fb2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="05fb2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="05fb2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="05fb2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="05fb2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05fb2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="05fb2-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05fb2-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05fb2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05fb2-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05fb2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05fb2-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05fb2-112">Attributes</span></span>  
  
|<span data-ttu-id="05fb2-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05fb2-113">Attribute</span></span>|<span data-ttu-id="05fb2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="05fb2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05fb2-115">**name**</span><span class="sxs-lookup"><span data-stu-id="05fb2-115">**name**</span></span>|<span data-ttu-id="05fb2-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="05fb2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="05fb2-117">Określa przyjazną nazwę algorytmu, który implementuje Klasa kryptografii.</span><span class="sxs-lookup"><span data-stu-id="05fb2-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="05fb2-118">**class**</span><span class="sxs-lookup"><span data-stu-id="05fb2-118">**class**</span></span>|<span data-ttu-id="05fb2-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="05fb2-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="05fb2-120">Określa wartość atrybutu **name** w [\<cryptoClass >](cryptoclass-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="05fb2-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05fb2-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05fb2-121">Child Elements</span></span>  
 <span data-ttu-id="05fb2-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="05fb2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05fb2-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05fb2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="05fb2-124">Element</span><span class="sxs-lookup"><span data-stu-id="05fb2-124">Element</span></span>|<span data-ttu-id="05fb2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="05fb2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="05fb2-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05fb2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="05fb2-127">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="05fb2-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05fb2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05fb2-128">Remarks</span></span>  
 <span data-ttu-id="05fb2-129">Atrybut **name** może być nazwą jednej z klas abstrakcyjnych znalezionych w przestrzeni nazw <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="05fb2-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="05fb2-130">Po wywołaniu metody **Create** dla abstrakcyjnej klasy kryptograficznej, nazwa klasy abstrakcyjnej jest przenoszona do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>.</span><span class="sxs-lookup"><span data-stu-id="05fb2-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="05fb2-131">Funkcja " **Nofrom** " zwraca wystąpienie typu wskazane przez atrybut **Class** .</span><span class="sxs-lookup"><span data-stu-id="05fb2-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="05fb2-132">Jeśli atrybut **name** jest krótką nazwą, taką jak RSA, można **użyć tej nazwy podczas wywoływania metody.**</span><span class="sxs-lookup"><span data-stu-id="05fb2-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05fb2-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="05fb2-133">Example</span></span>  
 <span data-ttu-id="05fb2-134">Poniższy przykład pokazuje, jak używać elementu **\<nameEntry >** , aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="05fb2-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="05fb2-135">Następnie można przekazać ciąg "RSA" do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> i użyć metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> do zwrócenia obiektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="05fb2-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05fb2-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05fb2-136">See also</span></span>

- [<span data-ttu-id="05fb2-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05fb2-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="05fb2-138">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="05fb2-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="05fb2-139">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="05fb2-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="05fb2-140">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="05fb2-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
