---
title: Wysyłanie według elementu treści
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183713"
---
# <a name="dispatch-by-body-element"></a>Wysyłanie według elementu treści
W tym przykładzie pokazano, jak zaimplementować alternatywny algorytm przypisywania wiadomości przychodzących do operacji.  
  
 Domyślnie dyspozytor modelu usługi wybiera odpowiednią metodę obsługi wiadomości przychodzącej na podstawie nagłówka "Akcja" adresowania WS wiadomości lub równoważnych informacji w żądaniu PROTOKOŁU HTTP SOAP.  
  
 Niektóre stosy usług sieci Web protokołu SOAP 1.1, które nie są zgodne z wytycznymi WS-I Basic Profile 1.1, nie wysyłają komunikatów opartych na identyfikatorze URI akcji, ale raczej na podstawie kwalifikowanej nazwy XML pierwszego elementu wewnątrz treści PROTOKOŁU SOAP. Podobnie po stronie klienta tych stosów może wysyłać wiadomości z pustym lub dowolnego nagłówka HTTP SoapAction, co było dozwolone przez protokół SOAP 1.1 specyfikacji.  
  
 Aby zmienić sposób wysyłania wiadomości do metod, <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> w przykładzie `DispatchByBodyElementOperationSelector`implementuje interfejs rozszerzalności w programie . Ta klasa wybiera operacje na podstawie pierwszego elementu treści wiadomości.  
  
 Konstruktor klasy oczekuje słownika wypełnione `XmlQualifiedName` parami i ciągami, przy czym nazwy kwalifikowane wskazują nazwę pierwszego rodu podrzędnego treści SOAP, a ciągi wskazują pasującą nazwę operacji. Jest `defaultOperationName` to nazwa operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowane do tego słownika:  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementacje są bardzo proste do zbudowania, ponieważ <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>istnieje tylko jedna metoda na interfejsie: . Zadaniem tej metody jest sprawdzenie wiadomości przychodzącej i zwrócenie ciągu, który jest równy nazwie metody w umowie serwisowej dla bieżącego punktu końcowego.  
  
 W tym przykładzie selektor operacji <xref:System.Xml.XmlDictionaryReader> uzyskuje dla treści wiadomości <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>przychodzącej przy użyciu . Ta metoda już umieszcza czytnik na pierwszym elemencie treści wiadomości, dzięki czemu jest wystarczająca, aby uzyskać nazwę `XmlQualifiedName` bieżącego elementu i identyfikator URI obszaru nazw i połączyć je w, który jest następnie używany do wyszukania odpowiedniej operacji ze słownika przechowywanego przez selektor operacji.  
  
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
  
 Uzyskiwanie dostępu do <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> treści wiadomości za pomocą lub dowolnej innej metody, które zapewniają dostęp do zawartości treści wiadomości powoduje, że wiadomość jest oznaczona jako "odczyt", co oznacza, że wiadomość jest nieprawidłowa do dalszego przetwarzania. W związku z tym selektor operacji tworzy kopię wiadomości przychodzącej z metodą pokazaną w poniższym kodzie. Ponieważ pozycja czytelnika nie została zmieniona podczas inspekcji, może się do niego odwoływać nowo utworzona wiadomość, do której są również kopiowane właściwości wiadomości i nagłówki wiadomości, co skutkuje dokładnym klonem oryginalnej wiadomości:  
  
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
 Selektory operacji wysyłki usługi są rozszerzeniami dyspozytora Windows Communication Foundation (WCF). W celu wybrania metod w kanale wywołania zwrotnego kontraktów dupleksu istnieją również selektory operacji klienta, które działają bardzo podobnie do selektorów operacji wysyłki opisanych w tym miejscu, ale które nie są wyraźnie uwzględnione w tym przykładzie.  
  
 Podobnie jak większość rozszerzeń modelu usługi, selektory operacji wysyłki są dodawane do dyspozytora przy użyciu zachowań. *Zachowanie* jest obiekt konfiguracji, który dodaje jedno lub więcej rozszerzeń do środowiska wykonawczego wysyłki (lub do środowiska wykonawczego klienta) lub w inny sposób zmienia jego ustawienia.  
  
 Ponieważ selektory operacji mają zakres kontraktu, odpowiednie <xref:System.ServiceModel.Description.IContractBehavior>zachowanie do zaimplementowania w tym miejscu jest . Ponieważ interfejs jest implementowany <xref:System.Attribute> w klasie pochodnej, jak pokazano w poniższym kodzie, zachowanie może być deklaratywnie dodane do każdej umowy serwisowej. Za każdym <xref:System.ServiceModel.ServiceHost> razem, gdy a jest otwarty i środowisko uruchomieniowe wysyłki jest zbudowany, wszystkie zachowania znalezione jako atrybuty w kontraktach, operacji i implementacji usługi lub jako element w konfiguracji usługi są automatycznie dodawane, a następnie proszone o współtworzenie rozszerzeń lub zmodyfikować domyślną konfigurację.  
  
 Dla zwięzłości poniższy fragment kodu <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>pokazuje tylko implementację metody , która wpływa na zmiany konfiguracji dla dyspozytora w tym przykładzie. Inne metody nie są wyświetlane, ponieważ powrót do obiektu wywołującego bez wykonywania jakiejkolwiek pracy.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Po pierwsze <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementacja konfiguruje słownik wyszukiwania dla selektora operacji <xref:System.ServiceModel.Description.OperationDescription> przez iterację nad <xref:System.ServiceModel.Description.ContractDescription>elementami w punkcie końcowym usługi . Następnie każdy opis operacji jest sprawdzany `DispatchBodyElementAttribute` pod kątem obecności <xref:System.ServiceModel.Description.IOperationBehavior> zachowania, implementacja, która jest również zdefiniowana w tym przykładzie. Chociaż ta klasa jest również zachowanie, jest pasywny i nie aktywnie przyczyniają się do żadnych zmian konfiguracji do środowiska wykonawczego wysyłki. Wszystkie jego metody powrócić do wywołującego bez podejmowania żadnych działań. Zachowanie operacji istnieje tylko tak, że metadane wymagane dla nowego mechanizmu wysyłki, a mianowicie kwalifikowana nazwa elementu treści, na którego wystąpienie jest zaznaczona operacja, mogą być skojarzone z odpowiednich operacji.  
  
 Jeśli takie zachowanie zostanie znalezione, do słownika zostanie`QName` dodana para wartości`Name` utworzona na podstawie kwalifikowanej nazwy XML (właściwości) i nazwy operacji ( właściwości).  
  
 Po wypełnieniu słownika, `DispatchByBodyElementOperationSelector` nowy jest konstruowany z tymi informacjami i ustawiony jako selektor operacji środowiska wykonawczego wysyłki:  
  
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
  
## <a name="implementing-the-service"></a>Wdrażanie usługi  
 Zachowanie zaimplementowane w tym przykładzie bezpośrednio wpływa na sposób interpretowania i wysyłania wiadomości z przewodu, co jest funkcją umowy serwisowej. W związku z tym zachowanie powinno być zadeklarowane na poziomie umowy serwisowej w dowolnej implementacji usługi, która zdecyduje się go używać.  
  
 Przykładowa usługa projektu `DispatchByBodyElementBehaviorAttribute` stosuje zachowanie `IDispatchedByBody` kontraktu do umowy serwisowej `OperationForBodyA()` `OperationForBodyB()` i `DispatchBodyElementAttribute` etykietuje każdą z dwóch operacji i z zachowaniem operacji. Po otwarciu hosta usługi dla usługi implementacji tej umowy, metadane są pobierane przez konstruktora dyspozytora, jak opisano wcześniej.  
  
 Ponieważ selektor operacji wywołuje wyłącznie na podstawie elementu treści wiadomości i ignoruje "Akcję", należy poinformować środowisko wykonawcze, aby nie sprawdzał nagłówka "Akcja" w `ReplyAction` zwróconych odpowiedziach, przypisując symbol wieloznaczny "*" do właściwości <xref:System.ServiceModel.OperationContractAttribute>. Ponadto wymagane jest, aby mieć domyślną operację, która ma "Action"\*właściwość ustawiona na symbol wieloznaczny " ". Domyślna operacja odbiera wszystkie komunikaty, których nie `DispatchBodyElementAttribute`można wysłać i nie ma:  
  
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
  
 Implementacja przykładowej usługi jest prosta. Każda metoda zawija odebraną wiadomość do wiadomości odpowiedzi i powtarza ją z powrotem do klienta.  
  
## <a name="running-and-building-the-sample"></a>Uruchamianie i tworzenie próbki  
 Po uruchomieniu próbki zawartość treści odpowiedzi operacji są wyświetlane w oknie konsoli klienta podobne do następujących (sformatowany) dane wyjściowe.  
  
 Klient wysyła trzy komunikaty do usługi, `bodyA`której `bodyB`element `bodyX`zawartości treści jest nazwany , i , odpowiednio. Jak można odroczyć z poprzedniego opisu i umowy serwisowej pokazano, przychodzące wiadomości z elementem `bodyA` jest wywoływana do `OperationForBodyA()` metody. Ponieważ nie ma jawnego obiektu docelowego wysyłki dla wiadomości z `bodyX` `DefaultOperation()`elementem treści, wiadomość jest wysyłana do . Każda z operacji usługi zawija treść odebranej wiadomości do elementu specyficznego dla metody i zwraca go, co odbywa się w celu wyraźnego skorelowania komunikatów wejściowych i wyjściowych dla tego przykładu:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
