---
title: Współdziałanie z aplikacjami COM
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 51626da6e97e346f43cfe606a5164024580a2ac7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046999"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="a8f3c-102">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="a8f3c-102">Integrating with COM Applications</span></span>
<span data-ttu-id="a8f3c-103">Usługi Windows Communication Foundation (WCF) można zintegrować bezpośrednio do istniejącego kodu przy użyciu monikera programu WCF.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="a8f3c-104">Moniker usługi może służyć w środowiskach programistycznych szeroki zakres COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8f3c-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a8f3c-105">In This Section</span></span>  
 [<span data-ttu-id="a8f3c-106">Przegląd integrowania z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="a8f3c-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="a8f3c-107">Zawiera omówienie głównych części procesu integracji.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="a8f3c-108">Instrukcje: Rejestrowanie i konfigurowanie monikera usługi</span><span class="sxs-lookup"><span data-stu-id="a8f3c-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="a8f3c-109">Aby użyć monikera programu WCF w ramach aplikacji modelu COM, należy zarejestrować wymaganych typów opartego na atrybutach z modelem COM i konfigurowanie aplikacji modelu COM i moniker za pomocą konfiguracji powiązania wymagane.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="a8f3c-110">Instrukcje: Użyj monikera usługi Windows Communication Foundation, bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="a8f3c-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="a8f3c-111">Wyjaśniono sposób uzyskiwania definicji zamówienia w postaci dokumentów sieci Web Services Definition Language (WSDL) lub z punktu końcowego usługi WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="a8f3c-112">Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="a8f3c-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="a8f3c-113">W tym artykule opisano sposób wywoływania próbkę WCF używanie monikera programu WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="a8f3c-114">Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="a8f3c-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="a8f3c-115">W tym artykule opisano sposób wywoływania próbkę WCF używanie monikera programu WCF, która określa punkt końcowy wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="a8f3c-116">Instrukcje: Określanie poświadczeń zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="a8f3c-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="a8f3c-117">Obsługuje monikera programu WCF `IChannelCredentials` interfejsu, który umożliwia szeroką gamę alternatywnych metod w celu określania poświadczeń kanału.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a8f3c-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="a8f3c-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="a8f3c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8f3c-119">See also</span></span>

- [<span data-ttu-id="a8f3c-120">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="a8f3c-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
