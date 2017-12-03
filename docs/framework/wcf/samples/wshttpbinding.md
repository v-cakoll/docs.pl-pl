---
title: WSHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 522042606681fe2dfc0ee2bc10b5a5f062a93d55
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="wshttpbinding"></a><span data-ttu-id="48a94-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="48a94-102">WSHttpBinding</span></span>
<span data-ttu-id="48a94-103">W tym przykładzie pokazano, jak do zaimplementowania typowych usługi i typowego klienta przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="48a94-103">This sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="48a94-104">W tym przykładzie składa się z konsoli programu klienckiego (client.exe) i biblioteki usługi hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="48a94-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="48a94-105">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="48a94-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="48a94-106">Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="48a94-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="48a94-107">Klient wysyła żądań synchronicznych operacji matematycznych danego i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="48a94-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="48a94-108">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="48a94-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48a94-109">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="48a94-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48a94-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="48a94-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="48a94-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="48a94-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48a94-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="48a94-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="48a94-113">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="48a94-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="48a94-114">Ten przykład przedstawia `ICalculator` kontraktu przy użyciu [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="48a94-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="48a94-115">W pliku Web.config została rozszerzona konfiguracji tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="48a94-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="48a94-116">Na podstawie `binding` elementu `maxReceivedMessageSize` wartość można skonfigurować maksymalny rozmiar wiadomości przychodzącej (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="48a94-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="48a94-117">`hostNameComparisonMode` Wartość umożliwia skonfigurowanie, czy nazwa hosta jest uznawany za podczas usuwania Multipleksowanie komunikaty do usługi.</span><span class="sxs-lookup"><span data-stu-id="48a94-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="48a94-118">`messageEncoding` Wartość umożliwia skonfigurowanie, czy ma być używany tekst lub MTOM kodowania dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="48a94-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="48a94-119">`textEncoding` Wartość umożliwia konfigurowanie kodowanie znaków dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="48a94-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="48a94-120">`bypassProxyOnLocal` Wartość umożliwia skonfigurowanie, czy używany serwer proxy HTTP do lokalnej komunikacji.</span><span class="sxs-lookup"><span data-stu-id="48a94-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="48a94-121">`transactionFlow` Wartość określa, czy bieżąca transakcja jest umieszczane (Jeśli operacja jest skonfigurowana dla przepływu transakcji).</span><span class="sxs-lookup"><span data-stu-id="48a94-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="48a94-122">Na [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) elementu włączone wartość logiczna określa, czy włączono niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="48a94-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="48a94-123">`ordered` Wartość określa, czy komunikat kolejność jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="48a94-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="48a94-124">`inactivityTimeout` Wartość określa, jak długo sesja może być bezczynne przed jest błędny.</span><span class="sxs-lookup"><span data-stu-id="48a94-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="48a94-125">Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` wartość konfiguruje tryb zabezpieczeń, którym powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="48a94-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="48a94-126">W tym przykładzie zabezpieczeń wiadomości jest używany, która jest dlaczego [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) określono wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="48a94-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="48a94-127">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="48a94-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="48a94-128">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="48a94-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48a94-129">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="48a94-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="48a94-130">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="48a94-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="48a94-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48a94-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="48a94-132">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48a94-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="48a94-133">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="48a94-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a94-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48a94-134">See Also</span></span>
