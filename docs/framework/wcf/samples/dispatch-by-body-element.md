---
title: Wysyłanie według elementu treści
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 19913cdaa47d766f62a313e216a653ac69633a99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594702"
---
# <a name="dispatch-by-body-element"></a>Wysyłanie według elementu treści
Ten przykład pokazuje, jak zaimplementować alternatywny algorytm przypisywania komunikatów przychodzących do operacji.  
  
 Domyślnie Dyspozytor modelu usług wybiera odpowiednią metodę obsługi dla komunikatu przychodzącego na podstawie nagłówka "Akcja" WS-Addressing "lub równoważne informacje w żądaniu protokołu HTTP SOAP.  
  
 Niektóre stosy usług sieci Web SOAP 1,1, które nie są zgodne z wytycznymi dotyczącymi profilu WS-I Basic 1,1 nie wysyłają komunikatów na podstawie identyfikatora URI akcji, ale raczej na podstawie kwalifikowanej nazwy XML pierwszego elementu wewnątrz treści protokołu SOAP. Podobnie po stronie klienta te stosy mogą wysyłać komunikaty z pustym lub dowolnym nagłówkiem HTTP SoapAction, który był dozwolony przez specyfikację protokołu SOAP 1,1.  
  
 Aby zmienić sposób wysyłania komunikatów do metod, przykład implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejs rozszerzalności na `DispatchByBodyElementOperationSelector` . Ta klasa wybiera operacje na podstawie pierwszego elementu treści komunikatu.  
  
 Konstruktor klasy oczekuje słownika zawierającego pary `XmlQualifiedName` i ciągi, według których kwalifikowane nazwy wskazują nazwę pierwszego elementu podrzędnego treści protokołu SOAP, a ciągi wskazują pasującą nazwę operacji. `defaultOperationName`Jest nazwą operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowane do tego słownika:  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementacje są bardzo proste, ponieważ istnieje tylko jedna metoda w interfejsie: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> . Zadaniem tej metody jest zbadanie komunikatu przychodzącego i zwrócenie ciągu, który jest równy nazwie metody w kontrakcie usługi dla bieżącego punktu końcowego.  
  
 W tym przykładzie selektor operacji uzyskuje <xref:System.Xml.XmlDictionaryReader> dla treści wiadomości przychodzącej przy użyciu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> . Ta metoda już umieszcza czytnik w pierwszym elemencie podrzędnym treści wiadomości, dzięki czemu można uzyskać nazwę bieżącego elementu i identyfikator URI przestrzeni nazw, a następnie połączyć je w `XmlQualifiedName` celu wyszukania odpowiedniej operacji ze słownika przechowywanego przez selektor operacji.  
  
```csharp
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
  
 Uzyskiwanie dostępu do treści wiadomości za pomocą <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lub dowolnych innych metod zapewniających dostęp do zawartości treści wiadomości powoduje, że komunikat zostanie oznaczony jako "read" (odczyt), co oznacza, że komunikat jest nieprawidłowy do dalszej obróbki. W związku z tym selektor operacji tworzy kopię komunikatu przychodzącego za pomocą metody pokazanej w poniższym kodzie. Ponieważ pozycja czytnika nie została zmieniona podczas inspekcji, może odwoływać się do nowo utworzonego komunikatu, do którego są również kopiowane właściwości wiadomości i nagłówki wiadomości, co powoduje dokładne klonowanie oryginalnej wiadomości:  
  
```csharp
private Message CreateMessageCopy(Message message,
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a>Dodawanie selektora operacji do usługi  
 Selektory operacji wysyłania usług są rozszerzeniami do dyspozytora Windows Communication Foundation (WCF). W przypadku wybierania metod w kanale wywołania zwrotnego w ramach kontraktów dupleksowych istnieją również selektory operacji klienta, które działają bardzo podobnie do selektorów operacji wysyłania opisanych tutaj, ale które nie zostały jawnie omówione w tym przykładzie.  
  
 Takie jak większość rozszerzeń modelu usług, selektory operacji wysyłania są dodawane do dyspozytora przy użyciu zachowań. *Zachowanie* jest obiektem konfiguracji, który dodaje jeden lub więcej rozszerzeń do środowiska uruchomieniowego wysyłania (lub do środowiska uruchomieniowego klienta) lub w inny sposób zmienia jego ustawienia.  
  
 Ponieważ selektory operacji mają zakres kontraktu, odpowiednie zachowanie, które należy zaimplementować, to <xref:System.ServiceModel.Description.IContractBehavior> . Ponieważ interfejs jest implementowany w <xref:System.Attribute> klasie pochodnej, jak pokazano w poniższym kodzie, zachowanie można deklaratywnie dodać do dowolnego kontraktu usługi. Za każdym razem <xref:System.ServiceModel.ServiceHost> , gdy jest otwarty, a środowisko uruchomieniowe wysyłania zostało skompilowane, wszystkie zachowania, które znajdują się w ramach kontraktów, operacji i implementacji usług lub jako element w konfiguracji usługi są automatycznie dodawane, a następnie proszeni do współtworzenia rozszerzeń lub modyfikowania konfiguracji domyślnej.  
  
 W przypadku zwięzłości Poniższy fragment kodu pokazuje tylko implementację metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> , która wpływa na zmiany konfiguracji dyspozytora w tym przykładzie. Inne metody nie są wyświetlane, ponieważ zwracają do obiektu wywołującego bez wykonywania żadnej pracy.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Najpierw <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementacja powoduje skonfigurowanie słownika wyszukiwania dla selektora operacji przez iterację <xref:System.ServiceModel.Description.OperationDescription> elementów w punkcie końcowym usługi <xref:System.ServiceModel.Description.ContractDescription> . Następnie każdy opis operacji jest sprawdzany pod kątem obecności `DispatchBodyElementAttribute` zachowania, a implementacja, <xref:System.ServiceModel.Description.IOperationBehavior> która jest również zdefiniowana w tym przykładzie. Chociaż ta klasa jest również zachowaniem, jest pasywna i nie wprowadza żadnych zmian w konfiguracji w czasie wykonywania wysyłania. Wszystkie jego metody zwracają do obiektu wywołującego bez podejmowania żadnych działań. Zachowanie tej operacji istnieje tylko wtedy, gdy metadane wymagane dla nowego mechanizmu wysyłania, czyli kwalifikowana nazwa elementu treści, dla którego wystąpienie operacji jest zaznaczone, mogą być skojarzone z odpowiednimi operacjami.  
  
 Jeśli takie zachowanie zostanie znalezione, para wartości utworzona na podstawie kwalifikowanej nazwy XML ( `QName` Property) i nazwy operacji ( `Name` Property) zostanie dodana do słownika.  
  
 Po wypełnieniu słownika zostanie utworzony nowy `DispatchByBodyElementOperationSelector` z tymi informacjami i ustawiony jako selektor operacji dla środowiska uruchomieniowego wysyłania:  
  
```csharp
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
  
## <a name="implementing-the-service"></a>Implementowanie usługi  
 Zachowanie zaimplementowane w tym przykładzie bezpośrednio wpływa na sposób interpretowania i wysyłania komunikatów z sieci, która jest funkcją kontraktu usługi. W związku z tym zachowanie powinno być zadeklarowane na poziomie kontraktu usługi w każdej implementacji usługi, która wybierze jej użycie.  
  
 Przykładowa usługa projektu stosuje `DispatchByBodyElementBehaviorAttribute` zachowanie kontraktu do `IDispatchedByBody` kontraktu usługi i etykiety każdej z tych dwóch operacji `OperationForBodyA()` oraz `OperationForBodyB()` z `DispatchBodyElementAttribute` zachowaniem operacji. W przypadku otwarcia hosta usługi dla usługi implementującej ten kontrakt te metadane są pobierane przez konstruktora dyspozytora zgodnie z wcześniejszym opisem.  
  
 Ponieważ selektor operacji jest wysyłany wyłącznie na podstawie treści wiadomości i ignoruje "działanie", jest wymagane, aby poinformować środowisko uruchomieniowe, aby nie sprawdzać nagłówka "Action" na zwracanych odpowiedzi, przypisując symbol wieloznaczny "*" `ReplyAction` właściwości <xref:System.ServiceModel.OperationContractAttribute> . Ponadto wymagane jest posiadanie domyślnej operacji, która ma właściwość "Action" ustawioną na symbol wieloznaczny " \* ". Operacja domyślna odbiera wszystkie komunikaty, których nie można wysłać, i nie ma `DispatchBodyElementAttribute` :  
  
```csharp
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
  
 Przykładowa implementacja usługi jest prosta. Każda metoda zawija odebrany komunikat do komunikatu odpowiedzi i odsyła go z powrotem do klienta.  
  
## <a name="running-and-building-the-sample"></a>Uruchamianie i Tworzenie przykładu  
 Po uruchomieniu przykładu zawartość treści odpowiedzi operacji zostanie wyświetlona w oknie konsoli klienta podobne do następujących (sformatowane) danych wyjściowych.  
  
 Klient wysyła trzy komunikaty do usługi, której treść składa się `bodyA` , `bodyB` i `bodyX` odpowiednio. Jak można wywnioskować na podstawie poprzedniego opisu i podanego kontraktu usługi, komunikat przychodzący do `bodyA` elementu jest wysyłany do `OperationForBodyA()` metody. Ze względu na to, że dla komunikatu z elementem Body nie istnieje jawny cel wysyłania `bodyX` , komunikat jest wysyłany do `DefaultOperation()` . Każda operacja usługi zawija treść otrzymanego komunikatu do elementu specyficznego dla metody i zwraca go, co jest gotowe do skorelowania komunikatów wejściowych i wyjściowych w tym przykładzie:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
