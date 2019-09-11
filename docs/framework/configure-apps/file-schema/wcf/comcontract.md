---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850026"
---
# <a name="comcontract"></a><span data-ttu-id="e9317-101">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="e9317-101">\<comContract></span></span>
<span data-ttu-id="e9317-102">Określa kontrakt usługi integracji COM+.</span><span class="sxs-lookup"><span data-stu-id="e9317-102">Specifies a COM+ integration service contract.</span></span>  
  
<span data-ttu-id="e9317-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9317-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9317-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e9317-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e9317-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="e9317-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="e9317-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<comContract >**</span><span class="sxs-lookup"><span data-stu-id="e9317-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9317-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9317-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9317-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9317-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e9317-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9317-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9317-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9317-110">Attributes</span></span>  
  
|<span data-ttu-id="e9317-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e9317-111">Attribute</span></span>|<span data-ttu-id="e9317-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e9317-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9317-113">Przedsiębiorc</span><span class="sxs-lookup"><span data-stu-id="e9317-113">contract</span></span>|<span data-ttu-id="e9317-114">Ciąg, który zawiera typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e9317-114">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="e9317-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="e9317-115">name</span></span>|<span data-ttu-id="e9317-116">Ciąg, który zawiera nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e9317-116">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="e9317-117">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e9317-117">namespace</span></span>|<span data-ttu-id="e9317-118">Ciąg, który zawiera przestrzeń nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e9317-118">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="e9317-119">requiresSession</span><span class="sxs-lookup"><span data-stu-id="e9317-119">requiresSession</span></span>|<span data-ttu-id="e9317-120">Wartość logiczna określająca, czy kontrakt może być używany tylko na powiązaniach sesji.</span><span class="sxs-lookup"><span data-stu-id="e9317-120">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="e9317-121">Po zainicjowaniu usługi środowisko Integration Runtime zapewnia spójność tego ustawienia z typem powiązania, które ma być używane.</span><span class="sxs-lookup"><span data-stu-id="e9317-121">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="e9317-122">Wyjątek jest generowany, jeśli co najmniej jedno powiązanie kontraktu jest w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="e9317-122">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="e9317-123">Jeśli ta właściwość ma `false`wartość, a kanał jednokierunkowy jest używany i istnieją wszystkie parametry [out], generowany jest również wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e9317-123">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9317-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9317-124">Child Elements</span></span>  
  
|<span data-ttu-id="e9317-125">Element</span><span class="sxs-lookup"><span data-stu-id="e9317-125">Element</span></span>|<span data-ttu-id="e9317-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e9317-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9317-127">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="e9317-127">persistableTypes</span></span>|<span data-ttu-id="e9317-128">Wszystkie typy, które są trwałe.</span><span class="sxs-lookup"><span data-stu-id="e9317-128">All the persistable types.</span></span>|  
|<span data-ttu-id="e9317-129">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="e9317-129">userDefinedTypes</span></span>|<span data-ttu-id="e9317-130">Kolekcja typów zdefiniowanych przez użytkownika (UDT), które mają zostać uwzględnione w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="e9317-130">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="e9317-131">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="e9317-131">exposedMethods</span></span>|<span data-ttu-id="e9317-132">Kolekcja metod modelu COM+, które są dostępne, gdy interfejs składnika modelu COM+ jest udostępniany jako usługa sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e9317-132">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9317-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9317-133">Parent Elements</span></span>  
  
|<span data-ttu-id="e9317-134">Element</span><span class="sxs-lookup"><span data-stu-id="e9317-134">Element</span></span>|<span data-ttu-id="e9317-135">Opis</span><span class="sxs-lookup"><span data-stu-id="e9317-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9317-136">comContracts</span><span class="sxs-lookup"><span data-stu-id="e9317-136">comContracts</span></span>|<span data-ttu-id="e9317-137">Zawiera kolekcję `comContract` elementów.</span><span class="sxs-lookup"><span data-stu-id="e9317-137">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9317-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9317-138">Remarks</span></span>  
 <span data-ttu-id="e9317-139">Kontrakty usługi integracji modelu COM+ są obecnie ograniczone `http://tempuri.org` do przestrzeni nazw, a nazwa kontraktu pochodzi od pomocniczego interfejsu com.</span><span class="sxs-lookup"><span data-stu-id="e9317-139">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="e9317-140">Można jednak określić alternatywy przy użyciu `comContracts` sekcji, a także `comContract` elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e9317-140">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="e9317-141">Można na przykład użyć poniższej konfiguracji, aby określić przestrzeń nazw, nazwę kontraktu i typy zdefiniowane przez użytkownika, a także inne ustawienia dla kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e9317-141">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="e9317-142">Po zainicjowaniu usługi określone nazwy obszarów nazw i kontraktów są stosowane do opisów wygenerowanych usług.</span><span class="sxs-lookup"><span data-stu-id="e9317-142">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9317-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9317-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="e9317-144">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e9317-144">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="e9317-145">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="e9317-145">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e9317-146">Instrukcje: Konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="e9317-146">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
