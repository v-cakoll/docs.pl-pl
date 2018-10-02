---
title: Mieszanie protokołów zaufania w scenariuszach obejmujących federację
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
ms.openlocfilehash: d4290880d8d708811a95b38356aa61f0d23c89a8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030080"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="7192e-102">Mieszanie protokołów zaufania w scenariuszach obejmujących federację</span><span class="sxs-lookup"><span data-stu-id="7192e-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="7192e-103">Mogą istnieć scenariusze, w których federacyjnego klienci komunikują się z usługą i Usługa tokenu zabezpieczającego (STS), które nie mają tę samą wersję zaufania.</span><span class="sxs-lookup"><span data-stu-id="7192e-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="7192e-104">Usługa może zawierać WSDL `RequestSecurityTokenTemplate` potwierdzenia z elementami WS-Trust, które są w różnych wersjach niż usługi STS.</span><span class="sxs-lookup"><span data-stu-id="7192e-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="7192e-105">W takich przypadkach klienta usługi Windows Communication Foundation (WCF) konwertuje elementy WS-Trust otrzymane od `RequestSecurityTokenTemplate` do dopasowania usługi STS zaufania wersji.</span><span class="sxs-lookup"><span data-stu-id="7192e-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="7192e-106">Usługi WCF obsługuje wersje niedopasowanych zaufania tylko standardowe powiązania.</span><span class="sxs-lookup"><span data-stu-id="7192e-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="7192e-107">Wszystkie parametry algorytmu standard, które są rozpoznawane przez architekturę WCF są częścią standardowych powiązania.</span><span class="sxs-lookup"><span data-stu-id="7192e-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="7192e-108">W tym temacie opisano zachowanie WCF za pomocą różnych ustawień zaufania między usługą i Usługa tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="7192e-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="7192e-109">Jednostki Uzależnionej lut 2005 i STS lut 2005</span><span class="sxs-lookup"><span data-stu-id="7192e-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="7192e-110">WSDL dla jednostki uzależnionej strona (RP) zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="7192e-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="7192e-111">Plik konfiguracji klienta zawiera listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="7192e-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="7192e-112">Usługi WCF nie rozróżnienia między klientem a usługą parametrów; dodaje wszystkie parametry i wysyła je w `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="7192e-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="7192e-113">Zaufania jednostki Uzależnionej 1.3 i usługi STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="7192e-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="7192e-114">WSDL dla jednostki Uzależnionej zawiera następujące elementy w ramach `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="7192e-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="7192e-115">Plik konfiguracji klienta zawiera `secondaryParameters` element, który otacza parametrów określonych przez jednostkę Uzależnioną.</span><span class="sxs-lookup"><span data-stu-id="7192e-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="7192e-116">Usuwa WCF `EncryptionAlgorithm`, `CanonicalizationAlgorithm` i `KeyWrapAlgorithm` elementy z element najwyższego poziomu w ramach RST, jeśli są obecne w `SecondaryParameters` elementu.</span><span class="sxs-lookup"><span data-stu-id="7192e-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="7192e-117">Dołącza WCF `SecondaryParameters` elementu wychodzących RST, bez modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="7192e-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="7192e-118">Zaufania jednostki Uzależnionej lut 2005 i STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="7192e-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="7192e-119">WSDL dla jednostki Uzależnionej zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="7192e-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="7192e-120">Plik konfiguracji klienta zawiera listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="7192e-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="7192e-121">Z pliku konfiguracji klienta WCF nie można odróżnić parametry usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="7192e-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="7192e-122">W związku z tym WCF konwertuje wszystkie parametry do przestrzeni nazw w wersji 1.3 zaufania.</span><span class="sxs-lookup"><span data-stu-id="7192e-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="7192e-123">Uchwyty WCF `KeyType`, `KeySize`, i `TokenType` elementy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7192e-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="7192e-124">Pobieranie pliku WSDL, utworzyć powiązanie i przypisać `KeyType`, `KeySize`, i `TokenType` z parametrów jednostki Uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="7192e-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="7192e-125">Następnie zostanie wygenerowany plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="7192e-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="7192e-126">Klienta można teraz zmienić żadnych parametrów w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7192e-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="7192e-127">Podczas wykonywania programu WCF kopiuje wszystkie parametry określoną `AdditionalTokenParameters` sekcji w pliku konfiguracji klienta, z wyjątkiem `KeyType`, `KeySize` i `TokenType`, ponieważ te parametry są rozliczane w pliku konfiguracji Generowanie.</span><span class="sxs-lookup"><span data-stu-id="7192e-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="7192e-128">Zaufania jednostki Uzależnionej 1.3 i zaufanie usługi STS lut 2005</span><span class="sxs-lookup"><span data-stu-id="7192e-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="7192e-129">WSDL dla jednostki Uzależnionej zawiera następujące elementy w `RequestSecurityTokenTemplate` sekcji:</span><span class="sxs-lookup"><span data-stu-id="7192e-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="7192e-130">Plik konfiguracji klienta zawiera `secondaryParamters` element, który otacza parametrów określonych przez jednostkę Uzależnioną.</span><span class="sxs-lookup"><span data-stu-id="7192e-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="7192e-131">Usługi WCF kopiuje wszystkie parametry, które są określone w `SecondaryParameters` sekcji, aby element najwyższego poziomu RST, ale nie konwertuje je do przestrzeni nazw protokołu WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="7192e-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
