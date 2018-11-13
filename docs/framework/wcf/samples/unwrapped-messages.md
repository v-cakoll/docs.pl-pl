---
title: Nieopakowane komunikaty
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 835312101ba9e0daaa7986a78c9a0040535881b9
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743943"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="f2da8-102">Nieopakowane komunikaty</span><span class="sxs-lookup"><span data-stu-id="f2da8-102">Unwrapped Messages</span></span>
<span data-ttu-id="f2da8-103">Niniejszy przykład pokazuje nieopakowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="f2da8-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="f2da8-104">Domyślnie treść komunikatu jest sformatowany w taki sposób, że zostaną opakowane parametrów do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f2da8-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="f2da8-105">Następujące przykładowe pokazuje `Add` komunikat żądania do `ICalculator` usługi w trybie opakowana.</span><span class="sxs-lookup"><span data-stu-id="f2da8-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s=http://www.w3.org/2003/05/soap-envelope  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="f2da8-106">`<Add>` Opakowuje element w treści komunikatu `n1` i `n2` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f2da8-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="f2da8-107">Natomiast poniższy przykład pokazuje równoważne komunikatu w trybie odkodowany.</span><span class="sxs-lookup"><span data-stu-id="f2da8-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 <span data-ttu-id="f2da8-108">Nieopakowane wiadomości nie jest zawijany `n1` i `n2` parametrów w elemencie zawierającego, są one bezpośrednie elementy podrzędne elementu treści protokołu soap.</span><span class="sxs-lookup"><span data-stu-id="f2da8-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2da8-109">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f2da8-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f2da8-110">W tym przykładzie tworzona jest wiadomość nieopakowanych, stosując <xref:System.ServiceModel.MessageContractAttribute> typem parametru operacji usługi i typ zwracanej wartości, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f2da8-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="f2da8-111">Aby umożliwić wyświetlanie komunikatów wysyłanych i odbieranych, w tym przykładzie użyto śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f2da8-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="f2da8-112">Ponadto <xref:System.ServiceModel.WSHttpBinding> została skonfigurowana bez zabezpieczeń w celu zmniejszenia liczby wiadomości, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="f2da8-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="f2da8-113">Wynikowy dziennika śledzenia (c:\logs\Message.log) mogą być wyświetlane za pomocą [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f2da8-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="f2da8-114">Zaznacz, aby wyświetlić zawartość wiadomości **wiadomości** zarówno po lewej stronie, jak i prawego okienka narzędzi przeglądarki danych śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="f2da8-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="f2da8-115">Dzienniki śledzenia w tym przykładzie są skonfigurowane do wygenerowania w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="f2da8-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="f2da8-116">Utwórz ten folder przed uruchomieniem przykładu i przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="f2da8-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f2da8-117">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="f2da8-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f2da8-118">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2da8-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f2da8-119">Utwórz katalog C:\LOGS rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f2da8-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="f2da8-120">Przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="f2da8-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="f2da8-121">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2da8-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f2da8-122">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2da8-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2da8-123">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f2da8-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2da8-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f2da8-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f2da8-125">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f2da8-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2da8-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f2da8-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="f2da8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2da8-127">See Also</span></span>
