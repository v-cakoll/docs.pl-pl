---
title: "Powiązanie danych w kliencie formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 905d010c1ecdab1fc7b2c99e6d720b85ad40be32
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-a-windows-forms-client"></a><span data-ttu-id="881ff-102">Powiązanie danych w kliencie formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="881ff-102">Data Binding in a Windows Forms Client</span></span>
<span data-ttu-id="881ff-103">W tym przykładzie pokazano sposób powiązania danych zwróconych przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="881ff-103">This sample demonstrates how to bind to data returned by a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Windows Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="881ff-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="881ff-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>  
  
 <span data-ttu-id="881ff-105">W przykładzie pokazano to usługa, która implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="881ff-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="881ff-106">Próbka składa się z klienta aplikacji formularzy systemu Windows (.exe) i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="881ff-106">The sample consists of a client Windows Forms application (.exe) and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="881ff-107">Kontrakt jest definiowana za pomocą `IWeatherService` interfejsu, który udostępnia operacji o nazwie `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="881ff-107">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="881ff-108">Ta operacja akceptuje tablicy miast i zwraca tablicę `WeatherData` obiekty reprezentujące wysoki i niski prognozowanych temperatura miasta.</span><span class="sxs-lookup"><span data-stu-id="881ff-108">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="881ff-109">Powiązanie danych występuje na komputerze klienckim w aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="881ff-109">The data binding occurs on the client in the Windows Forms application.</span></span> <span data-ttu-id="881ff-110">A `DataGridView` jest zdefiniowany w narzędziu Projektant dla formularzy systemu Windows, czyli graficzną reprezentację danych.</span><span class="sxs-lookup"><span data-stu-id="881ff-110">A `DataGridView` is defined in the Windows Forms designer, which is a graphical representation of the data.</span></span> <span data-ttu-id="881ff-111">Pośrednik o nazwie `BindingSource` tworzona jest również.</span><span class="sxs-lookup"><span data-stu-id="881ff-111">An intermediary named `BindingSource` is also created.</span></span> <span data-ttu-id="881ff-112">Źródło danych `BindingSource` ma ustawioną wartość tablicy danych zwróconych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="881ff-112">The data source of `BindingSource` is set to the data array returned by the service.</span></span> <span data-ttu-id="881ff-113">Celem `BindingSource` jest zapewnienie warstwę pośredni między danymi i widoku danych.</span><span class="sxs-lookup"><span data-stu-id="881ff-113">The purpose of the `BindingSource` is to provide a layer of indirection between the data and the data view.</span></span> <span data-ttu-id="881ff-114">Wszystkie interakcje z danymi, takich jak przeglądanie, sortowanie, filtrowanie i aktualizowanie, jest realizowane za pomocą wywołania `BindingSource` składnika.</span><span class="sxs-lookup"><span data-stu-id="881ff-114">All interaction with the data, such as navigating, sorting, filtering, and updating, is accomplished with calls to the `BindingSource` component.</span></span> <span data-ttu-id="881ff-115">Powiązywanie danych do celu `DataGridView`, `datasource` z `DataGridView` następnie ustawiono `BindingSource` obiektu.</span><span class="sxs-lookup"><span data-stu-id="881ff-115">To accomplish data binding to the `DataGridView`, the `datasource` of the `DataGridView` is then set to the `BindingSource` object.</span></span> <span data-ttu-id="881ff-116">Wszystkie dane zwrócone w wyniku [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] graficznie zebrane usługi dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="881ff-116">All of the data returned from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is then displayed graphically to the user.</span></span>  <span data-ttu-id="881ff-117">Za każdym razem, gdy użytkownik kliknie przycisk, zwrócone dane są automatycznie aktualizowane w powiązanym z danymi `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="881ff-117">Every time the user clicks the button, the returned data is automatically updated in the data-bound `DataGridView`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="881ff-118">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="881ff-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="881ff-119">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="881ff-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="881ff-120">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="881ff-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="881ff-121">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="881ff-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="881ff-122">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="881ff-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="881ff-123">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="881ff-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="881ff-124">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="881ff-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="881ff-125">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="881ff-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
  
## <a name="see-also"></a><span data-ttu-id="881ff-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="881ff-126">See Also</span></span>
