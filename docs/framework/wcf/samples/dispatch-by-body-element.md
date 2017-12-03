---
title: "Wysyłanie według elementu treści"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c3624290176d93519ae420a98a7e93534d910fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="dispatch-by-body-element"></a>Wysyłanie według elementu treści
W tym przykładzie pokazano, jak wdrożyć alternatywny algorytm przypisywanie komunikatów przychodzących do operacji.  
  
 Domyślnie dyspozytora modelu usługi wybiera metodę odpowiednią obsługę wiadomości przychodzących, oparte na wiadomości WS-Addressing "Akcja" nagłówek lub równoważnych informacji w żądaniu SOAP protokołu HTTP.  
  
 Niektóre SOAP 1.1 w sieci Web usług stosy nie wykonuj WS-I Basic Profile 1.1 wytyczne, nie wysyła komunikaty oparte na identyfikator URI akcji, ale raczej opartego na nazwie kwalifikowanej XML pierwszego elementu wewnątrz treści protokołu SOAP. Podobnie te stosy po stronie klienta może wysyłać wiadomości z pustą lub dowolnego HTTP SoapAction nagłówka, który został dozwolone przez specyfikację SOAP 1.1.  
  
 Aby zmienić sposób komunikaty są wysyłane do metod, implementuje próbki <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu rozszerzalności na `DispatchByBodyElementOperationSelector`. Ta klasa wybiera operacje oparte na pierwszym elementem w treści wiadomości.  
  
 Konstruktor klasy oczekuje słownik wypełniane przy użyciu pary `XmlQualifiedName` i ciągi, zgodnie z którymi nazwy kwalifikowane wskazują nazwę pierwszego elementu podrzędnego treści protokołu SOAP i ciągi wskazują pasujące nazwy operacji. `defaultOperationName` To nazwa operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowywane do tego słownika:  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementacje są bardzo proste do kompilacji, ponieważ istnieje tylko jedna metoda w interfejsie: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Zadania tej metody jest do zbadania wiadomości przychodzącej i zwraca ciąg, który jest równe Nazwa metody na kontrakt usługi dla bieżącego punktu końcowego.  
  
 W tym przykładzie uzyskuje selektor operacji <xref:System.Xml.XmlDictionaryReader> komunikatu przychodzącego elementu body przy użyciu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Ta metoda już umieszcza czytnik na pierwszy element podrzędny elementu treści wiadomości, aby jest wystarczająca do bieżącego elementu nazwa i identyfikator URI przestrzeni nazw i połączyć je w `XmlQualifiedName` następnie używany do wyszukiwania odpowiadająca mu operacja z Słownik posiadanych przez selektor operacji.  
  
```  
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 Dostęp do treści wiadomości z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lub dowolnej z metod, które zapewniają dostęp do zawartości w treści wiadomości powoduje, że komunikat, który ma być oznaczona jako "do odczytu", co oznacza, że wiadomość jest nieprawidłowa dla dalszego przetwarzania. W związku z tym selektor operacji tworzy kopię komunikat przychodzący z metodą poniższym kodem. Ponieważ proces czytający pozycji nie została zmieniona podczas kontroli, mogą się odwoływać linie nowo utworzony komunikat do którego właściwości wiadomości i nagłówki komunikatów są również kopiowane, co powoduje dokładne klonowania oryginalnej wiadomości:  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Dodawanie selektor operacji do usługi  
 Selektory operacji wysyłania usługi są rozszerzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dyspozytora. Wybierania metody w kanale wywołania zwrotnego kontraktów dupleksowych, są również selektorów operacji klienta, które znacznie działa jak selektorów operacji wysyłania opisane w tym miejscu, ale które nie są jawnie wymienione w tym przykładzie.  
  
 Podobnie jak większość rozszerzenia modelu usługi selektorów operacji wysyłania są dodawane do dyspozytora za pomocą zachowań. A *zachowanie* jest obiekt konfiguracji, który dodaje jedno lub więcej rozszerzeń do wysyłania środowiska wykonawczego (lub środowiska uruchomieniowego klienta) albo w przeciwnym razie zmienia jego ustawienia.  
  
 Ponieważ selektory operacji zakresu kontraktu, działanie odpowiednie do zaimplementowania w tym miejscu jest <xref:System.ServiceModel.Description.IContractBehavior>. Ponieważ interfejs jest wdrażany na <xref:System.Attribute> klasy jak pokazano w poniższym kodzie, zachowanie można deklaratywnie dodać do dowolnego kontraktu usługi. Zawsze, gdy <xref:System.ServiceModel.ServiceHost> jest otwarty i środowisko wykonawcze wysyłce jest wbudowana, wszystkie zachowania znaleziono jako atrybuty kontrakty, operacje i implementacji usługi lub jako element w konfiguracji usługi są automatycznie dodawane i później monit współtworzenia rozszerzenia lub zmodyfikować domyślną konfigurację.  
  
 Jednak poniższy fragment kodu przedstawia tylko implementacja metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, który ma wpływ zmian konfiguracji dla dyspozytora w tym przykładzie. Inne metody są niewidoczne, ponieważ zwracany do obiektu wywołującego w bez działał.  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Najpierw <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementacja ustawia słownik selektor operacji wyszukiwania przez Iterowanie po <xref:System.ServiceModel.Description.OperationDescription> elementów w punkcie końcowym usługi <xref:System.ServiceModel.Description.ContractDescription>. Następnie, każdy opis operacji jest sprawdzane pod kątem obecności `DispatchBodyElementAttribute` zachowanie, implementacja <xref:System.ServiceModel.Description.IOperationBehavior> jest też definiowany w tym przykładzie. Ta klasa jest również zachowanie, jest w stanie pasywnym i nie wpływa aktywnie jakiekolwiek zmiany konfiguracji do środowiska wykonawczego wysyłania. Zwróć wszystkie jego metody do obiektu wywołującego bez konieczności przełączania żadnych akcji. Zachowanie operacji istnieje tylko tak, aby metadane wymagane dla nowego wysyłania mechanizmu, czyli kwalifikowaną nazwę elementu body na wystąpienie, którego operacji jest zaznaczone, może być skojarzony z odpowiednich działań.  
  
 Jeśli takie zachowanie zostanie znaleziony, parę wartości utworzone na podstawie nazwy kwalifikowanej XML (`QName` właściwości) i nazwa operacji (`Name` właściwości) zostanie dodany do słownika.  
  
 Po słowniku zostanie wypełnione, nowy `DispatchByBodyElementOperationSelector` jest utworzone z tymi informacjami i Ustaw jako selektor operacji wysyłania środowiska uruchomieniowego:  
  
```  
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a>Wdrażanie usługi  
 Zachowanie zaimplementowana w tym przykładzie bezpośrednio wpływa na sposób komunikaty z sieci są interpretowane i wysyłane, która jest funkcją kontraktu usługi. W rezultacie zachowanie powinny zostać zadeklarowane na poziomie kontraktu usługi w implementacji usługi wybierający z niego korzystać.  
  
 Dotyczy usługi projektu próbki `DispatchByBodyElementBehaviorAttribute` kontraktu zachowania do `IDispatchedByBody` usługi umowy oraz etykiety z tych dwóch operacji `OperationForBodyA()` i `OperationForBodyB()` z `DispatchBodyElementAttribute` zachowanie operacji. Po otwarciu usługi hosta dla usługi, który implementuje ten kontrakt metadanych zostaje pobrana przez konstruktora dyspozytora w sposób opisany wcześniej.  
  
 Selektor operacji wywołuje wyłącznie na podstawie elementu treści wiadomości i ignoruje "Akcja", dlatego jest wymagany w celu Poinformuj środowiska uruchomieniowego nie, aby sprawdzić nagłówka "Action" zwrócony odpowiedzi na przypisując symbol wieloznaczny "*" do `ReplyAction` właściwości <xref:System.ServiceModel.OperationContractAttribute>. Ponadto jest wymagany do operacji domyślny, który ma właściwość "Akcja" symbol wieloznaczny "\*". Operacja domyślna odbiera wszystkie komunikaty, które nie mogą być wysyłane i nie ma `DispatchBodyElementAttribute`:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 Przykładowe zastosowanie usługi jest prosta. Każda metoda opakowuje odebranego komunikatu do komunikatu odpowiedzi i zwraca go do klienta.  
  
## <a name="running-and-building-the-sample"></a>Uruchomiona i tworzenia próbki  
 Po uruchomieniu przykładowej zawartości w treści odpowiedzi operacji są wyświetlane w oknie konsoli klienta podobne do następujących danych wyjściowych (sformatowanych).  
  
 Klient wysyła wiadomości do usługi którego zawartości, nosi nazwę elementu treści `bodyA`, `bodyB`, i `bodyX`odpowiednio. Jak można odroczyć z poprzednich opis i kontraktu usługi pokazano, przychodzących komunikatów z `bodyA` element jest wysyłane do `OperationForBodyA()` metody. Ponieważ nie istnieje bez obiektu docelowego jawne wysyłania wiadomości z `bodyX` elementu treści wiadomości jest wysyłane do `DefaultOperation()`. Każdej operacji usługi do określonej metody elementu jest zawijana treści odebranego komunikatu i zwraca go, które skonfigurowano w celu skorelowania danych wejściowych i wyjściowych wiadomości wyraźnie dla tego przykładu:  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Zobacz też
