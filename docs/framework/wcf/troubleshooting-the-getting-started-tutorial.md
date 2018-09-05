---
title: Rozwiązywanie problemów z samouczkiem dotyczącym wprowadzenia
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 43128743ba16aefc8669ace85070a16d80145a71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519424"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a><span data-ttu-id="2b98a-102">Rozwiązywanie problemów z samouczkiem dotyczącym wprowadzenia</span><span class="sxs-lookup"><span data-stu-id="2b98a-102">Troubleshooting the Getting Started Tutorial</span></span>
<span data-ttu-id="2b98a-103">W tym temacie wymieniono najbardziej typowe problemy występujące podczas pracy przy użyciu samouczka Wprowadzenie i ich rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2b98a-103">This topic lists the most common problems encountered when working through the Getting Started Tutorial and how to resolve them.</span></span>  
  
<span data-ttu-id="2b98a-104">**Nie mogę znaleźć pliki projektu na dysku twardego.**</span><span class="sxs-lookup"><span data-stu-id="2b98a-104">**I am unable to find the project files on my hard drive.**</span></span>

 <span data-ttu-id="2b98a-105">Program Visual Studio zapisuje pliki projektu w c:\users\\<user name>\Documents\\< wersja programu Visual Studio\>\Projects.</span><span class="sxs-lookup"><span data-stu-id="2b98a-105">Visual Studio saves project files in c:\users\\<user name>\Documents\\<Visual Studio version\>\Projects.</span></span>  
  
<span data-ttu-id="2b98a-106">**Przy próbie uruchomienia aplikacji usługi: HTTP nie można zarejestrować adres URL `http://+:8000/ServiceModelSamples/Service/`.** 
 **Proces nie ma praw dostępu do tej przestrzeni nazw.**</span><span class="sxs-lookup"><span data-stu-id="2b98a-106">**Attempting to run the service application: HTTP could not register URL `http://+:8000/ServiceModelSamples/Service/`.**
**Your process does not have access rights to this namespace.**</span></span> 

 <span data-ttu-id="2b98a-107">Proces, który hostuje usługę WCF musi być uruchamiane z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="2b98a-107">The process that hosts a WCF service must be run with Administrative privileges.</span></span> <span data-ttu-id="2b98a-108">Jeśli korzystasz z usługi z poziomu programu Visual Studio, należy uruchomić programu Visual Studio jako Administrator.</span><span class="sxs-lookup"><span data-stu-id="2b98a-108">If you are running the service from inside Visual Studio, you must run Visual Studio as an Administrator.</span></span> <span data-ttu-id="2b98a-109">Kliknij tak zrobić **Start**, kliknij prawym przyciskiem myszy **programu Visual Studio \< *wersji* >**  i wybierz **Uruchom jako Administrator**.</span><span class="sxs-lookup"><span data-stu-id="2b98a-109">To do so click **Start**, right-click **Visual Studio \<*version*>** and select **Run As Administrator**.</span></span> <span data-ttu-id="2b98a-110">Jeśli korzystasz z usługi, w wierszu polecenia w oknie konsoli, należy uruchomić w oknie konsoli jako Administrator, w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="2b98a-110">If you are running the service from a command-line prompt in a console window, you must start the console window as an Administrator in a similar way.</span></span> <span data-ttu-id="2b98a-111">Kliknij przycisk **Start**, kliknij prawym przyciskiem myszy **polecenia** i wybierz **Uruchom jako Administrator**.</span><span class="sxs-lookup"><span data-stu-id="2b98a-111">Click **Start**, right-click **Command Prompt** and select **Run As Administrator**.</span></span>  
  
<span data-ttu-id="2b98a-112">**Podjęto próbę użycia narzędzia Svcutil.exe: "svcutil" nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy.**</span><span class="sxs-lookup"><span data-stu-id="2b98a-112">**Attempting to use the Svcutil.exe tool: 'svcutil' is not recognized as an internal or external command, operable program or batch file.**</span></span>

 <span data-ttu-id="2b98a-113">Svcutil.exe musi być w ścieżce systemowej.</span><span class="sxs-lookup"><span data-stu-id="2b98a-113">Svcutil.exe must be in the system path.</span></span> <span data-ttu-id="2b98a-114">Najprostszym rozwiązaniu jest używać wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2b98a-114">The easiest solution is to use the Command Prompt.</span></span> <span data-ttu-id="2b98a-115">Kliknij przycisk **Start**, wybierz opcję **wszystkie programy**, **programu Visual Studio \< *wersji*>**,  **Narzędzia programu Visual Studio**, i **wiersz polecenia programisty dla programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="2b98a-115">Click **Start**, select **All Programs**, **Visual Studio \<*version*>**, **Visual Studio Tools**, and **Developer Command Prompt for Visual Studio**.</span></span> <span data-ttu-id="2b98a-116">Ten wiersz polecenia ustawia ścieżkę systemu w poprawnych lokalizacjach, w przypadku wszystkich narzędzi dostarczana jako część programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2b98a-116">This command prompt sets the system path to the correct locations for all tools shipped as part of Visual Studio.</span></span>  

<span data-ttu-id="2b98a-117">**Nie można odnaleźć pliku App.config, wygenerowanego przez Svcutil.exe.**</span><span class="sxs-lookup"><span data-stu-id="2b98a-117">**Unable to find the App.config file generated by Svcutil.exe.**</span></span>

 <span data-ttu-id="2b98a-118">**Dodaj istniejący element** domyślnie okno dialogowe tylko Wyświetla pliki z następującymi rozszerzeniami: .cs resx, .settings, XSD, .wsdl.</span><span class="sxs-lookup"><span data-stu-id="2b98a-118">The **Add Existing Item** dialog only displays files with the following extensions by default: .cs, .resx, .settings, .xsd, .wsdl.</span></span> <span data-ttu-id="2b98a-119">Można określić, czy chcesz zobaczyć wszystkie typy plików, wybierając **wszystkie pliki (\*.\*)**  w polu listy rozwijanej w prawym dolnym rogu **Dodaj istniejący element** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2b98a-119">You can specify that you want to see all file types by selecting **All Files (\*.\*)** in the drop-down list box in the lower right corner of the **Add Existing Item** dialog box.</span></span>  


<span data-ttu-id="2b98a-120">**Kompilowanie aplikacji klienta: "CalculatorClient" nie zawiera definicji dla "\<nazwę metody >" i żadna metoda rozszerzenia "\<nazwę metody >" przyjmującej pierwszy argument typu "CalculatorClient" znaleziono (czy brakuje dyrektywy lub odwołania do zestawu?)**</span><span class="sxs-lookup"><span data-stu-id="2b98a-120">**Compiling the client application: 'CalculatorClient' does not contain a definition for '\<method name>' and no extension method '\<method name>' accepting a first argument of type 'CalculatorClient' could be found (are you missing a using directive or an assembly reference?)**</span></span>  

<span data-ttu-id="2b98a-121">Tylko tych metod, które są oznaczone `ServiceOperationAttribute` są widoczne na zewnątrz.</span><span class="sxs-lookup"><span data-stu-id="2b98a-121">Only those methods that are marked with the `ServiceOperationAttribute` are exposed to the outside world.</span></span> <span data-ttu-id="2b98a-122">Jeżeli pominięto `ServiceOperationAttribute` atrybut z jednej z metod w `ICalculator` interfejsu, otrzymasz komunikat o błędzie podczas kompilowania aplikacji klienckiej, która sprawia, że wywołanie operacji Brak atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2b98a-122">If you omitted the `ServiceOperationAttribute` attribute from one of the methods in the `ICalculator` interface, you get this error message when compiling a client application that makes a call to the operation missing the attribute.</span></span>  

<span data-ttu-id="2b98a-123">**Kompilowanie aplikacji klienckiej: typ lub przestrzeń nazw nie można odnaleźć "CalculatorClient" (Brak przy użyciu dyrektywy lub odwołanie do zestawu?)**</span><span class="sxs-lookup"><span data-stu-id="2b98a-123">**Compiling the client application: The type or namespace name 'CalculatorClient' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

 <span data-ttu-id="2b98a-124">Ten błąd, jeśli plik Proxy.cs lub Proxy.vb nie należy dodawać do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="2b98a-124">You get this error if you do not add the Proxy.cs or Proxy.vb file to your client project.</span></span>  

<span data-ttu-id="2b98a-125">**Uruchamianie klienta: nieobsługiwany wyjątek: System.ServiceModel.EndpointNotFoundException: nie można połączyć z `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. Kod błędu TCP 10061: nie można ustanowić połączenia ponieważ aktywnie odrzucił w komputerze docelowym.**</span><span class="sxs-lookup"><span data-stu-id="2b98a-125">**Running the client: Unhandled Exception: System.ServiceModel.EndpointNotFoundException: Could not connect to `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. TCP error code 10061: No connection could be made because the target machine actively refused it.**</span></span>

<span data-ttu-id="2b98a-126">Ten błąd występuje, jeśli aplikacja kliencka jest uruchomiona bez konieczności uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="2b98a-126">This error occurs if you run the client application without running the service.</span></span>  
  
<span data-ttu-id="2b98a-127">**Nieobsługiwany wyjątek: System.ServiceModel.Security.SecurityNegotiationException: Negocjowanie zabezpieczeń protokołu SOAP z `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` dla elementu docelowego `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` nie powiodło się**</span><span class="sxs-lookup"><span data-stu-id="2b98a-127">**Unhandled Exception: System.ServiceModel.Security.SecurityNegotiationException: SOAP security negotiation with `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` for target `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` failed**</span></span>  

<span data-ttu-id="2b98a-128">Ten błąd występuje na komputerze przyłączonym do domeny, który nie ma łączności sieciowej.</span><span class="sxs-lookup"><span data-stu-id="2b98a-128">This error occurs on a domain-joined computer that does not have network connectivity.</span></span> <span data-ttu-id="2b98a-129">Łączenie komputera z siecią lub wyłączyć funkcję zabezpieczeń dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="2b98a-129">Either connect your computer to the network or turn off security for both the client and the service.</span></span> <span data-ttu-id="2b98a-130">Usługi należy zmodyfikować kod, który tworzy powiązanie WSHttpBinding do następujących.</span><span class="sxs-lookup"><span data-stu-id="2b98a-130">For the service, modify the code that creates the WSHttpBinding to the following.</span></span>  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

<span data-ttu-id="2b98a-131">Dla klienta, należy zmienić  **\<zabezpieczeń >** pod  **\<powiązania >** element do następującego:</span><span class="sxs-lookup"><span data-stu-id="2b98a-131">For the client, change the **\<security>** element under the **\<binding>** element to the following:</span></span>  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a><span data-ttu-id="2b98a-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b98a-132">See Also</span></span>  
 [<span data-ttu-id="2b98a-133">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="2b98a-133">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="2b98a-134">Szybki start: rozwiązywanie problemów z architekturą WCF</span><span class="sxs-lookup"><span data-stu-id="2b98a-134">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [<span data-ttu-id="2b98a-135">Rozwiązywanie problemów dotyczących konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2b98a-135">Troubleshooting Setup Issues</span></span>](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
