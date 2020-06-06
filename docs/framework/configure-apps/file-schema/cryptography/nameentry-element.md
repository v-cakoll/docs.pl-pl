---
title: <nameEntry> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71699779"
---
# <a name="nameentry-element"></a><span data-ttu-id="ac323-102">\<nameEntry> Element</span><span class="sxs-lookup"><span data-stu-id="ac323-102">\<nameEntry> Element</span></span>
<span data-ttu-id="ac323-103">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="ac323-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="ac323-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac323-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac323-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ac323-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ac323-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ac323-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac323-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac323-107">Attributes</span></span>  
  
|<span data-ttu-id="ac323-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ac323-108">Attribute</span></span>|<span data-ttu-id="ac323-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ac323-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac323-110">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="ac323-110">**name**</span></span>|<span data-ttu-id="ac323-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ac323-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac323-112">Określa przyjazną nazwę algorytmu, który implementuje Klasa kryptografii.</span><span class="sxs-lookup"><span data-stu-id="ac323-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="ac323-113">**określonej**</span><span class="sxs-lookup"><span data-stu-id="ac323-113">**class**</span></span>|<span data-ttu-id="ac323-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ac323-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac323-115">Określa wartość atrybutu **name** w [\<cryptoClass>](cryptoclass-element.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="ac323-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac323-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ac323-116">Child Elements</span></span>  
 <span data-ttu-id="ac323-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="ac323-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac323-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ac323-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ac323-119">Element</span><span class="sxs-lookup"><span data-stu-id="ac323-119">Element</span></span>|<span data-ttu-id="ac323-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ac323-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac323-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac323-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="ac323-122">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ac323-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac323-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac323-123">Remarks</span></span>  
 <span data-ttu-id="ac323-124">Atrybut **name** może być nazwą jednej z klas abstrakcyjnych znalezionych w <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ac323-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="ac323-125">Po wywołaniu metody **Create** dla abstrakcyjnej klasy kryptograficznej, nazwa klasy abstrakcyjnej jest przenoszona do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ac323-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="ac323-126">Funkcja " **Nofrom** " zwraca wystąpienie typu wskazane przez atrybut **Class** .</span><span class="sxs-lookup"><span data-stu-id="ac323-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="ac323-127">Jeśli atrybut **name** jest krótką nazwą, taką jak RSA, można **użyć tej nazwy podczas wywoływania metody.**</span><span class="sxs-lookup"><span data-stu-id="ac323-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac323-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac323-128">Example</span></span>  
 <span data-ttu-id="ac323-129">Poniższy przykład pokazuje, jak użyć elementu, **\<nameEntry>** Aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="ac323-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ac323-130">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyć <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ac323-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac323-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac323-131">See also</span></span>

- [<span data-ttu-id="ac323-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ac323-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ac323-133">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="ac323-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac323-134">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="ac323-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ac323-135">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="ac323-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
