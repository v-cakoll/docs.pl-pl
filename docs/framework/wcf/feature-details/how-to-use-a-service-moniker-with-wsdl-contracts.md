---
title: 'Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70d7e9ff45616f832597ebc48db00198967935c6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601143"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="16001-102">Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="16001-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="16001-103">Istnieją sytuacje, w których można chcieć korzystać z całkowicie niezależnego klienta międzyoperacyjnego modelu COM.</span><span class="sxs-lookup"><span data-stu-id="16001-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="16001-104">Usługa, która ma zostać wywołana, może nie ujawniać punktu końcowego MEX, a Biblioteka DLL klienta WCF nie może być zarejestrowana na potrzeby współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="16001-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="16001-105">W takich przypadkach można utworzyć plik WSDL opisujący usługę i przekazać go do monikera usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="16001-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="16001-106">W tym temacie opisano sposób wywoływania przykładu Wprowadzenie WCF przy użyciu monikera WSDL programu WCF.</span><span class="sxs-lookup"><span data-stu-id="16001-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="16001-107">Używanie monikera usługi WSDL</span><span class="sxs-lookup"><span data-stu-id="16001-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="16001-108">Otwórz i skompiluj przykładowe rozwiązanie GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="16001-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="16001-109">Otwórz program Internet Explorer i przejdź do programu `http://localhost/ServiceModelSamples/Service.svc` , aby upewnić się, że usługa działa.</span><span class="sxs-lookup"><span data-stu-id="16001-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="16001-110">W pliku Service.cs Dodaj następujący atrybut klasy CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="16001-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="16001-111">Dodawanie powiązania przestrzeni nazw do pliku App. config usługi:</span><span class="sxs-lookup"><span data-stu-id="16001-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="16001-112">Utwórz plik WSDL, aby można było odczytać aplikację.</span><span class="sxs-lookup"><span data-stu-id="16001-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="16001-113">Ponieważ przestrzenie nazw zostały dodane w krokach 3 i 4, można użyć programu IE do zapytania o cały opis WSDL usługi, przechodząc do tematu `http://localhost/ServiceModelSamples/Service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="16001-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="16001-114">Następnie można zapisać plik z programu Internet Explorer jako serviceWsdl. XML.</span><span class="sxs-lookup"><span data-stu-id="16001-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="16001-115">Jeśli nie określisz przestrzeni nazw w krokach 3 i 4, dokument WSDL zwrócony z zapytania o powyższy adres URL nie będzie kompletny w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="16001-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="16001-116">Zwrócony dokument WSDL będzie zawierać kilka instrukcji importu, które zaimportują inne dokumenty WSDL.</span><span class="sxs-lookup"><span data-stu-id="16001-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="16001-117">Trzeba będzie przejść przez każdą instrukcję importu i utworzyć kompletny dokument WSDL, łącząc element WSDL zwrócony z usługi z zaimportowanym WSDL.</span><span class="sxs-lookup"><span data-stu-id="16001-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="16001-118">Otwórz Visual Basic 6,0 i Utwórz nowy plik w standardowym pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="16001-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="16001-119">Dodaj przycisk do formularza i kliknij dwukrotnie przycisk, aby dodać następujący kod do procedury obsługi kliknięcia:</span><span class="sxs-lookup"><span data-stu-id="16001-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
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
    > Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie zwróci `GetObject` błąd mówiąc "Nieprawidłowa składnia".  <span data-ttu-id="16001-121">Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="16001-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="16001-122">Uruchom aplikację Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16001-122">Run the Visual Basic application.</span></span> <span data-ttu-id="16001-123">Zostanie wyświetlone okno komunikatu z wynikami wywoływania odejmowania (145, 76,54).</span><span class="sxs-lookup"><span data-stu-id="16001-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16001-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16001-124">See also</span></span>

- [<span data-ttu-id="16001-125">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="16001-125">Getting Started</span></span>](../samples/getting-started-sample.md)
- [<span data-ttu-id="16001-126">Omówienie integracji z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="16001-126">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
