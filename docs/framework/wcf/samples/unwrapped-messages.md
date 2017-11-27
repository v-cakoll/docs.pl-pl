---
title: Nieopakowane komunikaty
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99aa1d00c2992842a7019d4f4fc4aa98c25f644a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unwrapped-messages"></a><span data-ttu-id="02e98-102">Nieopakowane komunikaty</span><span class="sxs-lookup"><span data-stu-id="02e98-102">Unwrapped Messages</span></span>
<span data-ttu-id="02e98-103">W tym przykładzie przedstawiono nieopakowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="02e98-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="02e98-104">Domyślnie treść komunikatu jest sformatowany w taki sposób, że są opakowywane parametrów do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="02e98-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="02e98-105">Następujące przykładowe pokazuje `Add` komunikat żądania do `ICalculator` usługę w trybie opakowana.</span><span class="sxs-lookup"><span data-stu-id="02e98-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="02e98-106">`<Add>` Opakowuje element w treści wiadomości `n1` i `n2` parametrów.</span><span class="sxs-lookup"><span data-stu-id="02e98-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="02e98-107">Z kolei poniższy przykład przedstawia równoważne komunikat w trybie bez otoki.</span><span class="sxs-lookup"><span data-stu-id="02e98-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="02e98-108">Odkodowany wiadomości nie jest zawijany `n1` i `n2` parametrów w elemencie zawierającym są bezpośrednimi elementami podrzędnymi elementu treści protokołu soap.</span><span class="sxs-lookup"><span data-stu-id="02e98-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02e98-109">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="02e98-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="02e98-110">W tym przykładzie wiadomość bez otoki jest tworzony przez zastosowanie <xref:System.ServiceModel.MessageContractAttribute> typem parametru operacji usługi i typ zwracanej wartości, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="02e98-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="02e98-111">Aby umożliwić wyświetlanie wiadomości wysyłanych i odbieranych, w tym przykładzie użyto śledzenia.</span><span class="sxs-lookup"><span data-stu-id="02e98-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="02e98-112">Ponadto <xref:System.ServiceModel.WSHttpBinding> został skonfigurowany bez zabezpieczeń, aby zmniejszyć liczbę wiadomości, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="02e98-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="02e98-113">Wynikowa dziennika śledzenia (c:\logs\Message.log) można wyświetlić przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="02e98-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="02e98-114">Aby wyświetlić zawartość wiadomości, wybierz **wiadomości** zarówno lewego i prawego okienka narzędzia podglądu śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="02e98-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="02e98-115">Dzienniki śledzenia w tym przykładzie są skonfigurowane do wygenerowania do folderu C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="02e98-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="02e98-116">Utwórz ten folder przed uruchomieniem próbki i przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="02e98-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="02e98-117">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="02e98-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="02e98-118">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="02e98-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="02e98-119">Utwórz katalog C:\LOGS rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="02e98-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="02e98-120">Przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="02e98-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="02e98-121">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="02e98-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="02e98-122">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="02e98-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="02e98-123">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="02e98-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="02e98-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="02e98-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="02e98-125">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="02e98-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02e98-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="02e98-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="02e98-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02e98-127">See Also</span></span>
