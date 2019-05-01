---
title: 'Instrukcje: używanie krótkiej nazwy usługi z kontraktami WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 2968641538bf0b4d0e136d5784bf69e5e7fcb3a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972890"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="13ed3-102">Instrukcje: używanie krótkiej nazwy usługi z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="13ed3-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="13ed3-103">Istnieją sytuacje, gdy chcesz całkowicie niezależna klient COM Interop.</span><span class="sxs-lookup"><span data-stu-id="13ed3-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="13ed3-104">Usługi, którą chcesz wywołać nie może ujawniać punktu końcowego MEX i klienta WCF, które biblioteki DLL nie jest zarejestrowany dla współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="13ed3-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="13ed3-105">W takich przypadkach można utworzyć pliku WSDL, który zawiera opis usługi i przekaż go do monikera programu WCF.</span><span class="sxs-lookup"><span data-stu-id="13ed3-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="13ed3-106">W tym temacie opisano sposób wywoływania przykładu wprowadzenie usługi WCF, używanie monikera programu WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="13ed3-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="13ed3-107">Używanie monikera usługi WSDL</span><span class="sxs-lookup"><span data-stu-id="13ed3-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="13ed3-108">Otworzyć i skompilować GettingStarted przykładowe rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="13ed3-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="13ed3-109">Otwórz program Internet Explorer i przejdź do `http://localhost/ServiceModelSamples/Service.svc` aby upewnić się, że usługa działa.</span><span class="sxs-lookup"><span data-stu-id="13ed3-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="13ed3-110">W pliku Service.cs Dodaj następujący atrybut w klasie CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="13ed3-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="13ed3-111">Dodawanie przestrzeni nazw powiązania z usługą pliku App.config:</span><span class="sxs-lookup"><span data-stu-id="13ed3-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="13ed3-112">Utwórz plik WSDL dla aplikacji na odczytywanie.</span><span class="sxs-lookup"><span data-stu-id="13ed3-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="13ed3-113">Ponieważ przestrzenie nazw zostały dodane w kroku 3 i 4, można użyć programu Internet Explorer dla całego opis WSDL usługi kwerendy, przechodząc do `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="13ed3-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="13ed3-114">Można następnie zapisz plik w programie Internet Explorer jako serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="13ed3-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="13ed3-115">Jeśli nie określisz przestrzeni nazw w kroku 3 i 4, zwrócone w wyniku wykonywania zapytań na powyższy adres URL dokumentu WSDL nie będą pełne WSDL.</span><span class="sxs-lookup"><span data-stu-id="13ed3-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="13ed3-116">Dokument WSDL, zwracana będzie zawierać kilka deklaracji importu, które importują inne dokumenty WSDL.</span><span class="sxs-lookup"><span data-stu-id="13ed3-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="13ed3-117">Trzeba będzie przejść każda instrukcja importu i tworzyć pełny dokument WSDL, łącząc WSDL zwrócony przez usługę za pomocą języka WSDL, zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="13ed3-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="13ed3-118">Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych.</span><span class="sxs-lookup"><span data-stu-id="13ed3-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="13ed3-119">Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="13ed3-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
    >  Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna wywołanie `GetObject` zwróci błąd informujący o "Nieprawidłowa składnia".  <span data-ttu-id="13ed3-121">Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="13ed3-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="13ed3-122">Uruchom aplikację języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13ed3-122">Run the Visual Basic application.</span></span> <span data-ttu-id="13ed3-123">Okno komunikatu pojawi się wraz z wynikami Subtract wywołującym (145, 76.54).</span><span class="sxs-lookup"><span data-stu-id="13ed3-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ed3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13ed3-124">See also</span></span>

- [<span data-ttu-id="13ed3-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="13ed3-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="13ed3-126">Przegląd integrowania z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="13ed3-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
