---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 7751e40762a99711302681f28a88d451087e4980
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044513"
---
# <a name="wshttpbinding"></a><span data-ttu-id="00020-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="00020-102">WSHttpBinding</span></span>
<span data-ttu-id="00020-103">Ten przykład pokazuje, jak zaimplementować typową usługę i typowy klient przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="00020-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="00020-104">Ten przykład składa się z programu konsolowego klienta (Client. exe) i biblioteki usług hostowanej przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="00020-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="00020-105">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="00020-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="00020-106">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="00020-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="00020-107">Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="00020-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="00020-108">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="00020-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00020-109">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="00020-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00020-110">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="00020-110">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="00020-111">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="00020-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00020-112">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="00020-112">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="00020-113">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="00020-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="00020-114">Ten przykład uwidacznia `ICalculator` kontrakt [ \<przy użyciu > WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="00020-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="00020-115">Konfiguracja tego powiązania została rozwinięta w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="00020-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->   
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"   
              transactionFlow="false"   
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"   
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"   
              textEncoding="utf-8"   
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"   
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"   
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="00020-116">W elemencie `binding` `maxReceivedMessageSize` Base wartość umożliwia skonfigurowanie maksymalnego rozmiaru komunikatu przychodzącego (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="00020-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="00020-117">`hostNameComparisonMode` Wartość umożliwia skonfigurowanie, czy nazwa hosta jest brana pod uwagę podczas usuwania komunikatów do usługi.</span><span class="sxs-lookup"><span data-stu-id="00020-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="00020-118">`messageEncoding` Wartość umożliwia skonfigurowanie, czy ma być używane kodowanie tekstu czy MTOM dla komunikatów.</span><span class="sxs-lookup"><span data-stu-id="00020-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="00020-119">`textEncoding` Wartość umożliwia skonfigurowanie kodowania znaków dla komunikatów.</span><span class="sxs-lookup"><span data-stu-id="00020-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="00020-120">`bypassProxyOnLocal` Wartość umożliwia skonfigurowanie, czy serwer proxy HTTP ma być używany do komunikacji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="00020-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="00020-121">`transactionFlow` Wartość określa, czy bieżąca transakcja jest przepływa (Jeśli skonfigurowano operację przepływu transakcji).</span><span class="sxs-lookup"><span data-stu-id="00020-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="00020-122">W elemencie ReliableSession > wartość włączone wartości logicznej określa, czy są włączone niezawodne sesje. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)</span><span class="sxs-lookup"><span data-stu-id="00020-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="00020-123">Wartość `ordered` określa, czy porządkowanie wiadomości jest zachowywane.</span><span class="sxs-lookup"><span data-stu-id="00020-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="00020-124">`inactivityTimeout` Wartość określa, jak długo sesja może być bezczynna, zanim zostanie uszkodzona.</span><span class="sxs-lookup"><span data-stu-id="00020-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="00020-125">Na > `mode` zabezpieczenia służy do konfigurowania trybu zabezpieczeń, który ma być używany. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="00020-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="00020-126">W tym przykładzie zabezpieczenia komunikatów są używane, co oznacza, że [ \<komunikat >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)jest określony wewnątrz > zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="00020-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="00020-127">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="00020-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="00020-128">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="00020-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00020-129">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="00020-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="00020-130">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="00020-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="00020-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00020-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="00020-132">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00020-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="00020-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00020-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
