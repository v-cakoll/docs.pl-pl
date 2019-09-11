---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854833"
---
# <a name="userdefinedtype"></a><span data-ttu-id="5a2ef-101">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="5a2ef-101">\<userDefinedType></span></span>
<span data-ttu-id="5a2ef-102">Reprezentuje typ zdefiniowany przez użytkownika (UDT), który ma zostać uwzględniony w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
<span data-ttu-id="5a2ef-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a2ef-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a2ef-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a2ef-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a2ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="5a2ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="5a2ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="5a2ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="5a2ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<userDefinedTypes >** ](userdefinedtypes.md)</span><span class="sxs-lookup"><span data-stu-id="5a2ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)</span></span>\
<span data-ttu-id="5a2ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userDefinedType >**</span><span class="sxs-lookup"><span data-stu-id="5a2ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a2ef-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a2ef-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a2ef-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a2ef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a2ef-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a2ef-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a2ef-112">Attributes</span></span>  
  
|<span data-ttu-id="5a2ef-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5a2ef-113">Attribute</span></span>|<span data-ttu-id="5a2ef-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5a2ef-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5a2ef-115">Opcjonalny atrybut, który zawiera ciąg, który zawiera nazwę typu, który można odczytać.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-115">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="5a2ef-116">Nie jest on używany przez środowisko uruchomieniowe, ale pomaga czytelnikowi odróżnić typy.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-116">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="5a2ef-117">Ciąg identyfikatora GUID, który identyfikuje określony typ UDT w zarejestrowanej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-117">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="5a2ef-118">Ciąg identyfikatora GUID, który identyfikuje zarejestrowanej biblioteki typów, która definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-118">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="5a2ef-119">Ciąg, który identyfikuje wersję biblioteki typów, która definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-119">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a2ef-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a2ef-120">Child Elements</span></span>  
 <span data-ttu-id="5a2ef-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a2ef-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a2ef-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5a2ef-123">Element</span><span class="sxs-lookup"><span data-stu-id="5a2ef-123">Element</span></span>|<span data-ttu-id="5a2ef-124">Opis</span><span class="sxs-lookup"><span data-stu-id="5a2ef-124">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="5a2ef-125">Kolekcja `userDefinedType` elementów.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-125">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a2ef-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a2ef-126">Remarks</span></span>  
 <span data-ttu-id="5a2ef-127">Środowisko Integration Runtime środowiska COM+ tworzy usługi, sprawdzając bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-127">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="5a2ef-128">Gdy składnik COM+ zawiera metody, które przechodzą wariant, system nie może ustalić rzeczywistych typów do przekazania przed środowiskiem uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-128">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="5a2ef-129">W związku z tym podczas próby przekazania typu zdefiniowanego przez użytkownika (UDT) w ramach WARIANTu nie powiedzie się, ponieważ nie jest to znany typ serializacji.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-129">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="5a2ef-130">Aby obejść ten problem, można dodać UDTs do pliku konfiguracji, aby można je było uwzględnić jako znane typy w odpowiednim kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-130">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="5a2ef-131">Aby to zrobić, należy jednoznacznie zidentyfikować UDT i kontrakty, czyli oryginalne interfejsy COM, które z niego korzystają.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-131">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="5a2ef-132">Poniższy przykład ilustruje dodanie dwóch konkretnych UDTs do sekcji > <`userDefinedTypes`w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-132">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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
  
 <span data-ttu-id="5a2ef-133">Po zainicjowaniu usługi środowisko Integration Runtime wyszukuje określone typy i dodaje je do kolekcji znanych typów dla określonych kontraktów.</span><span class="sxs-lookup"><span data-stu-id="5a2ef-133">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2ef-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a2ef-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="5a2ef-135">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="5a2ef-135">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="5a2ef-136">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="5a2ef-136">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5a2ef-137">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="5a2ef-137">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
