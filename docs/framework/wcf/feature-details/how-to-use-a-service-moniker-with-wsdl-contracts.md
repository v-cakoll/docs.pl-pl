---
title: "Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d98fb82984fec4acbb8b95d4bc4667468804ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="01536-102">Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="01536-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="01536-103">Istnieją sytuacje, gdy chcesz całkowicie niezależna klient COM Interop.</span><span class="sxs-lookup"><span data-stu-id="01536-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="01536-104">Usługi, którą chcesz wywołać nie może narazić punktu końcowego MEX i klienta WCF, które biblioteki DLL nie jest zarejestrowany dla modelu COM interop.</span><span class="sxs-lookup"><span data-stu-id="01536-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="01536-105">W takich przypadkach możesz utworzyć plik WSDL, który zawiera opis usługi i przekaż go do krótkiej nazwy usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="01536-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="01536-106">W tym temacie opisano sposób wywołania próbki pobierania programu WCF za pomocą moniker WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="01536-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="01536-107">Przy użyciu moniker usługi WSDL</span><span class="sxs-lookup"><span data-stu-id="01536-107">Using the WSDL service moniker</span></span>  
  
1.  <span data-ttu-id="01536-108">Otwórz i kompilacji GettingStarted przykładowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="01536-108">Open and build the GettingStarted sample solution.</span></span>  
  
2.  <span data-ttu-id="01536-109">Otwórz program Internet Explorer i przejdź do http://localhost/ServiceModelSamples/Service.svc aby upewnić się, że usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="01536-109">Open Internet Explorer and browse to http://localhost/ServiceModelSamples/Service.svc to make sure that the service is working.</span></span>  
  
3.  <span data-ttu-id="01536-110">W pliku Service.cs Dodaj następujący atrybut w klasie CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="01536-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  <span data-ttu-id="01536-111">Dodawanie przestrzeni nazw powiązania z usługą App.config:</span><span class="sxs-lookup"><span data-stu-id="01536-111">Add a binding namespace to the service App.config:</span></span>  
  
  
  
5.  <span data-ttu-id="01536-112">Utwórz plik WSDL dla aplikacji do odczytu.</span><span class="sxs-lookup"><span data-stu-id="01536-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="01536-113">Ponieważ przestrzenie nazw zostały dodane w kroku 3 i 4, można użyć programu Internet Explorer dla całego opis WSDL usługi kwerendy, przechodząc do http://localhost/ServiceModelSamples/Service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="01536-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to http://localhost/ServiceModelSamples/Service.svc?wsdl.</span></span> <span data-ttu-id="01536-114">Można następnie zapisz plik z programu Internet Explorer jako serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="01536-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="01536-115">Jeśli nie określisz przestrzenie nazw w kroku 3 i 4, dokument WSDL zwracane z zapytań powyższy adres URL nie będzie pełną WSDL.</span><span class="sxs-lookup"><span data-stu-id="01536-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="01536-116">Zwrócony dokument WSDL zawiera kilka instrukcje importu, które importują innych dokumentów WSDL.</span><span class="sxs-lookup"><span data-stu-id="01536-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="01536-117">Musisz przejść przez każdego instrukcję import i kompilacji cały dokument WSDL, łączenie WSDL zakończyła WSDL zaimportowane z usługi.</span><span class="sxs-lookup"><span data-stu-id="01536-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6.  <span data-ttu-id="01536-118">Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa.</span><span class="sxs-lookup"><span data-stu-id="01536-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="01536-119">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="01536-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłowa składnia".  <span data-ttu-id="01536-121">Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="01536-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7.  <span data-ttu-id="01536-122">Uruchom aplikację języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01536-122">Run the Visual Basic application.</span></span> <span data-ttu-id="01536-123">Wyniki wywołania Subtract (145, 76.54) pojawi się okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="01536-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01536-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01536-124">See Also</span></span>  
 [<span data-ttu-id="01536-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="01536-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="01536-126">Przegląd integrowania z COM aplikacjami</span><span class="sxs-lookup"><span data-stu-id="01536-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
