---
title: '&lt;comContract&gt;'
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: e2addbada7f55076ae919d93c897991a7ec0fcd8
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779208"
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="0bff1-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="0bff1-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="0bff1-103">Określa kontrakt usługi integracji COM +.</span><span class="sxs-lookup"><span data-stu-id="0bff1-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="0bff1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0bff1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0bff1-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0bff1-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bff1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bff1-106">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bff1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0bff1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0bff1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0bff1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bff1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0bff1-109">Attributes</span></span>  
  
|<span data-ttu-id="0bff1-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0bff1-110">Attribute</span></span>|<span data-ttu-id="0bff1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0bff1-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bff1-112">kontrakt</span><span class="sxs-lookup"><span data-stu-id="0bff1-112">contract</span></span>|<span data-ttu-id="0bff1-113">Ciąg, który zawiera typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0bff1-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="0bff1-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="0bff1-114">name</span></span>|<span data-ttu-id="0bff1-115">Ciąg, który zawiera nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0bff1-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="0bff1-116">— przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="0bff1-116">namespace</span></span>|<span data-ttu-id="0bff1-117">Ciąg, który zawiera przestrzeń nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0bff1-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="0bff1-118">Element requiresSession</span><span class="sxs-lookup"><span data-stu-id="0bff1-118">requiresSession</span></span>|<span data-ttu-id="0bff1-119">Wartość logiczna określająca, czy kontrakt mogą być używane tylko na powiązaniach sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="0bff1-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="0bff1-120">Podczas inicjowania usługi produktu integration runtime zapewnia to ustawienie jest zgodne z typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="0bff1-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="0bff1-121">Wyjątek jest generowany, jeśli jeden lub więcej powiązań dla kontraktu usługi są w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="0bff1-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="0bff1-122">Jeśli ta właściwość jest `false`i jednokierunkowe kanał jest w użyciu i istnieją [parametry out], wyjątek zostanie również wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="0bff1-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bff1-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0bff1-123">Child Elements</span></span>  
  
|<span data-ttu-id="0bff1-124">Element</span><span class="sxs-lookup"><span data-stu-id="0bff1-124">Element</span></span>|<span data-ttu-id="0bff1-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0bff1-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bff1-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="0bff1-126">persistableTypes</span></span>|<span data-ttu-id="0bff1-127">Wszystkie typy stałe.</span><span class="sxs-lookup"><span data-stu-id="0bff1-127">All the persistable types.</span></span>|  
|<span data-ttu-id="0bff1-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="0bff1-128">userDefinedTypes</span></span>|<span data-ttu-id="0bff1-129">Kolekcja z użytkownika zdefiniowanych typów (UDT), które ma być zawarty w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="0bff1-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="0bff1-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="0bff1-130">exposedMethods</span></span>|<span data-ttu-id="0bff1-131">Kolekcja metod modelu COM +, które są dostępne, gdy interfejs składnika COM + jest widoczny jako usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0bff1-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bff1-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0bff1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0bff1-133">Element</span><span class="sxs-lookup"><span data-stu-id="0bff1-133">Element</span></span>|<span data-ttu-id="0bff1-134">Opis</span><span class="sxs-lookup"><span data-stu-id="0bff1-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bff1-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="0bff1-135">comContracts</span></span>|<span data-ttu-id="0bff1-136">Zawiera kolekcję `comContract` elementów.</span><span class="sxs-lookup"><span data-stu-id="0bff1-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bff1-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bff1-137">Remarks</span></span>  
 <span data-ttu-id="0bff1-138">Kontrakty usług integracji modelu COM + są obecnie ograniczone do `http://tempuri.org` przestrzeni nazw i Nazwa kontraktu jest tworzony na podstawie obsługi interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="0bff1-138">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="0bff1-139">Można jednak określić alternatywne przy użyciu `comContracts` sekcji, jak również `comContract` elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0bff1-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="0bff1-140">Na przykład można użyć następującej konfiguracji do określania przestrzeni nazw, Nazwa kontraktu i typów zdefiniowanych przez użytkownika do uwzględnienia, a także inne ustawienia dla kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="0bff1-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
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
  
 <span data-ttu-id="0bff1-141">Podczas inicjowania usługi określonych przestrzeni nazw i nazwy kontraktów są stosowane do opisów wygenerowanego usługi.</span><span class="sxs-lookup"><span data-stu-id="0bff1-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bff1-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bff1-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="0bff1-143">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0bff1-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="0bff1-144">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="0bff1-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="0bff1-145">Instrukcje: konfigurowanie ustawień usługi COM+</span><span class="sxs-lookup"><span data-stu-id="0bff1-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
