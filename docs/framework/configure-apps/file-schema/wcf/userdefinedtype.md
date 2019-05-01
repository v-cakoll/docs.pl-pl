---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 46beb88cedf051ed1683161b6ed9b37273ed01f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769840"
---
# <a name="userdefinedtype"></a><span data-ttu-id="a2cd4-101">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="a2cd4-101">\<userDefinedType></span></span>
<span data-ttu-id="a2cd4-102">Reprezentuje użytkownika zdefiniowany typ (UDT), które ma być zawarty w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="a2cd4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a2cd4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a2cd4-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a2cd4-104">\<comContracts></span></span>  
<span data-ttu-id="a2cd4-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="a2cd4-105">\<comContract></span></span>  
<span data-ttu-id="a2cd4-106">\<userDefinedTypes></span><span class="sxs-lookup"><span data-stu-id="a2cd4-106">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2cd4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2cd4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2cd4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a2cd4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a2cd4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2cd4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2cd4-110">Attributes</span></span>  
  
|<span data-ttu-id="a2cd4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a2cd4-111">Attribute</span></span>|<span data-ttu-id="a2cd4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a2cd4-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a2cd4-113">Opcjonalny atrybut, który zawiera ciąg dostarczający czytelną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-113">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="a2cd4-114">To nie jest używany przez środowisko uruchomieniowe, ale pomaga czytnik do rozróżniania typów.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-114">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="a2cd4-115">Ciąg identyfikatora GUID, który identyfikuje określonego typu UDT w ramach z zarejestrowaną biblioteką typów.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-115">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="a2cd4-116">Ciąg GUID identyfikujący zarejestrowaną bibliotekę typu, który definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-116">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="a2cd4-117">Ciąg, który identyfikuje typ wersji biblioteki, który definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-117">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2cd4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2cd4-118">Child Elements</span></span>  
 <span data-ttu-id="a2cd4-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2cd4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2cd4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a2cd4-121">Element</span><span class="sxs-lookup"><span data-stu-id="a2cd4-121">Element</span></span>|<span data-ttu-id="a2cd4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a2cd4-122">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="a2cd4-123">Kolekcja `userDefinedType` elementów.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-123">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2cd4-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2cd4-124">Remarks</span></span>  
 <span data-ttu-id="a2cd4-125">Środowisko uruchomieniowe integracji modelu COM + tworzy usług, sprawdzając biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-125">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="a2cd4-126">Gdy składnik COM + zawiera metody, zaliczonych wariant, system nie może określić rzeczywiste typy, które mają być przekazane przed środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-126">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="a2cd4-127">W związku z tym spróbujesz przekazać użytkownika zdefiniowany typ (UDT) w ramach WARIANTU, go nie powiedzie się, ponieważ nie jest znany typ do serializacji.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-127">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="a2cd4-128">Aby obejść ten problem, można dodać typów zdefiniowanych przez użytkownika do pliku konfiguracji, tak aby mogły być dołączony jako znanych typów w kontrakcie odpowiednią usługę.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-128">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="a2cd4-129">Aby to zrobić, należy jednoznacznie zidentyfikować UDT i kontraktami, oznacza to, oryginalnym interfejsy COM, w celu zastosowania.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-129">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="a2cd4-130">W poniższym przykładzie pokazano, dodanie dwóch określonych typów do <`userDefinedTypes`> sekcji w pliku konfiguracji, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-130">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
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
  
 <span data-ttu-id="a2cd4-131">Podczas inicjowania usługi integration runtime odwołuje się do określonych typów i dodaje je do kolekcji znanych typów dla określonej umowy.</span><span class="sxs-lookup"><span data-stu-id="a2cd4-131">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2cd4-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2cd4-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="a2cd4-133">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a2cd4-133">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="a2cd4-134">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="a2cd4-134">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a2cd4-135">Instrukcje: Konfigurowanie ustawień usługi COM +</span><span class="sxs-lookup"><span data-stu-id="a2cd4-135">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
