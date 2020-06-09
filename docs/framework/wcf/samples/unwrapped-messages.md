---
title: Nieopakowane komunikaty
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: ea90a6355f63d5fffd0cc3c5d350f83e395c31c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591088"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="3231c-102">Nieopakowane komunikaty</span><span class="sxs-lookup"><span data-stu-id="3231c-102">Unwrapped Messages</span></span>
<span data-ttu-id="3231c-103">Ten przykład pokazuje nieopakowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="3231c-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="3231c-104">Domyślnie treść komunikatu jest formatowana w taki sposób, że parametry operacji usługi są opakowane.</span><span class="sxs-lookup"><span data-stu-id="3231c-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="3231c-105">Poniższy przykład pokazuje `Add` komunikat żądania do `ICalculator` usługi w trybie opakowanym.</span><span class="sxs-lookup"><span data-stu-id="3231c-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
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
  
 <span data-ttu-id="3231c-106">`<Add>`Element w treści wiadomości otacza `n1` `n2` Parametry i.</span><span class="sxs-lookup"><span data-stu-id="3231c-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="3231c-107">Z kolei Poniższy przykład pokazuje odpowiedni komunikat w trybie nieopakowanym.</span><span class="sxs-lookup"><span data-stu-id="3231c-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
```  
  
 <span data-ttu-id="3231c-108">Nieopakowany komunikat nie otacza `n1` `n2` parametrów i w elemencie zawierającym, są bezpośrednimi elementami podrzędnymi elementu treści protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3231c-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3231c-109">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3231c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3231c-110">W tym przykładzie nieopakowany komunikat jest tworzony przez zastosowanie <xref:System.ServiceModel.MessageContractAttribute> do typu parametru operacji usługi i typu wartości zwracanej, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3231c-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="3231c-111">Aby umożliwić wyświetlanie wysyłanych i odbieranych komunikatów, ten przykład używa śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3231c-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="3231c-112">Ponadto program <xref:System.ServiceModel.WSHttpBinding> został skonfigurowany bez zabezpieczeń, aby zmniejszyć liczbę komunikatów, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="3231c-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="3231c-113">Wynikowy dziennik śledzenia (c:\logs\Message.log) można wyświetlić za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3231c-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="3231c-114">Aby wyświetlić zawartość wiadomości, wybierz pozycję **komunikaty** w lewym okienku narzędzia Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="3231c-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="3231c-115">Dzienniki śledzenia w tym przykładzie są skonfigurowane tak, aby były generowane w folderze C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="3231c-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="3231c-116">Utwórz ten folder przed uruchomieniem przykładu i nadaj użytkownikowi uprawnienia do zapisu w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3231c-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3231c-117">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="3231c-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3231c-118">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3231c-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3231c-119">Utwórz katalog C:\LOGS na potrzeby rejestrowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3231c-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="3231c-120">Nadaj użytkownikom uprawnienia do zapisu w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3231c-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="3231c-121">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3231c-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3231c-122">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3231c-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3231c-123">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3231c-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3231c-124">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3231c-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3231c-125">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="3231c-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3231c-126">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3231c-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
