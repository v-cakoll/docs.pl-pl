---
title: Niestandardowy dyspozytor kanału
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: ea1bdd470855d1b2f6572a15ce45f9b90d74fdca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145128"
---
# <a name="custom-channel-dispatcher"></a>Niestandardowy dyspozytor kanału
W tym przykładzie pokazano, jak utworzyć stos kanału <xref:System.ServiceModel.ServiceHostBase> w sposób niestandardowy, implementując bezpośrednio i jak utworzyć niestandardowego dyspozytora kanału w środowisku hosta sieci Web. Dyspozytor kanału <xref:System.ServiceModel.Channels.IChannelListener> współdziała z do akceptowania kanałów i pobiera wiadomości ze stosu kanału. Ten przykład zawiera również podstawowy przykład, aby pokazać, jak zbudować <xref:System.ServiceModel.Activation.VirtualPathExtension>stos kanału w środowisku hosta sieci Web przy użyciu .  
  
## <a name="custom-servicehostbase"></a>Niestandardowa baza hosta usługi  
 W tym przykładzie <xref:System.ServiceModel.ServiceHostBase> implementuje <xref:System.ServiceModel.ServiceHost> typ podstawowy, a nie wykazać, jak zastąpić implementacji stosu Programu Windows Communication Foundation (WCF) niestandardową warstwą obsługi komunikatów na górze stosu kanału. Można zastąpić metodę wirtualną <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> do tworzenia odbiorników kanałów i dyspozytora kanału.  
  
 Aby zaimplementować usługę hostowania <xref:System.ServiceModel.Activation.VirtualPathExtension> sieci <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> Web, pobierz rozszerzenie <xref:System.ServiceModel.Channels.BindingParameterCollection> usługi z kolekcji i dodaj je do warstwy transportu, aby warstwa transportu wiedziała, jak skonfigurować odbiornik kanałów na podstawie ustawień środowiska hostingu, czyli ustawień usługi internetowego usług informacyjnych (IIS)/usługi aktywacji procesów systemu Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Niestandardowy dyspozytor kanału  
 Niestandardowy dyspozytor kanału <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>rozszerza typ . Ten typ implementuje logikę programowania warstwy kanału. W tym przykładzie jest obsługiwany tylko <xref:System.ServiceModel.Channels.IReplyChannel> dla wzorca wymiany wiadomości żądanie odpowiedź, ale niestandardowy dyspozytor kanału można łatwo rozszerzyć na inne typy kanałów.  
  
 Dyspozytor najpierw otwiera odbiornik kanału, a następnie akceptuje kanał odpowiedzi singleton. Z kanału, zaczyna wysyłać wiadomości (żądania) w nieskończonej pętli. Dla każdego żądania tworzy komunikat odpowiedzi i wysyła go z powrotem do klienta.  
  
## <a name="creating-a-response-message"></a>Tworzenie wiadomości odpowiedzi  
 Przetwarzanie wiadomości jest implementowane `MyServiceManager`w typie . W `HandleRequest` metodzie `Action` nagłówek wiadomości jest najpierw sprawdzany, aby zobaczyć, czy żądanie jest obsługiwane. Wstępnie zdefiniowana akcja SOAPhttp://tempuri.org/HelloWorld/Hello" " jest zdefiniowana w celu zapewnienia filtrowania wiadomości. Jest to podobne do koncepcji umowy serwisowej <xref:System.ServiceModel.ServiceHost>w realizacji WCF .  
  
 W przypadku akcji poprawnej protokołu SOAP przykład pobiera żądane dane wiadomości i generuje odpowiednią odpowiedź <xref:System.ServiceModel.ServiceHost> na żądanie podobną do widocznej w przypadku.  
  
 Specjalnie obsługi zlecenia HTTP-GET przez zwrócenie niestandardowego komunikatu HTML, w tym przypadku, dzięki czemu można przeglądać usługę z przeglądarki, aby zobaczyć, że jest skompilowany poprawnie. Jeśli akcja SOAP nie jest zgodna, wyślij komunikat o błędzie z powrotem, aby wskazać, że żądanie nie jest obsługiwane.  
  
 Klient tego przykładu jest normalnym klientem WCF, który nie zakłada niczego z usługi. Tak, usługa jest specjalnie zaprojektowany, aby dopasować to,<xref:System.ServiceModel.ServiceHost> co można uzyskać z normalnej implementacji WCF. W rezultacie tylko umowa serwisowa jest wymagana na kliencie.  
  
## <a name="using-the-sample"></a>Korzystanie z próbki  
 Uruchamianie aplikacji klienckiej bezpośrednio generuje następujące dane wyjściowe.  
  
```output  
Client is talking to a request/reply WCF service.
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Można również przeglądać usługę z przeglądarki, tak aby komunikat HTTP-GET jest przetwarzany na serwerze. Spowoduje to powrót dobrze sformatowanego tekstu HTML.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
