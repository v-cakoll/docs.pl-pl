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
ms.openlocfilehash: dc3bbe0ee72ca5583b1e52a61c914ad866a22a05
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596813"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="69d08-102">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="69d08-102">Integrating with COM Applications</span></span>
<span data-ttu-id="69d08-103">Usługi Windows Communication Foundation (WCF) można zintegrować bezpośrednio z istniejącym kodem przy użyciu monikera usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="69d08-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="69d08-104">Moniker usługi może być używany z szerokiego zakresu środowisk programistycznych opartych na modelu COM, takich jak pakiet Office VBA, Visual Basic 6,0 lub Visual C++ 6,0.</span><span class="sxs-lookup"><span data-stu-id="69d08-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69d08-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="69d08-105">In This Section</span></span>  
 [<span data-ttu-id="69d08-106">Omówienie integracji z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="69d08-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="69d08-107">Zawiera omówienie głównych części procesu integracji.</span><span class="sxs-lookup"><span data-stu-id="69d08-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="69d08-108">Instrukcje: rejestrowanie i konfigurowanie monikera usługi</span><span class="sxs-lookup"><span data-stu-id="69d08-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="69d08-109">Aby użyć monikera usługi WCF w aplikacji COM, należy zarejestrować wymagane typy z atrybutami COM i skonfigurować aplikację COM oraz moniker z wymaganą konfiguracją powiązania.</span><span class="sxs-lookup"><span data-stu-id="69d08-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="69d08-110">Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="69d08-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="69d08-111">Wyjaśnia, jak uzyskać definicję kontraktu w formie dokumentu języka definicji usług sieci Web (WSDL) lub z punktu końcowego WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="69d08-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="69d08-112">Instrukcje: używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="69d08-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="69d08-113">Opisuje sposób wywoływania przykładu WCF przy użyciu monikera WSDL programu WCF.</span><span class="sxs-lookup"><span data-stu-id="69d08-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="69d08-114">Instrukcje: używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="69d08-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="69d08-115">Opisuje sposób wywoływania przykładu WCF przy użyciu monikera programu WCF określającego punkt końcowy MEX.</span><span class="sxs-lookup"><span data-stu-id="69d08-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="69d08-116">Instrukcje: określanie poświadczeń zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="69d08-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="69d08-117">Moniker usługi WCF obsługuje `IChannelCredentials` interfejs, który umożliwia szereg alternatywnych metod określania poświadczeń kanału.</span><span class="sxs-lookup"><span data-stu-id="69d08-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="69d08-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="69d08-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="69d08-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69d08-119">See also</span></span>

- [<span data-ttu-id="69d08-120">Integrowanie z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="69d08-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
