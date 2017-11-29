---
title: "Powiązywanie danych w kliencie programu ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ceb63315d94c0deed161bb294e8f61bf523bb63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="4d2c6-102">Powiązywanie danych w kliencie programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4d2c6-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="4d2c6-103">W tym przykładzie pokazano, jak można powiązać danych zwróconych przez typowe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w aplikacji formularzy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-103">This sample demonstrates how to bind data returned by a typical [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Web Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d2c6-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4d2c6-105">W przykładzie pokazano to usługa, która implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="4d2c6-106">Próbka składa się z aplikacja formularzy sieci Web dostępnych w przeglądarce klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="4d2c6-106">The sample consists of a client Web Forms application accessible from a browser and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="4d2c6-107">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="4d2c6-108">Kontrakt jest definiowana za pomocą `IWeatherService` interfejsu, który udostępnia operacji o nazwie `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="4d2c6-109">Ta operacja akceptuje tablicy miast i zwraca tablicę `WeatherData` obiekty reprezentujące wysoki i niski prognozowanych temperatura miasta.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="4d2c6-110">Na [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] strony .aspx klienta, sieci DataGrid Web definiowana kontrolka, który zawiera graficzną reprezentację danych zwróconych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-110">On the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="4d2c6-111">Kod dla wywołań strony .aspx [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi pogody danych i zwraca dane do tablicy `WeatherData` obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-111">Code on the .aspx page calls the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="4d2c6-112">DataGrid Określa, gdzie można uzyskać za pomocą przez ustawienie jej `DataSource` właściwości do tej tablicy.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="4d2c6-113">Powiązanie danych występuje podczas wywołania do elementu DataGrid `DataBind` metody.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="4d2c6-114">Wszystkie ten kod znajduje się wewnątrz.`aspx`</span><span class="sxs-lookup"><span data-stu-id="4d2c6-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="4d2c6-115">strony `Page_Load` metody, aby zawsze użytkownik odświeża stronę przeglądarki, dane jest aktualizowany w elemencie DataGrid.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d2c6-116">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="4d2c6-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4d2c6-117">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d2c6-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4d2c6-118">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d2c6-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4d2c6-119">Klient ten przykład jest witryną sieci Web, działającą na serwerze sieci Web development.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="4d2c6-120">Aby uruchomić serwera wdrożeniowego sieci Web, wpisz następujące polecenie w wierszu polecenia: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-120">To launch the development Web server, type the following at the command prompt: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="4d2c6-121">Następnie przejdź do http://localhost: 8000/klienta.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-121">Then browse to http://localhost:8000/client.</span></span> <span data-ttu-id="4d2c6-122">Aby uruchomić ten przykład na komputerach, należy zastąpić wszystkie odwołania do `localhost` w pliku Web.config klienta z nazwą komputera serwera.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d2c6-123">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d2c6-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4d2c6-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d2c6-125">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d2c6-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d2c6-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a><span data-ttu-id="4d2c6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d2c6-127">See Also</span></span>
