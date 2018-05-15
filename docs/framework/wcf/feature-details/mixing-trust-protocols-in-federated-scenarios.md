---
title: Mieszanie protokołów zaufania w scenariuszach obejmujących federację
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="717d4-102">Mieszanie protokołów zaufania w scenariuszach obejmujących federację</span><span class="sxs-lookup"><span data-stu-id="717d4-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="717d4-103">Może to być scenariuszy w których federacyjnych klienci komunikują się z usługą i tokenu usługa zabezpieczenia (STS), które nie mają tej samej wersji zaufania.</span><span class="sxs-lookup"><span data-stu-id="717d4-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="717d4-104">Usługa może zawierać WSDL `RequestSecurityTokenTemplate` potwierdzenia z elementami WS-Trust, które są w różnych wersjach niż Usługa tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="717d4-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="717d4-105">W takich przypadkach klient usługi Windows Communication Foundation (WCF) konwertuje elementy WS-Trust otrzymanych od `RequestSecurityTokenTemplate` zgodna wersja zaufania usługi STS.</span><span class="sxs-lookup"><span data-stu-id="717d4-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="717d4-106">Usługi WCF obsługuje wersje niedopasowanych zaufania tylko dla powiązań standardowych.</span><span class="sxs-lookup"><span data-stu-id="717d4-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="717d4-107">Wszystkie parametry standard — algorytm, które są rozpoznawane przez WCF są częścią Powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="717d4-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="717d4-108">W tym temacie opisano zachowanie WCF z różnymi ustawieniami relacji zaufania między usługą i Usługa tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="717d4-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="717d4-109">RP luty 2005 i STS luty 2005</span><span class="sxs-lookup"><span data-stu-id="717d4-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="717d4-110">WSDL dla jednostki uzależnionej strony (RP) zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="717d4-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="717d4-111">Plik konfiguracji klienta zawiera listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="717d4-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="717d4-112">Usługi WCF nie rozróżnianie między klientem a usługą parametrów; dodaje wszystkie parametry i wysyła je w `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="717d4-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="717d4-113">Zaufanie RP 1.3 i zaufania STS 1.3</span><span class="sxs-lookup"><span data-stu-id="717d4-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="717d4-114">WSDL dla planu odzyskiwania zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="717d4-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="717d4-115">Plik konfiguracji klienta zawiera `secondaryParameters` element, który opakowuje parametrów określonych przez planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="717d4-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="717d4-116">Usuwa WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` i `KeyWrapAlgorithm` elementy z elementu najwyższego poziomu w obszarze RST, jeśli są one obecne w `SecondaryParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="717d4-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="717d4-117">Dołącza WCF `SecondaryParameters` elementu RST wychodzących, nie mają być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="717d4-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="717d4-118">Zaufanie RP luty 2005 i zaufania STS 1.3</span><span class="sxs-lookup"><span data-stu-id="717d4-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="717d4-119">WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="717d4-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="717d4-120">Plik konfiguracji klienta zawiera listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="717d4-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="717d4-121">Z pliku konfiguracji klienta WCF nie można rozróżnić parametry usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="717d4-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="717d4-122">W związku z tym WCF konwertuje wszystkie parametry do przestrzeni nazw w wersji 1.3 zaufania.</span><span class="sxs-lookup"><span data-stu-id="717d4-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="717d4-123">Uchwyty WCF `KeyType`, `KeySize`, i `TokenType` elementy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="717d4-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="717d4-124">Pobieranie pliku WSDL, utwórz powiązanie i przypisz `KeyType`, `KeySize`, i `TokenType` z parametrów planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="717d4-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="717d4-125">Następnie zostanie wygenerowany plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="717d4-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="717d4-126">Klienta można teraz zmienić żadnego parametru w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="717d4-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="717d4-127">W czasie wykonywania, WCF kopiuje wszystkie parametry określonego do `AdditionalTokenParameters` sekcji pliku konfiguracji klienta, z wyjątkiem `KeyType`, `KeySize` i `TokenType`, ponieważ te parametry są wyjaśnić w pliku konfiguracji Generowanie.</span><span class="sxs-lookup"><span data-stu-id="717d4-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="717d4-128">Zaufanie RP 1.3 i zaufania STS luty 2005</span><span class="sxs-lookup"><span data-stu-id="717d4-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="717d4-129">WSDL dla planu odzyskiwania zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="717d4-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="717d4-130">Plik konfiguracji klienta zawiera `secondaryParamters` element, który opakowuje parametrów określonych przez planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="717d4-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="717d4-131">Usługi WCF kopiuje wszystkie parametry określony w ramach `SecondaryParameters` sekcji, aby element RST najwyższego poziomu, ale nie konwertuje je do przestrzeni nazw protokołu WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="717d4-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
