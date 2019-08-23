---
title: 'Instrukcje: używanie krótkiej nazwy usługi z kontraktami wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 00aa1bbde95c0636391f213f830fc67b2dedf459
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968792"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="61170-102">Instrukcje: używanie krótkiej nazwy usługi z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="61170-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="61170-103">Po rozpoczęciu tworzenia nowych usług WCF możesz zdecydować, że chcesz mieć możliwość wywoływania tych usług ze skryptu lub aplikacji Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="61170-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="61170-104">Jedną z metod jest generowanie zestawu klienta WCF, rejestrowanie zestawu przy użyciu modelu COM, Instalowanie zestawu w GAC, a następnie odwoływanie się do typów COM z kodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="61170-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="61170-105">Podczas dystrybucji aplikacji konieczne będzie również dystrybuowanie zestawu klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="61170-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="61170-106">Użytkownik będzie musiał następnie zarejestrować zestaw klienta programu WCF przy użyciu modelu COM i umieścić go w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="61170-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="61170-107">Współdziałanie modelu COM WCF umożliwia również wykonywanie tych samych wywołań usługi bez polegania na zestawie klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="61170-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="61170-108">Moniker programu WCF umożliwia wywoływanie dowolnej usługi WCF z dowolnego języka zgodnego z modelem COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) itd.) przez określenie identyfikatora URI punktu końcowego wymiany metadanych (Mex), którego moniker usługi używa do wyodrębniania typu Informacje o usłudze.</span><span class="sxs-lookup"><span data-stu-id="61170-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="61170-109">W tym temacie opisano sposób wywoływania przykładu Wprowadzenie WCF przy użyciu monikera programu WCF określającego punkt końcowy MEX.</span><span class="sxs-lookup"><span data-stu-id="61170-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61170-110">Typy zdefiniowane przez zestaw klienta WCF nigdy nie są tworzone w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="61170-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="61170-111">Zestaw jest używany tylko dla metadanych.</span><span class="sxs-lookup"><span data-stu-id="61170-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="61170-112">Używanie monikera usługi z adresem Mex</span><span class="sxs-lookup"><span data-stu-id="61170-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="61170-113">Utwórz przykład wprowadzenie i użyj programu Internet Explorer, aby przejść do jego adresu http://localhost/ServiceModelSamples/Service.svc) URL (aby upewnić się, że usługa działa.</span><span class="sxs-lookup"><span data-stu-id="61170-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="61170-114">Utwórz skrypt Visual Basic lub aplikację Visual Basic, która zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="61170-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="61170-115">Uruchom aplikację Visual Basic lub skrypt.</span><span class="sxs-lookup"><span data-stu-id="61170-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="61170-116">Wywoływana usługa musi uwidocznić punkt końcowy MEX, aby moniker mógł odczytać metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="61170-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="61170-117">Aby uzyskać więcej informacji, zobacz [jak: Publikowanie metadanych dla usługi za pomocą pliku](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="61170-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="61170-118">Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci komunikat o błędzie informujący o nieprawidłowej składni.</span><span class="sxs-lookup"><span data-stu-id="61170-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="61170-119">Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="61170-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61170-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61170-120">See also</span></span>

- [<span data-ttu-id="61170-121">Instrukcje: Użyj monikera usługi Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="61170-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="61170-122">Instrukcje: Używanie monikera usługi z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="61170-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
