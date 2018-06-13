---
title: Opis usługi
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d86a6a78995042f0c6a45cf6e40e31c3e515e8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504214"
---
# <a name="service-description"></a><span data-ttu-id="479d6-102">Opis usługi</span><span class="sxs-lookup"><span data-stu-id="479d6-102">Service Description</span></span>
<span data-ttu-id="479d6-103">Przykład opisu usługi pokazano, jak usługa można pobrać jego informacje o opisie usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="479d6-103">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="479d6-104">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), za pomocą operacji usługi dodatkowe zdefiniowane zwraca informacje opisowe dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="479d6-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="479d6-105">Zwracane informacje wymieniono adres podstawowy i punkty końcowe dla usługi.</span><span class="sxs-lookup"><span data-stu-id="479d6-105">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="479d6-106">Udostępnia te informacje przy użyciu <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, i <xref:System.ServiceModel.Description.ServiceDescription> klasy.</span><span class="sxs-lookup"><span data-stu-id="479d6-106">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="479d6-107">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="479d6-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="479d6-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="479d6-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="479d6-109">Ten przykład ma zmodyfikowanej wersji kontraktu Kalkulator o nazwie `IServiceDescriptionCalculator`.</span><span class="sxs-lookup"><span data-stu-id="479d6-109">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="479d6-110">Kontrakt definiuje operację dodatkowe usługi o nazwie `GetServiceDescriptionInfo` która zwraca ciąg wielowierszowego klientowi, który opisano podstawowy adres lub adresy i punkt końcowy usługi lub punkty końcowe dla usługi.</span><span class="sxs-lookup"><span data-stu-id="479d6-110">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 <span data-ttu-id="479d6-111">Kod implementacji `GetServiceDescriptionInfo` używa <xref:System.ServiceModel.Description.ServiceDescription> do listy punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="479d6-111">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="479d6-112">Ponieważ punktów końcowych usługi może mieć względne adresy, najpierw wymieniono adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="479d6-112">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="479d6-113">Aby uzyskać wszystkie te informacje, kod uzyskuje jego operacji kontekstu za pomocą <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="479d6-113">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="479d6-114"><xref:System.ServiceModel.ServiceHost> i jego <xref:System.ServiceModel.Description.ServiceDescription> obiektu są pobierane z kontekstu operacji.</span><span class="sxs-lookup"><span data-stu-id="479d6-114">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="479d6-115">Aby wyświetlić listę podstawowej punktów końcowych dla usługi, kod iteruje hosta usługi <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="479d6-115">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="479d6-116">Aby wyświetlić listę punktów końcowych usługi dla usługi, kod iteruje po kolekcji punktów końcowych opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="479d6-116">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
```  
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 <span data-ttu-id="479d6-117">Po uruchomieniu próbki, zobacz operacje Kalkulator, a następnie informacje o usłudze zwrócony przez `GetServiceDescriptionInfo` operacji.</span><span class="sxs-lookup"><span data-stu-id="479d6-117">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="479d6-118">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="479d6-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="479d6-119">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="479d6-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="479d6-120">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="479d6-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="479d6-121">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="479d6-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="479d6-122">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="479d6-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="479d6-123">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="479d6-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="479d6-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="479d6-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="479d6-125">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="479d6-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="479d6-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="479d6-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
  
## <a name="see-also"></a><span data-ttu-id="479d6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="479d6-127">See Also</span></span>
