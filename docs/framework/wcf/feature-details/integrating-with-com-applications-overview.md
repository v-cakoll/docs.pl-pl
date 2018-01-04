---
title: "Przegląd integrowania z aplikacjami modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b20ae5329f08e9391fd7b93218c44c3c1978a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="e8d1d-102">Przegląd integrowania z aplikacjami modelu COM</span><span class="sxs-lookup"><span data-stu-id="e8d1d-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e8d1d-103">udostępnia bogate środowisko tworzenia połączonych aplikacji dewelopera kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="e8d1d-104">Jednak jeśli masz znaczących inwestycji w niezarządzanym kodzie oparte na modelu COM i nie chcesz migrować, można nadal zintegrować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług sieci Web bezpośrednio do istniejącego kodu za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="e8d1d-105">Krótka nazwa usługi może służyć w środowiskach programistycznych szeroki zakres modelu COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8d1d-106">Moniker usługi używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanał komunikacyjny na potrzeby całej komunikacji.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="e8d1d-107">Bezpieczeństwo i tożsamość mechanizmów dla tego kanału różnią się od używanych w standardowe COM i DCOM serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="e8d1d-108">Ponadto ponieważ używa moniker usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanał komunikacyjny jedną minutę na wszystkich wywołań jest domyślny limit czasu.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="e8d1d-109">Moniker usługi jest używany z `GetObject` funkcji niezarządzanej developer podejścia jednoznacznie, specyficzne dla modelu COM przy dotyczący wywołania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="e8d1d-110">Wymaga to definicji lokalnego, widoczny dla modelu COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt usługi i powiązania, który ma być używany w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="e8d1d-111">Takich jak inne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, moniker usługi należy tworzyć typu kanału do usługi, chociaż ten kanał konstrukcji wykonywane w sposób przezroczysty dla programisty modelu COM przy pierwszym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="e8d1d-112">Wspólne innych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, korzystając z krótką nazwę, aplikacje Określ address, binding i contract do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="e8d1d-113">Kontrakt można określić w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="e8d1d-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="e8d1d-114">Typu kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="e8d1d-115">Kontrakt WSDL — Umowa jest dostarczany w formie dokument WSDL.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="e8d1d-116">MEX kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="e8d1d-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="e8d1d-117">Parametry obsługiwane przez Moniker usługi</span><span class="sxs-lookup"><span data-stu-id="e8d1d-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="e8d1d-118">W poniższej tabeli przedstawiono parametry, które są obsługiwane przez moniker usługi.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="e8d1d-119">Parametr</span><span class="sxs-lookup"><span data-stu-id="e8d1d-119">Parameter</span></span>|<span data-ttu-id="e8d1d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e8d1d-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="e8d1d-121">Adres URL lokalizacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="e8d1d-122">Nazwa sekcji powiązania z konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="e8d1d-123">Nazwane wystąpienie obiektu binding z wewnątrz sekcji powiązania o nazwie.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="e8d1d-124">Identyfikator interfejsu (IID) reprezentujący kontrakt usługi lub Nazwa kontraktu (od MEX).</span><span class="sxs-lookup"><span data-stu-id="e8d1d-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="e8d1d-125">Dokument WSDL, który zapewnia alternatywny definicję kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="e8d1d-126">Tożsamość główna nazwa (usługi SPN) serwera używanego do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="e8d1d-127">Tożsamość główna nazwa (UPN) użytkownika ma być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="e8d1d-128">Tożsamość DNS ma być używany do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="e8d1d-129">Adres URL lokalizacji punktu końcowego usługi wymiany metadanych (MEX).</span><span class="sxs-lookup"><span data-stu-id="e8d1d-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="e8d1d-130">Nazwa sekcji powiązania z konfigurację aplikacji, aby połączyć się z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="e8d1d-131">Nazwane wystąpienie obiektu binding z wewnątrz sekcji powiązania o nazwie nawiązywania połączenia z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="e8d1d-132">Namespace nazwy sekcji powiązania z pobrane MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="e8d1d-133">Namespace umowy z pobrane MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="e8d1d-134">Tożsamość główna nazwa (usługi SPN) serwera, które ma być używany do komunikacji z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="e8d1d-135">Tożsamość główna nazwa (UPN) użytkownika ma być używany do komunikacji z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="e8d1d-136">Tożsamość DNS ma być używany do komunikacji z punktem końcowym MEX.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="e8d1d-137">Określ użycie serializatora "xml" lub "datacontract".</span><span class="sxs-lookup"><span data-stu-id="e8d1d-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e8d1d-138">Nawet wtedy, gdy jest używany z klientami całkowicie oparty na modelu COM, wymaga moniker usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i obsługi .NET Framework 2.0 jest zainstalowany na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="e8d1d-139">Jest również krytycznych, że aplikacje klienckie, które używają moniker usługi załadować odpowiednią wersję środowiska uruchomieniowego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="e8d1d-140">Używając krótkiej nazwy w aplikacjach pakietu Office, aby upewnić się, że jest załadowany poprawne framework w wersji może wymagać pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8d1d-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="e8d1d-141">Na przykład przy użyciu programu Excel, następujący tekst należy umieścić w pliku o nazwie Excel.exe.config w tym samym katalogu co plik Excel.exe:</span><span class="sxs-lookup"><span data-stu-id="e8d1d-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="e8d1d-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="e8d1d-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="e8d1d-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8d1d-143">See Also</span></span>  
 [<span data-ttu-id="e8d1d-144">Instrukcje: rejestrowanie i konfigurowanie monikera usługi</span><span class="sxs-lookup"><span data-stu-id="e8d1d-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
