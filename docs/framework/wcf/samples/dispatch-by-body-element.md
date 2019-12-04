---
title: Wysyłanie według elementu treści
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 307d6bbbab118392ef079942eae367a4c6792c22
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712030"
---
# <a name="dispatch-by-body-element"></a>Wysyłanie według elementu treści
Ten przykład pokazuje, jak zaimplementować alternatywny algorytm przypisywania komunikatów przychodzących do operacji.  
  
 Domyślnie Dyspozytor modelu usług wybiera odpowiednią metodę obsługi dla komunikatu przychodzącego na podstawie nagłówka "Akcja" WS-Addressing "lub równoważne informacje w żądaniu protokołu HTTP SOAP.  
  
 Niektóre stosy usług sieci Web SOAP 1,1, które nie są zgodne z wytycznymi dotyczącymi profilu WS-I Basic 1,1 nie wysyłają komunikatów na podstawie identyfikatora URI akcji, ale raczej na podstawie kwalifikowanej nazwy XML pierwszego elementu wewnątrz treści protokołu SOAP. Podobnie po stronie klienta te stosy mogą wysyłać komunikaty z pustym lub dowolnym nagłówkiem HTTP SoapAction, który był dozwolony przez specyfikację protokołu SOAP 1,1.  
  
 Aby zmienić sposób wysyłania komunikatów do metod, przykład implementuje interfejs rozszerzalności <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na `DispatchByBodyElementOperationSelector`. Ta klasa wybiera operacje na podstawie pierwszego elementu treści komunikatu.  
  
 Konstruktor klasy oczekuje słownika wypełnionego parami `XmlQualifiedName` i ciągów, według których kwalifikowane nazwy wskazują nazwę pierwszego elementu podrzędnego treści protokołu SOAP, a ciągi wskazują pasującą nazwę operacji. `defaultOperationName` to nazwa operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowane do tego słownika:  
  
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
  
 implementacje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> są bardzo proste dla kompilacji, ponieważ istnieje tylko jedna metoda w interfejsie: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Zadaniem tej metody jest zbadanie komunikatu przychodzącego i zwrócenie ciągu, który jest równy nazwie metody w kontrakcie usługi dla bieżącego punktu końcowego.  
  
 W tym przykładzie selektor operacji uzyskuje <xref:System.Xml.XmlDictionaryReader> treści wiadomości przychodzącej przy użyciu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Ta metoda już umieszcza czytnik w pierwszym elemencie podrzędnym treści wiadomości, dzięki czemu można uzyskać nazwę bieżącego elementu i identyfikator URI przestrzeni nazw, a następnie połączyć je w `XmlQualifiedName`, które są następnie używane do wyszukiwania odpowiedniej operacji ze słownika przechowywanego przez selektor operacji.  
  
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
  
 Uzyskiwanie dostępu do treści wiadomości za pomocą <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lub dowolnej z innych metod zapewniających dostęp do zawartości treści wiadomości powoduje, że komunikat zostanie oznaczony jako "read" (odczyt), co oznacza, że komunikat jest nieprawidłowy do dalszej obróbki. W związku z tym selektor operacji tworzy kopię komunikatu przychodzącego za pomocą metody pokazanej w poniższym kodzie. Ponieważ pozycja czytnika nie została zmieniona podczas inspekcji, może odwoływać się do nowo utworzonego komunikatu, do którego są również kopiowane właściwości wiadomości i nagłówki wiadomości, co powoduje dokładne klonowanie oryginalnej wiadomości:  
  
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
  
 Ponieważ selektory operacji mają zakres kontraktu, odpowiednie zachowanie w celu zaimplementowania jest <xref:System.ServiceModel.Description.IContractBehavior>. Ponieważ interfejs jest zaimplementowany na <xref:System.Attribute> klasie pochodnej, jak pokazano w poniższym kodzie, zachowanie można deklaratywnie dodać do dowolnego kontraktu usługi. Za każdym razem, gdy <xref:System.ServiceModel.ServiceHost> jest otwarty, a środowisko uruchomieniowe wysyłania zostało skompilowane, wszystkie zachowania, które znajdują się w ramach kontraktów, operacji i implementacji usług lub jako element w konfiguracji usługi są automatycznie dodawane, a następnie proszeni do współtworzenia rozszerzeń lub modyfikowania konfiguracji domyślnej.  
  
 W przypadku zwięzłości Poniższy fragment kodu zawiera tylko implementację metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, co wpływa na zmiany konfiguracji dyspozytora w tym przykładzie. Inne metody nie są wyświetlane, ponieważ zwracają do obiektu wywołującego bez wykonywania żadnej pracy.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Najpierw implementacja <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> ustawia słownik wyszukiwania dla selektora operacji poprzez iterację elementów <xref:System.ServiceModel.Description.OperationDescription> w <xref:System.ServiceModel.Description.ContractDescription>punktu końcowego usługi. Następnie każdy opis operacji jest sprawdzany pod kątem obecności `DispatchBodyElementAttribute`, implementacja <xref:System.ServiceModel.Description.IOperationBehavior>, która jest również zdefiniowana w tym przykładzie. Chociaż ta klasa jest również zachowaniem, jest pasywna i nie wprowadza żadnych zmian w konfiguracji w czasie wykonywania wysyłania. Wszystkie jego metody zwracają do obiektu wywołującego bez podejmowania żadnych działań. Zachowanie tej operacji istnieje tylko wtedy, gdy metadane wymagane dla nowego mechanizmu wysyłania, czyli kwalifikowana nazwa elementu treści, dla którego wystąpienie operacji jest zaznaczone, mogą być skojarzone z odpowiednimi operacjami.  
  
 Jeśli takie zachowanie zostanie znalezione, para wartości utworzona na podstawie kwalifikowanej nazwy XML (Właściwość`QName`) i nazwy operacji (Właściwość`Name`) zostanie dodana do słownika.  
  
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
  
 Przykładowa usługa projektu stosuje zachowanie `DispatchByBodyElementBehaviorAttribute` umowy do kontraktu usługi `IDispatchedByBody` i etykiety każdej z dwóch operacji `OperationForBodyA()` i `OperationForBodyB()` z zachowaniem `DispatchBodyElementAttribute` operacji. W przypadku otwarcia hosta usługi dla usługi implementującej ten kontrakt te metadane są pobierane przez konstruktora dyspozytora zgodnie z wcześniejszym opisem.  
  
 Ponieważ selektor operacji jest wysyłany wyłącznie na podstawie treści wiadomości i ignoruje "działanie", jest wymagane, aby poinformować środowisko uruchomieniowe, aby nie sprawdzać nagłówka "Action" na zwracanych odpowiedzi, przypisując symbol wieloznaczny "*" do właściwości `ReplyAction` <xref:System.ServiceModel.OperationContractAttribute>. Ponadto wymagane jest posiadanie domyślnej operacji, która ma właściwość "Action" ustawioną na symbol wieloznaczny "\*". Operacja domyślna odbiera wszystkie komunikaty, których nie można wysłać, i nie ma `DispatchBodyElementAttribute`:  
  
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
  
 Klient wysyła trzy komunikaty do usługi, której treść składa się o nazwie `bodyA`, odpowiednio `bodyB`i `bodyX`. Jak można wywnioskować na podstawie poprzedniego opisu i podanej umowy dotyczącej usługi, komunikat przychodzący z elementem `bodyA` jest wysyłany do metody `OperationForBodyA()`. Ze względu na to, że dla komunikatu z `bodyX` treści nie istnieje jawny cel wysyłania wiadomości, komunikat jest wysyłany do `DefaultOperation()`. Każda operacja usługi zawija treść otrzymanego komunikatu do elementu specyficznego dla metody i zwraca go, co jest gotowe do skorelowania komunikatów wejściowych i wyjściowych w tym przykładzie:  
  
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
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
