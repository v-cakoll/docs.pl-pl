---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8694f83a731363f83cb09de43214eb4b211ef5ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145070"
---
# <a name="comcontract"></a><span data-ttu-id="092c1-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="092c1-101">\<comContract></span></span>
<span data-ttu-id="092c1-102">Określa kontrakt usługi integracji COM +.</span><span class="sxs-lookup"><span data-stu-id="092c1-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="092c1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="092c1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="092c1-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="092c1-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="092c1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="092c1-105">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="092c1-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="092c1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="092c1-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="092c1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="092c1-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="092c1-108">Attributes</span></span>  
  
|<span data-ttu-id="092c1-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="092c1-109">Attribute</span></span>|<span data-ttu-id="092c1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="092c1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="092c1-111">kontrakt</span><span class="sxs-lookup"><span data-stu-id="092c1-111">contract</span></span>|<span data-ttu-id="092c1-112">Ciąg, który zawiera typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="092c1-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="092c1-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="092c1-113">name</span></span>|<span data-ttu-id="092c1-114">Ciąg, który zawiera nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="092c1-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="092c1-115">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="092c1-115">namespace</span></span>|<span data-ttu-id="092c1-116">Ciąg, który zawiera przestrzeń nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="092c1-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="092c1-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="092c1-117">requiresSession</span></span>|<span data-ttu-id="092c1-118">Wartość logiczna określająca, czy kontrakt mogą być używane tylko na powiązaniach sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="092c1-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="092c1-119">Podczas inicjowania usługi produktu integration runtime zapewnia to ustawienie jest zgodne z typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="092c1-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="092c1-120">Wyjątek jest generowany, jeśli jeden lub więcej powiązań dla kontraktu usługi są w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="092c1-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="092c1-121">Jeśli ta właściwość jest `false`i jednokierunkowe kanał jest w użyciu i istnieją [parametry out], wyjątek zostanie również wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="092c1-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="092c1-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="092c1-122">Child Elements</span></span>  
  
|<span data-ttu-id="092c1-123">Element</span><span class="sxs-lookup"><span data-stu-id="092c1-123">Element</span></span>|<span data-ttu-id="092c1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="092c1-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="092c1-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="092c1-125">persistableTypes</span></span>|<span data-ttu-id="092c1-126">Wszystkie typy stałe.</span><span class="sxs-lookup"><span data-stu-id="092c1-126">All the persistable types.</span></span>|  
|<span data-ttu-id="092c1-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="092c1-127">userDefinedTypes</span></span>|<span data-ttu-id="092c1-128">Kolekcja z użytkownika zdefiniowanych typów (UDT), które ma być zawarty w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="092c1-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="092c1-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="092c1-129">exposedMethods</span></span>|<span data-ttu-id="092c1-130">Kolekcja metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest widoczny jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="092c1-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="092c1-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="092c1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="092c1-132">Element</span><span class="sxs-lookup"><span data-stu-id="092c1-132">Element</span></span>|<span data-ttu-id="092c1-133">Opis</span><span class="sxs-lookup"><span data-stu-id="092c1-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="092c1-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="092c1-134">comContracts</span></span>|<span data-ttu-id="092c1-135">Zawiera kolekcję `comContract` elementów.</span><span class="sxs-lookup"><span data-stu-id="092c1-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="092c1-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="092c1-136">Remarks</span></span>  
 <span data-ttu-id="092c1-137">Kontrakty usług integracji modelu COM + są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw i Nazwa kontraktu jest tworzony na podstawie obsługi interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="092c1-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="092c1-138">Można jednak określić alternatywne przy użyciu `comContracts` sekcji, jak również `comContract` elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="092c1-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="092c1-139">Na przykład można użyć następującej konfiguracji do określania przestrzeni nazw, Nazwa kontraktu i typów zdefiniowanych przez użytkownika do uwzględnienia, a także inne ustawienia dla kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="092c1-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="092c1-140">Podczas inicjowania usługi określonych przestrzeni nazw i nazwy kontraktów są stosowane do opisów wygenerowanego usługi.</span><span class="sxs-lookup"><span data-stu-id="092c1-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092c1-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="092c1-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="092c1-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="092c1-142">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="092c1-143">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="092c1-143">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="092c1-144">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="092c1-144">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
