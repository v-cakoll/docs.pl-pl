---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143372"
---
# <a name="wshttpbinding"></a><span data-ttu-id="b5d2d-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b5d2d-102">WSHttpBinding</span></span>
<span data-ttu-id="b5d2d-103">W tym przykładzie pokazano, jak zaimplementować typową usługę i typowego klienta przy użyciu programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b5d2d-104">Ten przykład składa się z programu konsoli klienta (client.exe) i biblioteki usług hostowanych przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b5d2d-105">Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="b5d2d-106">Kontrakt jest definiowany `ICalculator` przez interfejs, który udostępnia operacje matematyczne (dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="b5d2d-107">Klient sprawia, że synchroniczne żądania do danej operacji matematycznej i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="b5d2d-108">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b5d2d-109">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5d2d-110">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b5d2d-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5d2d-112">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="b5d2d-113">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b5d2d-114">Ten przykład udostępnia `ICalculator` kontrakt przy użyciu [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="b5d2d-115">Konfiguracja tego powiązania została rozwinięta w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="b5d2d-116">W elemencie podstawowym `binding` `maxReceivedMessageSize` wartość umożliwia skonfigurowanie maksymalnego rozmiaru wiadomości przychodzącej (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="b5d2d-117">Wartość `hostNameComparisonMode` umożliwia skonfigurowanie, czy nazwa hosta jest brana pod uwagę podczas od multipleksowania komunikatów do usługi.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="b5d2d-118">Wartość `messageEncoding` umożliwia skonfigurowanie, czy do używania kodowania tekstu lub MTOM dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="b5d2d-119">Wartość `textEncoding` umożliwia skonfigurowanie kodowania znaków dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="b5d2d-120">Wartość `bypassProxyOnLocal` umożliwia skonfigurowanie, czy ma być używany serwer proxy HTTP do komunikacji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="b5d2d-121">Wartość `transactionFlow` konfiguruje, czy bieżąca transakcja jest przepływa (jeśli operacja jest skonfigurowana dla przepływu transakcji).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="b5d2d-122">W [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element włączone wartości logicznej konfiguruje, czy niezawodne sesje są włączone.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="b5d2d-123">Wartość `ordered` konfiguruje, czy kolejność wiadomości jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="b5d2d-124">Wartość `inactivityTimeout` konfiguruje, jak długo sesja może być bezczynna przed błędem.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="b5d2d-125">W [ \<>zabezpieczeń ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` wartość konfiguruje, który tryb zabezpieczeń powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="b5d2d-126">W tym przykładzie używane są zabezpieczenia wiadomości, dlatego [ \<>wiadomości](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) jest określony wewnątrz [ \<>zabezpieczeń ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="b5d2d-127">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b5d2d-128">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b5d2d-129">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="b5d2d-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b5d2d-130">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="b5d2d-131">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="b5d2d-132">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="b5d2d-133">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
