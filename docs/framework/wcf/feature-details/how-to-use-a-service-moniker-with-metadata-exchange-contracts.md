---
title: 'Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: e7c05bb43b7811d4716a225142dd880886586783
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495112"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="516cd-102">Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="516cd-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="516cd-103">Po rozwinięciu niektórych nowych usług WCF, może zdecydować, chcesz można było wywołać te usługi z poziomu skryptu lub aplikacji w języku Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="516cd-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="516cd-104">Jedną z metod byłoby wygenerować zestaw klienta WCF, zarejestrować zestaw w modelu COM, zainstaluj zestaw w pamięci podręcznej GAC i następnie odwoływać się do typów modelu COM w kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="516cd-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="516cd-105">Podczas dystrybucji aplikacji, trzeba będzie dystrybuować także zestaw klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="516cd-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="516cd-106">Użytkownik będzie miał zarejestrowania się zestaw klienta programu WCF za pomocą modelu COM i umieść go w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="516cd-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="516cd-107">Usługa międzyoperacyjna modelu COM WCF umożliwia również wykonywanie tych samych wywołań usługi bez polegania na zestaw klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="516cd-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="516cd-108">Monikera programu WCF umożliwia wywoływanie żadnej usługi WCF z dowolnego języka zgodnego z COM. (Visual Basic, VBScript, Visual Basic for Applications (VBA) i tak dalej), określając punkt końcowy metadanych programu exchange (Mex) identyfikator URI, który monikera usługi używany do wyodrębniania typu informacje o usłudze.</span><span class="sxs-lookup"><span data-stu-id="516cd-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="516cd-109">W tym temacie opisano sposób wywoływania przykładu wprowadzenie usługi WCF, używanie monikera programu WCF, która określa punkt końcowy wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="516cd-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="516cd-110">Typy zdefiniowane przez zestaw klienta WCF faktycznie nigdy nie są tworzone.</span><span class="sxs-lookup"><span data-stu-id="516cd-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="516cd-111">Zestaw jest używany tylko w przypadku metadanych.</span><span class="sxs-lookup"><span data-stu-id="516cd-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="516cd-112">Używanie monikera usługi przy użyciu adresu wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="516cd-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="516cd-113">Wprowadzenie do przykładu kompilacji i użyj programu Internet Explorer, aby przejść do jej adresu URL (http://localhost/ServiceModelSamples/Service.svc) aby upewnić się, że usługa działa.</span><span class="sxs-lookup"><span data-stu-id="516cd-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="516cd-114">Utwórz skrypt Visual Basic lub aplikacji Visual Basic, który zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="516cd-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="516cd-115">Uruchamianie aplikacji języka Visual Basic lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="516cd-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="516cd-116">Usługi, którą wywołujesz musi ujawniać punkt końcowy wymiany metadanych dla monikera móc odczytać metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="516cd-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="516cd-117">Aby uzyskać więcej informacji, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="516cd-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="516cd-118">Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o "Nieprawidłową składnię."</span><span class="sxs-lookup"><span data-stu-id="516cd-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="516cd-119">Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="516cd-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516cd-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="516cd-120">See also</span></span>
- [<span data-ttu-id="516cd-121">Instrukcje: Użyj monikera usługi Windows Communication Foundation, bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="516cd-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="516cd-122">Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="516cd-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
