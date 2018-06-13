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
ms.openlocfilehash: 292892ef572bd63fff055aeed88073573fadb934
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491845"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="2d413-102">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="2d413-102">Integrating with COM Applications</span></span>
<span data-ttu-id="2d413-103">Usługi Windows Communication Foundation (WCF) można zintegrować bezpośrednio do istniejącego kodu za pomocą moniker usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2d413-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="2d413-104">Krótka nazwa usługi może służyć w środowiskach programistycznych szeroki zakres modelu COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="2d413-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d413-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2d413-105">In This Section</span></span>  
 [<span data-ttu-id="2d413-106">Przegląd integrowania z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="2d413-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="2d413-107">Zawiera omówienie głównych części procesu integracji.</span><span class="sxs-lookup"><span data-stu-id="2d413-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="2d413-108">Instrukcje: rejestrowanie i konfigurowanie monikera usługi</span><span class="sxs-lookup"><span data-stu-id="2d413-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="2d413-109">Aby użyć moniker usługi WCF w ramach aplikacji modelu COM, należy zarejestrować wymagane typy oparte na atrybutach w modelu COM i skonfigurować aplikacji modelu COM i krótka nazwa za pomocą konfiguracji powiązania wymagany.</span><span class="sxs-lookup"><span data-stu-id="2d413-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="2d413-110">Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="2d413-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="2d413-111">Wyjaśniono, jak uzyskać definicję kontraktu w formie dokumentu sieci Web Services Definition Language (WSDL) lub z punktu końcowego usługi WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="2d413-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="2d413-112">Instrukcje: używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="2d413-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="2d413-113">Opisuje sposób wywołania próbkę WCF za pomocą moniker WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="2d413-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="2d413-114">Instrukcje: używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="2d413-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="2d413-115">Opisuje sposób wywołania próbkę WCF za pomocą usługi WCF krótkiej nazwy, która określa punkt końcowy Mex.</span><span class="sxs-lookup"><span data-stu-id="2d413-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="2d413-116">Instrukcje: określanie poświadczeń zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="2d413-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="2d413-117">Obsługuje moniker usługi WCF `IChannelCredentials` interfejs, umożliwiający szereg alternatywnych metod dotyczących określania poświadczeń kanału.</span><span class="sxs-lookup"><span data-stu-id="2d413-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2d413-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2d413-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="2d413-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d413-119">See Also</span></span>  
 [<span data-ttu-id="2d413-120">Współdziałanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="2d413-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
