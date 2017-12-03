---
title: "Niestandardowy dyspozytor kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81512576e1d26b63cf65b3a0c9992c2d273d2779
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-channel-dispatcher"></a>Niestandardowy dyspozytor kanału
Ten przykład demonstruje sposób tworzenia kanału stosu w niestandardowy sposób zaimplementowanie <xref:System.ServiceModel.ServiceHostBase> bezpośrednio oraz sposobu tworzenia dyspozytora niestandardowym kanale w środowisku hosta sieci Web. Dyspozytor kanału współdziała z <xref:System.ServiceModel.Channels.IChannelListener> ma akceptować komunikaty kanałów i pobiera ze stosu kanału. W tym przykładzie przedstawiono również podstawowy przykład demonstrujące sposób tworzenia kanału stosu w środowisku hosta sieci Web przy użyciu <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Niestandardowe obiektu ServiceHostBase.  
 W tym przykładzie implementuje typ podstawowy <xref:System.ServiceModel.ServiceHostBase> zamiast <xref:System.ServiceModel.ServiceHost> do pokazują, jak zastąpić [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] stosu implementacji z wiadomością niestandardową obsługę warstwy na szczycie stosu kanału. Należy przesłonić metodę wirtualną <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> tworzenie odbiorniki kanałów i dyspozytora kanału.  
  
 Do wdrożenia usługi sieci Web hostowanych, pobierz rozszerzenie usługi <xref:System.ServiceModel.Activation.VirtualPathExtension> z <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> kolekcji i dodaj go do <xref:System.ServiceModel.Channels.BindingParameterCollection> tak, aby warstwy transportowej wie, jak skonfigurować odbiornika kanałów na podstawie ustawień środowiska hostingu, który jest Internet Information Services (IIS) / ustawienia usługi aktywacji procesów systemu Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Niestandardowy dyspozytor kanału  
 Dyspozytor niestandardowym kanale rozszerza typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Ten typ implementuje logiki programowania warstwie kanału. W tym przykładzie, tylko <xref:System.ServiceModel.Channels.IReplyChannel> jest obsługiwane w przypadku wymiany komunikatów żądanie odpowiedź, ale dyspozytora kanału niestandardowych można łatwo rozszerzyć innych typów kanałów.  
  
 Dyspozytor otwierania odbiornika kanałów i następnie akceptuje pojedyncze kanału odpowiedzi. Z kanału rozpoczyna się do wysyłania wiadomości (liczba żądań) w pętli nieskończonej. Dla każdego żądania tworzy komunikat odpowiedzi i wysyła je z powrotem do klienta.  
  
## <a name="creating-a-response-message"></a>Tworzenie komunikatu odpowiedzi  
 Przetwarzanie komunikatów jest zaimplementowany w typie `MyServiceManager`. W `HandleRequest` metody `Action` nagłówka wiadomości jest najpierw sprawdzane w celu sprawdzenia, czy żądanie jest obsługiwane. Wstępnie zdefiniowane akcji SOAP "http://tempuri.org/HelloWorld/Hello" zdefiniowano zapewnienie filtrowania wiadomości. To jest podobny do koncepcji kontraktu usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacja <xref:System.ServiceModel.ServiceHost>.  
  
 W przypadku poprawne akcji SOAP próbki pobiera dane żądanej wiadomości i generuje odpowiadająca mu reakcja na żądanie, podobnie jak co jest widoczne w <xref:System.ServiceModel.ServiceHost> przypadku.  
  
 Specjalnie zlecenia HTTP GET są obsługiwane przez zwrócenie niestandardowe wiadomości w formacie HTML, w tym przypadku tak, aby przeglądać usługi z przeglądarki, aby zobaczyć, że jest on niepoprawnie skompilowany. Jeśli Akcja SOAP są niezgodne, Błąd wysyłania wiadomości Wstecz, aby wskazać, że żądanie nie jest obsługiwane.  
  
 Klient w tym przykładzie jest zwykłym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który nie przyjmuje żadnych z usługi. Usługa jest specjalnie zaprojektowane do dopasowania, otrzymasz od zwykłym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.ServiceHost> implementacji. W związku z tym kontraktu usługi jest wymagany na kliencie.  
  
## <a name="using-the-sample"></a>Przy użyciu próbki  
 Uruchomienie aplikacji klienckiej bezpośrednio tworzy następujące dane wyjściowe.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Możesz również przejść usługi z przeglądarki, aby na serwerze pobiera przetworzyć komunikatu HTTP GET. Należy dobrze sformatowany tekst HTML to pobiera ponownie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
