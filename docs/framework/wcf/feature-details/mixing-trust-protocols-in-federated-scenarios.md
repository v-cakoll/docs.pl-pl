---
title: "Mieszanie protokołów zaufania w scenariuszach obejmujących federację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="1d3ba-102">Mieszanie protokołów zaufania w scenariuszach obejmujących federację</span><span class="sxs-lookup"><span data-stu-id="1d3ba-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="1d3ba-103">Może to być scenariuszy w których federacyjnych klienci komunikują się z usługą i tokenu usługa zabezpieczenia (STS), które nie mają tej samej wersji zaufania.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="1d3ba-104">Usługa może zawierać WSDL `RequestSecurityTokenTemplate` potwierdzenia z elementami WS-Trust, które są w różnych wersjach niż Usługa tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="1d3ba-105">W takich przypadkach [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta konwertuje elementy WS-Trust otrzymanych od `RequestSecurityTokenTemplate` zgodna wersja zaufania usługi STS.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d3ba-106">uchwyty niezgodne wersje zaufania tylko dla powiązań standardowych.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="1d3ba-107">Wszystkie parametry standard — algorytm, które są rozpoznawane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są częścią standardowej powiązania.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="1d3ba-108">W tym temacie opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zachowanie w przypadku różnych zaufania ustawienia między usługą i Usługa tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="1d3ba-109">RP luty 2005 i STS luty 2005</span><span class="sxs-lookup"><span data-stu-id="1d3ba-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="1d3ba-110">WSDL dla jednostki uzależnionej strony (RP) zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="1d3ba-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="1d3ba-111">Plik konfiguracji klienta zawiera listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d3ba-112">Nie można rozróżnianie między klientem a usługą parametrów; dodaje wszystkie parametry i wysyła je w `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="1d3ba-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="1d3ba-113">Zaufanie RP 1.3 i zaufania STS 1.3</span><span class="sxs-lookup"><span data-stu-id="1d3ba-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="1d3ba-114">WSDL dla planu odzyskiwania zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="1d3ba-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="1d3ba-115">Plik konfiguracji klienta zawiera `secondaryParameters` element, który opakowuje parametrów określonych przez planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d3ba-116">Usuwa `EncryptionAlgorithm`, `CanonicalizationAlgorithm` i `KeyWrapAlgorithm` elementy z elementu najwyższego poziomu w obszarze RST, jeśli są one obecne w `SecondaryParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-116"> removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d3ba-117">dołącza `SecondaryParameters` elementu RST wychodzących, nie mają być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="1d3ba-118">Zaufanie RP luty 2005 i zaufania STS 1.3</span><span class="sxs-lookup"><span data-stu-id="1d3ba-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="1d3ba-119">WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="1d3ba-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="1d3ba-120">Plik konfiguracji klienta zawiera listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="1d3ba-121">W pliku konfiguracji klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie rozróżnianie między parametrami usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="1d3ba-122">W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konwertuje wszystkie parametry do przestrzeni nazw w wersji 1.3 zaufania.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d3ba-123">uchwyty `KeyType`, `KeySize`, i `TokenType` elementy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1d3ba-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="1d3ba-124">Pobieranie pliku WSDL, utwórz powiązanie i przypisz `KeyType`, `KeySize`, i `TokenType` z parametrów planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="1d3ba-125">Następnie zostanie wygenerowany plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="1d3ba-126">Klienta można teraz zmienić żadnego parametru w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="1d3ba-127">W czasie wykonywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kopiuje wszystkie parametry określonego do `AdditionalTokenParameters` sekcji pliku konfiguracji klienta, z wyjątkiem `KeyType`, `KeySize` i `TokenType`, ponieważ te parametry są wyjaśnić podczas konfiguracji Generowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="1d3ba-128">Zaufanie RP 1.3 i zaufania STS luty 2005</span><span class="sxs-lookup"><span data-stu-id="1d3ba-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="1d3ba-129">WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="1d3ba-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="1d3ba-130">Plik konfiguracji klienta zawiera `secondaryParamters` element, który opakowuje parametrów określonych przez planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1d3ba-131">kopiuje wszystkie parametry, które są określone w `SecondaryParameters` sekcji, aby element RST najwyższego poziomu, ale nie konwertuje je do przestrzeni nazw protokołu WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="1d3ba-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
