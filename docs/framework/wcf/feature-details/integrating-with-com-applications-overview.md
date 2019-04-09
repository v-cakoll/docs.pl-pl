---
title: Przegląd integrowania z aplikacjami modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 182e5f41498d8f5e3fcbc4b84aa7e86b67ce3ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087628"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="1edda-102">Przegląd integrowania z aplikacjami modelu COM</span><span class="sxs-lookup"><span data-stu-id="1edda-102">Integrating with COM Applications Overview</span></span>
<span data-ttu-id="1edda-103">Windows Communication Foundation (WCF) zapewnia dewelopera kodu zarządzanego przy użyciu bogate środowisko tworzenia połączonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1edda-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="1edda-104">Jednak jeśli masz znaczne inwestycje w niezarządzanym kodzie opartym na modelu COM i nie chcesz migrować, można nadal zintegrować usług sieci Web WCF bezpośrednio do istniejącego kodu przy użyciu monikera programu WCF.</span><span class="sxs-lookup"><span data-stu-id="1edda-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="1edda-105">Moniker usługi może służyć w środowiskach programistycznych szeroki zakres COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="1edda-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1edda-106">Moniker usługi używa kanał komunikacyjny WCF dla całej komunikacji.</span><span class="sxs-lookup"><span data-stu-id="1edda-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="1edda-107">Mechanizmy zabezpieczeń i tożsamości dla tego kanału różnią się od tych używanych w standardowych serwerów proxy modelu COM i DCOM.</span><span class="sxs-lookup"><span data-stu-id="1edda-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="1edda-108">Ponadto ponieważ monikera programu używa kanał komunikacyjny WCF domyślny limit czasu jest jedną minutę na wszystkich wywołań.</span><span class="sxs-lookup"><span data-stu-id="1edda-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="1edda-109">Moniker usługi jest używana z `GetObject` funkcji niezarządzanych deweloperów dzięki podejściu silnie typizowane, specyficzne dla modelu COM do wywoływania usług sieci Web WCF.</span><span class="sxs-lookup"><span data-stu-id="1edda-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="1edda-110">Wymaga to lokalne, widoczne dla modelu COM definicję kontraktu usługi WCF w sieci Web i powiązania, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="1edda-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="1edda-111">Podobnie jak inni klienci WCF monikera programu należy tworzyć wpisane kanału do usługi, chociaż tej konstrukcji kanału wykonywane w sposób przezroczysty do programisty należy COM przy pierwszym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="1edda-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="1edda-112">Wspólnych innych WCF klientów, gdy używanie monikera programu aplikacje, określ adres, powiązania i umowy do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="1edda-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="1edda-113">Kontrakt można określić w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="1edda-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="1edda-114">Wpisane kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1edda-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="1edda-115">WSDL kontraktu — jest dostarczany w formie dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="1edda-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="1edda-116">MEX kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="1edda-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="1edda-117">Parametrów obsługiwanych przez monikera usługi</span><span class="sxs-lookup"><span data-stu-id="1edda-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="1edda-118">W poniższej tabeli przedstawiono parametry, które są obsługiwane przez monikera programu.</span><span class="sxs-lookup"><span data-stu-id="1edda-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="1edda-119">Parametr</span><span class="sxs-lookup"><span data-stu-id="1edda-119">Parameter</span></span>|<span data-ttu-id="1edda-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1edda-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="1edda-121">Lokalizacja adresu URL usługi.</span><span class="sxs-lookup"><span data-stu-id="1edda-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="1edda-122">Nazwa sekcji do powiązania z konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1edda-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="1edda-123">Nazwane wystąpienie obiektu binding z wewnątrz sekcji o nazwie powiązania.</span><span class="sxs-lookup"><span data-stu-id="1edda-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="1edda-124">Identyfikator interfejsu (IID) reprezentujący kontraktu usługi lub Nazwa kontraktu (z MEX).</span><span class="sxs-lookup"><span data-stu-id="1edda-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="1edda-125">Dokument WSDL, który dostarcza alternatywnej formy definicję kontraktu.</span><span class="sxs-lookup"><span data-stu-id="1edda-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="1edda-126">Tożsamość główna nazwa (usługi SPN) serwera ma być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="1edda-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="1edda-127">Tożsamość głównej nazwy (UPN) użytkownika, które ma być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="1edda-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="1edda-128">Tożsamość DNS, który ma być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="1edda-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="1edda-129">Lokalizacja adresu URL punktu końcowego metadanych programu Exchange (MEX) usługi.</span><span class="sxs-lookup"><span data-stu-id="1edda-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="1edda-130">Powiązania nazwy sekcji z konfiguracji aplikacji, aby połączyć się z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="1edda-131">Nazwane wystąpienie obiektu binding z w ramach sekcji powiązania o nazwie, aby połączyć się z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="1edda-132">Namespace nazwa sekcji powiązania z pobrane MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="1edda-133">Namespace umowy z pobrane MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="1edda-134">Tożsamość główna nazwa (usługi SPN) serwera ma być używany do komunikowania się z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="1edda-135">Tożsamość głównej nazwy (UPN) użytkownika, które ma być używany do komunikowania się z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="1edda-136">Tożsamość DNS, który ma być używany do komunikowania się z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="1edda-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="1edda-137">Określ korzystanie z serializatora "xml" lub "schematu datacontract".</span><span class="sxs-lookup"><span data-stu-id="1edda-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1edda-138">Nawet wtedy, gdy jest używany z klientami w całości opartą na modelu COM, monikera programu wymaga usług WCF i pomocnicze systemu .NET Framework 2.0, należy zainstalować na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1edda-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="1edda-139">Jest również krytycznych, że aplikacje klienckie, które używają monikera programu ładować odpowiednią wersję środowiska uruchomieniowego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1edda-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="1edda-140">Korzystając z monikerem w aplikacjach pakietu Office, plik konfiguracji może być wymagane, aby zapewnić, że jest załadowany poprawną wersję.</span><span class="sxs-lookup"><span data-stu-id="1edda-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="1edda-141">Na przykład za pomocą programu Excel, następujący tekst będzie umieszczona w pliku o nazwie Excel.exe.config w tym samym katalogu co plik Excel.exe:</span><span class="sxs-lookup"><span data-stu-id="1edda-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="1edda-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1edda-142">See also</span></span>

- [<span data-ttu-id="1edda-143">Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi</span><span class="sxs-lookup"><span data-stu-id="1edda-143">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
