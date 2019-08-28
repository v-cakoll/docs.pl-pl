---
title: Przegląd integrowania z aplikacjami modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 99e3c2f4445673f3b74048a2b466203af7bc2795
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045881"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="afa1c-102">Przegląd integrowania z aplikacjami modelu COM</span><span class="sxs-lookup"><span data-stu-id="afa1c-102">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="afa1c-103">Windows Communication Foundation (WCF) udostępnia deweloperowi kodu zarządzanego zaawansowane środowisko do tworzenia połączonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afa1c-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="afa1c-104">Jeśli jednak masz znaczną inwestycję w niezarządzanym kodzie COM i nie chcesz migrować, nadal możesz zintegrować usługi sieci Web WCF bezpośrednio z istniejącym kodem przy użyciu monikera usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="afa1c-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="afa1c-105">Moniker usługi może być używany z szerokiego zakresu środowisk programistycznych opartych na modelu COM, takich jak Office VBA, Visual Basic 6,0 i Visual C++ 6,0.</span><span class="sxs-lookup"><span data-stu-id="afa1c-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="afa1c-106">Moniker usługi używa kanału komunikacyjnego WCF do całej komunikacji.</span><span class="sxs-lookup"><span data-stu-id="afa1c-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="afa1c-107">Mechanizmy zabezpieczeń i tożsamości dla tego kanału różnią się od tych używanych w standardowych serwerach proxy modelu COM i modelu DCOM.</span><span class="sxs-lookup"><span data-stu-id="afa1c-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="afa1c-108">Ponadto, ponieważ moniker usługi używa kanału komunikacyjnego WCF, domyślny okres limitu czasu wynosi jedną minutę dla wszystkich wywołań.</span><span class="sxs-lookup"><span data-stu-id="afa1c-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="afa1c-109">Moniker usługi jest używany z `GetObject` funkcją do zapewnienia niezarządzanego dewelopera z silnie wpisaną podejściem specyficznym dla modelu COM do wywoływania usług sieci Web WCF.</span><span class="sxs-lookup"><span data-stu-id="afa1c-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="afa1c-110">Wymaga to lokalnej, widocznej dla modelu COM definicji kontraktu usługi sieci Web WCF i powiązania, które ma być używane.</span><span class="sxs-lookup"><span data-stu-id="afa1c-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="afa1c-111">Podobnie jak w przypadku innych klientów programu WCF, moniker usługi musi utworzyć kanał o określonym typie dla usługi, chociaż konstrukcja tego kanału jest nieprzezroczysta dla programisty COM przy pierwszym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="afa1c-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="afa1c-112">Wspólnie z innymi klientami programu WCF przy użyciu monikera aplikacje określają adres, powiązanie i kontrakt do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="afa1c-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="afa1c-113">Umowę można określić w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="afa1c-113">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="afa1c-114">Typ kontraktu — kontrakt jest rejestrowany jako widoczny dla modelu COM na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="afa1c-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="afa1c-115">Kontrakt WSDL — kontrakt jest dostarczany w formie dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="afa1c-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="afa1c-116">Kontrakt MEX — umowa jest pobierana w czasie wykonywania z punktu końcowego wymiany metadanych (MEX).</span><span class="sxs-lookup"><span data-stu-id="afa1c-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="afa1c-117">Parametry obsługiwane przez moniker usługi</span><span class="sxs-lookup"><span data-stu-id="afa1c-117">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="afa1c-118">W poniższej tabeli przedstawiono parametry, które są obsługiwane przez moniker usługi.</span><span class="sxs-lookup"><span data-stu-id="afa1c-118">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="afa1c-119">Parametr</span><span class="sxs-lookup"><span data-stu-id="afa1c-119">Parameter</span></span>|<span data-ttu-id="afa1c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="afa1c-120">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="afa1c-121">Lokalizacja adresu URL usługi.</span><span class="sxs-lookup"><span data-stu-id="afa1c-121">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="afa1c-122">Nazwa sekcji powiązania z konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afa1c-122">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="afa1c-123">Nazwane wystąpienie powiązania z poziomu sekcji nazwanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="afa1c-123">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="afa1c-124">Identyfikator interfejsu (IID) reprezentujący kontrakt usługi lub nazwę kontraktu (z MEX).</span><span class="sxs-lookup"><span data-stu-id="afa1c-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="afa1c-125">Dokument WSDL, który zapewnia alternatywną formę definicji kontraktu.</span><span class="sxs-lookup"><span data-stu-id="afa1c-125">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="afa1c-126">Tożsamość głównej nazwy serwera (SPN), która będzie używana do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="afa1c-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="afa1c-127">Tożsamość głównej nazwy użytkownika (UPN), która będzie używana do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="afa1c-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="afa1c-128">Tożsamość DNS, która będzie używana do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="afa1c-128">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="afa1c-129">Lokalizacja adresu URL punktu końcowego wymiany metadanych (MEX) usługi.</span><span class="sxs-lookup"><span data-stu-id="afa1c-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="afa1c-130">Nazwa sekcji powiązania z konfiguracji aplikacji w celu nawiązania połączenia z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="afa1c-131">Nazwane wystąpienie powiązania z poziomu sekcji nazwanego powiązania, aby nawiązać połączenie z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="afa1c-132">Przestrzeń nazw sekcji powiązania z pobranej MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-132">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="afa1c-133">Przestrzeń nazw kontraktu z pobranej klasy MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-133">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="afa1c-134">Tożsamość głównej nazwy serwera (SPN), która będzie używana do komunikacji z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="afa1c-135">Tożsamość głównej nazwy użytkownika (UPN), która będzie używana do komunikacji z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="afa1c-136">Tożsamość DNS, która będzie używana do komunikacji z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="afa1c-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="afa1c-137">Określ użycie serializatora "XML" lub "DataContract".</span><span class="sxs-lookup"><span data-stu-id="afa1c-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="afa1c-138">W przypadku korzystania z całkowicie opartych na modelu COM moniker usługi wymaga programu WCF i .NET Framework 2,0 do zainstalowania na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="afa1c-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="afa1c-139">Jest również ważne, aby aplikacje klienckie używające monikera usługi ładowały odpowiednią wersję środowiska uruchomieniowego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="afa1c-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="afa1c-140">W przypadku używania monikera w aplikacjach pakietu Office może być wymagany plik konfiguracji, aby upewnić się, że załadowano poprawną wersję platformy.</span><span class="sxs-lookup"><span data-stu-id="afa1c-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="afa1c-141">Na przykład w programie Excel następujący tekst powinien być umieszczony w pliku o nazwie Excel. exe. config w tym samym katalogu, w którym znajduje się plik Excel. exe:</span><span class="sxs-lookup"><span data-stu-id="afa1c-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="afa1c-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="afa1c-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="afa1c-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afa1c-143">See also</span></span>

- [<span data-ttu-id="afa1c-144">Instrukcje: Rejestrowanie i Konfigurowanie monikera usługi</span><span class="sxs-lookup"><span data-stu-id="afa1c-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
