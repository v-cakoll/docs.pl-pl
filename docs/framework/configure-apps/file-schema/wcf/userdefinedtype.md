---
title: '&lt;userDefinedType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bb67a585d7abf3e885c483145215ed4fb9f92be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserdefinedtypegt"></a><span data-ttu-id="9d6c0-102">&lt;userDefinedType&gt;</span><span class="sxs-lookup"><span data-stu-id="9d6c0-102">&lt;userDefinedType&gt;</span></span>
<span data-ttu-id="9d6c0-103">Reprezentuje użytkownika zdefiniowany typ (UDT), które ma być zawarty w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-103">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="9d6c0-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9d6c0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d6c0-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="9d6c0-105">\<comContracts></span></span>  
<span data-ttu-id="9d6c0-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="9d6c0-106">\<comContract></span></span>  
<span data-ttu-id="9d6c0-107">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="9d6c0-107">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6c0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d6c0-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d6c0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d6c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9d6c0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d6c0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d6c0-111">Attributes</span></span>  
  
|<span data-ttu-id="9d6c0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9d6c0-112">Attribute</span></span>|<span data-ttu-id="9d6c0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9d6c0-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9d6c0-114">Opcjonalny atrybut, który zawiera ciąg, który zawiera czytelną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-114">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="9d6c0-115">To nie jest używany przez środowisko uruchomieniowe, ale pomaga czytnik do rozróżniania typów.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-115">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="9d6c0-116">Ciąg GUID identyfikujący określonego typu UDT w ramach z zarejestrowaną biblioteką typów.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-116">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="9d6c0-117">Ciąg GUID identyfikujący zarejestrowaną bibliotekę typu, który definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-117">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="9d6c0-118">Ciąg, który identyfikuje wersję biblioteki typu, który definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-118">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d6c0-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d6c0-119">Child Elements</span></span>  
 <span data-ttu-id="9d6c0-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d6c0-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d6c0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9d6c0-122">Element</span><span class="sxs-lookup"><span data-stu-id="9d6c0-122">Element</span></span>|<span data-ttu-id="9d6c0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9d6c0-123">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="9d6c0-124">Kolekcja `userDefinedType` elementów.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-124">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6c0-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d6c0-125">Remarks</span></span>  
 <span data-ttu-id="9d6c0-126">Środowiska uruchomieniowego integracji COM + tworzy usług, sprawdzając, czy biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-126">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="9d6c0-127">Gdy składnik modelu COM + zawiera metody, które przekazują wariant, system nie może określić rzeczywiste typy do przekazania przed środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-127">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="9d6c0-128">W związku z tym przy próbie przekazania użytkownika zdefiniowany typ (UDT) w ramach WARIANTU go nie działa, ponieważ nie jest znanym typem do serializacji.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-128">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="9d6c0-129">Aby obejść ten problem, można dodać typów do pliku konfiguracji, tak aby mogły być uwzględniana jako znane typy kontraktu odpowiednią usługę.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-129">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="9d6c0-130">Aby to zrobić, należy jednoznacznie zidentyfikować UDT i kontraktem (kontraktami), oznacza to, oryginalny interfejsy modelu COM, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-130">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="9d6c0-131">W poniższym przykładzie pokazano, dodawanie dwóch określonych typów do <`userDefinedTypes`> pliku konfiguracji, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-131">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="9d6c0-132">Podczas inicjowania usługi integracji środowiska uruchomieniowego odwołuje się do określonych typów i dodaje je do kolekcji znanych typów dla określonego umów.</span><span class="sxs-lookup"><span data-stu-id="9d6c0-132">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6c0-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d6c0-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [<span data-ttu-id="9d6c0-134">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="9d6c0-134">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="9d6c0-135">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="9d6c0-135">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="9d6c0-136">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="9d6c0-136">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
