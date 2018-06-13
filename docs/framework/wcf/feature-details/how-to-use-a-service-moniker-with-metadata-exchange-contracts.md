---
title: 'Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491253"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="f1db0-102">Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="f1db0-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="f1db0-103">Po rozwinięciu niektóre nowe usługi WCF, mogą zdecydować, chcesz mieć możliwość wywołania tych usług z skryptu lub aplikacji Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="f1db0-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="f1db0-104">Jedna z metod byłoby wygenerować zestawu klienta WCF, zarejestrować zestawu w modelu COM, Instalowanie zestawu w pamięci podręcznej GAC i odwoływanie do typów COM w kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f1db0-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="f1db0-105">Podczas dystrybucji aplikacji należy rozesłać także zestaw klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f1db0-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="f1db0-106">Użytkownik będzie miał do rejestrowania zestawów klienta WCF COM i umieszczenie go w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="f1db0-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="f1db0-107">Współdziałanie z COM WCF umożliwia również wywoływać tej samej usługi bez polegania na zestawie klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f1db0-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="f1db0-108">Monikera programu WCF pozwala wywoływać żadnej usługi WCF z dowolnego języka zgodny z modelu COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) i tak dalej), określając punkt końcowy programu exchange (Mex) metadanych identyfikator URI, który moniker usługi używany do wyodrębniania typu informacje o usłudze.</span><span class="sxs-lookup"><span data-stu-id="f1db0-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="f1db0-109">W tym temacie opisano sposób wywołania próbki pobierania programu WCF za pomocą usługi WCF krótkiej nazwy, która określa punkt końcowy Mex.</span><span class="sxs-lookup"><span data-stu-id="f1db0-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1db0-110">Typy zdefiniowane przez zestaw klienta WCF nigdy są tworzone.</span><span class="sxs-lookup"><span data-stu-id="f1db0-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="f1db0-111">Zestaw jest używany tylko dla metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1db0-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="f1db0-112">Przy użyciu moniker usługi za pomocą adresu MEX.</span><span class="sxs-lookup"><span data-stu-id="f1db0-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="f1db0-113">Tworzenie przykładowej wprowadzenie i przejdź do adresu URL za pomocą programu Internet Explorer (http://localhost/ServiceModelSamples/Service.svc) aby upewnić się, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f1db0-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="f1db0-114">Utwórz skrypt Visual Basic lub Visual Basic aplikacji, która zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f1db0-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="f1db0-115">Uruchamianie aplikacji Visual Basic lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="f1db0-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1db0-116">Usługa wywoływanego musi ujawniać punkt końcowy Mex dla krótkiej nazwy móc odczytać metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="f1db0-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="f1db0-117">Aby uzyskać więcej informacji, zobacz [porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="f1db0-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1db0-118">Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłową składnię."</span><span class="sxs-lookup"><span data-stu-id="f1db0-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="f1db0-119">Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="f1db0-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1db0-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1db0-120">See Also</span></span>  
 [<span data-ttu-id="f1db0-121">Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="f1db0-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="f1db0-122">Instrukcje: używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="f1db0-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
