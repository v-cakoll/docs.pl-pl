---
title: Niestandardowy dyspozytor kanału
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 20574b4c849f312cb2cf55709d8d5e2a9b5dbca7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003109"
---
# <a name="custom-channel-dispatcher"></a>Niestandardowy dyspozytor kanału
W tym przykładzie przedstawiono sposób tworzenia kanału stosu w niestandardowy sposób przez zaimplementowanie <xref:System.ServiceModel.ServiceHostBase> bezpośrednio oraz sposób tworzenia dyspozytora niestandardowym kanale w środowisku hosta sieci Web. Dyspozytor kanału wchodzi w interakcję z <xref:System.ServiceModel.Channels.IChannelListener> do akceptowania kanałów oraz pobiera komunikaty ze stosu kanału. W tym przykładzie przedstawiono również podstawowy przykład, aby pokazać, jak utworzyć stos kanału w środowisku hosta sieci Web przy użyciu <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Custom ServiceHostBase  
 W tym przykładzie implementuje typu podstawowego <xref:System.ServiceModel.ServiceHostBase> zamiast <xref:System.ServiceModel.ServiceHost> wykazać, jak zastąpić implementacja stosu Windows Communication Foundation (WCF) z wiadomością niestandardową obsługę warstwy na szczycie stosu kanału. Należy przesłonić metodę wirtualną <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> tworzenie odbiorniki kanałów i Dyspozytor kanału.  
  
 Aby wdrożyć usługi hostowane w sieci Web, pobierz rozszerzenie usług <xref:System.ServiceModel.Activation.VirtualPathExtension> z <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> kolekcji i dodać go do <xref:System.ServiceModel.Channels.BindingParameterCollection> tak, aby warstwy transportowej wie, jak skonfigurować odbiornik kanału, w oparciu o ustawienia środowiska hostingu, który jest Internet Information Services (IIS) / ustawienia Windows Process Activation Service (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Niestandardowy dyspozytor kanału  
 Dyspozytor kanału niestandardowe rozszerza typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Ten typ implementuje logikę programistyczną warstwy kanału. W tym przykładzie, tylko <xref:System.ServiceModel.Channels.IReplyChannel> jest obsługiwana w przypadku wymiany komunikatów typu żądanie odpowiedź, ale dyspozytora niestandardowym kanale można ją łatwo rozszerzyć do innych typów kanałów.  
  
 Dyspozytor pierwszego otwierania odbiornika kanałów i następnie akceptuje pojedyncze kanału odpowiedzi. Za pomocą kanału rozpoczyna się do wysyłania wiadomości (żądania) w pętli nieskończonej. Dla każdego żądania tworzy komunikat odpowiedzi i wysyła go do klienta.  
  
## <a name="creating-a-response-message"></a>Tworzenie komunikatu odpowiedzi  
 Przetwarzanie komunikatów jest zaimplementowana w typie `MyServiceManager`. W `HandleRequest` metody `Action` nagłówek komunikatu najpierw jest sprawdzane w celu sprawdzenia, czy żądanie jest obsługiwane. A wstępnie zdefiniowane Akcja SOAP "http://tempuri.org/HelloWorld/Hello" jest zdefiniowany w celu zapewnienia filtrowanie komunikatów. Jest to podobne do koncepcji kontraktu usługi w implementacji WCF <xref:System.ServiceModel.ServiceHost>.  
  
 Dla protokołu SOAP akcji wielkie i małe, przykład pobiera dane żądanej wiadomości i generuje odpowiedniej odpowiedzi na żądanie, podobnie jak co to jest widoczny w <xref:System.ServiceModel.ServiceHost> przypadek.  
  
 Specjalnie czasownik HTTP GET są obsługiwane przez zwrócenie niestandardowy wiadomości HTML, w tym przypadku tak, aby przeglądać usługi z przeglądarki, aby zobaczyć, że jest on skompilowany poprawnie. Jeśli Akcja SOAP nie jest zgodna, Wyślij awarii komunikat Wstecz, aby wskazać, że żądanie nie jest obsługiwany.  
  
 Klient w tym przykładzie jest normalne klienta WCF, która nie przyjmuje żadnych z usługi. Tak, usługa jest specjalnie przeznaczony do dopasowania, otrzymasz od normalnych WCF<xref:System.ServiceModel.ServiceHost> implementacji. W rezultacie kontraktu usługi jest wymagany na kliencie.  
  
## <a name="using-the-sample"></a>Przy użyciu przykładu  
 Uruchomienie aplikacji klienckiej bezpośrednio generuje następujące wyniki.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Możesz także przejść usługi z przeglądarki, dzięki czemu wiadomości HTTP GET pobiera przetwarzane na serwerze. To otrzymuje należy dobrze HTML tekstu sformatowanego.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
