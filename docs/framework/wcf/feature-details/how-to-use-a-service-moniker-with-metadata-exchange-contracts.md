---
title: "Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed6ce9b87a5e2d8945a57110c02cce8024439f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="bc361-102">Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="bc361-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="bc361-103">Po rozwinięciu niektóre nowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, użytkownik może zadecydować chcesz mieć możliwość wywołania tych usług z skryptu lub aplikacji Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="bc361-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="bc361-104">Jedna z metod byłoby Generowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zestawu klienta zarejestrować zestawu w modelu COM, zainstalowania zestawu w pamięci podręcznej GAC i odwoływanie do typów COM w kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bc361-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="bc361-105">Podczas dystrybucji aplikacji, konieczne będzie dystrybuować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] również zestawu klienta.</span><span class="sxs-lookup"><span data-stu-id="bc361-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="bc361-106">Użytkownik będzie miał do rejestrowania zestawów klienta WCF COM i umieszczenie go w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="bc361-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bc361-107">Współdziałanie z COM umożliwia także wywoływać tej samej usługi bez polegania na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zestawu klienta.</span><span class="sxs-lookup"><span data-stu-id="bc361-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="bc361-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker pozwala wywoływać żadnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług z dowolnego języka zgodny z modelu COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) i tak dalej), określając punkt końcowy programu exchange (Mex) metadanych identyfikator URI, który używa moniker usługi Aby wyodrębnić informacje o typie dotyczących usługi.</span><span class="sxs-lookup"><span data-stu-id="bc361-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="bc361-109">W tym temacie opisano sposób wywołania wprowadzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbkowania przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótkiej nazwy, która określa punkt końcowy Mex.</span><span class="sxs-lookup"><span data-stu-id="bc361-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc361-110">Typy zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpienia zestawu klienta faktycznie nigdy nie są tworzone.</span><span class="sxs-lookup"><span data-stu-id="bc361-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="bc361-111">Zestaw jest używany tylko dla metadanych.</span><span class="sxs-lookup"><span data-stu-id="bc361-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="bc361-112">Przy użyciu moniker usługi za pomocą adresu MEX.</span><span class="sxs-lookup"><span data-stu-id="bc361-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="bc361-113">Tworzenie przykładowych wprowadzenie i użyj programu Internet Explorer, aby przejść na adres URL (http://localhost/ServiceModelSamples/Service.svc), aby upewnić się, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="bc361-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="bc361-114">Utwórz skrypt Visual Basic lub Visual Basic aplikacji, która zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="bc361-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="bc361-115">Uruchamianie aplikacji Visual Basic lub skryptu.</span><span class="sxs-lookup"><span data-stu-id="bc361-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc361-116">Usługa wywoływanego musi ujawniać punkt końcowy Mex dla krótkiej nazwy móc odczytać metadane z usługi.</span><span class="sxs-lookup"><span data-stu-id="bc361-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="bc361-117">Aby uzyskać więcej informacji, zobacz [porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="bc361-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bc361-118">Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłową składnię."</span><span class="sxs-lookup"><span data-stu-id="bc361-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="bc361-119">Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="bc361-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc361-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc361-120">See Also</span></span>  
 [<span data-ttu-id="bc361-121">Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="bc361-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="bc361-122">Porady: używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="bc361-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
