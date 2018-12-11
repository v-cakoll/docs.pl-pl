---
title: Wysyłanie według elementu treści
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 58d505770a495e5e423104b9fb912d088ca56f86
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143162"
---
# <a name="dispatch-by-body-element"></a>Wysyłanie według elementu treści
Ten przykład demonstruje sposób implementacji alternatywnego algorytmu do przypisywania komunikatów przychodzących do operacji.  
  
 Domyślnie dyspozytora modelu usługi wybierze metodę obsługi odpowiednie dla wiadomości przychodzących, w oparciu o wiadomości WS-Addressing "Action" nagłówek lub równoważnych informacji w żądaniu HTTP SOAP.  
  
 Niektóre SOAP 1.1 Web services stosów, które nie podlegają WS-I Basic Profile 1.1 wytycznych, nie wysyła komunikaty w oparciu o identyfikator URI akcji, ale raczej oparty na nazwy kwalifikowanej XML pierwszego elementu w treści protokołu SOAP. Podobnie po stronie klienta, te stosów może wysyłać komunikatów za pomocą pustego lub dowolnego HTTP SoapAction nagłówka, który był dozwolony przez specyfikację SOAP 1.1.  
  
 Aby zmienić sposób komunikaty są wysyłane do metod, implementuje próbki <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejs rozszerzalności `DispatchByBodyElementOperationSelector`. Ta klasa wybiera operacje oparte na pierwszy element w treści wiadomości.  
  
 Konstruktor klasy oczekuje słownik wypełniane przy użyciu pary `XmlQualifiedName` i ciągi znaków, według której kwalifikowanych nazw wskazuje nazwę pierwszego elementu podrzędnego w treści protokołu SOAP i ciągi wskazują pasujące nazwy operacji. `defaultOperationName` Jest nazwą operacji, która odbiera wszystkie komunikaty, które nie mogą być dopasowywane do tego słownika:  
  
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
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementacje są bardzo proste tworzenie, ponieważ istnieje tylko jedna metoda w interfejsie: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>. Zadania tej metody jest sprawdzanie wiadomości przychodzących i zwraca ciąg, która jest równa nazwę metody w kontrakcie usługi na bieżący punkt końcowy.  
  
 W tym przykładzie pobiera selektor operacji <xref:System.Xml.XmlDictionaryReader> komunikatu przychodzącego treści za pomocą <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Ta metoda już umieszcza czytelnika na pierwszy element podrzędny w treści wiadomości, tak, aby wystarczające, aby uzyskać nazwę bieżącego elementu i identyfikator URI przestrzeni nazw, a także połączyć je w `XmlQualifiedName` następnie używany do wyszukiwania odpowiednich operacji Słownik utrzymywane przez selektor operacji.  
  
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
  
 Dostęp do treści wiadomości z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lub dowolnej z metod, które zapewniają dostęp do zawartości w treści komunikatu powoduje, że komunikat, który ma zostać oznaczony jako "przeczytane", co oznacza, że wiadomość jest nieprawidłowy w przypadku dalszego przetwarzania. W związku z tym selektor operacji tworzy kopię wiadomości przychodzących za pomocą metody pokazano w poniższym kodzie. Ponieważ pozycja czytnik nie został zmieniony podczas inspekcji, mogą być przywoływane przez nowo utworzony komunikat do której właściwości wiadomości i nagłówki komunikatów także są kopiowane, co skutkuje dokładną oryginalnego komunikatu:  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a>Dodawanie selektor operacji usługi  
 Selektory operacji wysyłania usługi są rozszerzeniami do dyspozytora Windows Communication Foundation (WCF). Wybierania metody na kanał wywołania zwrotnego kontrakty dwukierunkowe, są również selektorów operacji klienta, co sprawdza się w dużej mierze jak selektory operacji wysyłania opisane w tym miejscu, ale które nie są jawnie wymienione w tym przykładzie.  
  
 Podobnie jak większość rozszerzeń modelu usługi selektory operacji wysyłania są dodawane do dyspozytora za pomocą zachowań. A *zachowanie* jest obiekt konfiguracji, który dodaje jedno lub więcej rozszerzeń środowiska uruchomieniowego wysyłania (lub środowiska uruchomieniowego klienta) lub w przeciwnym razie zmiany jej ustawień.  
  
 Ponieważ selektory operacji mają zakres kontraktu, jest odpowiednie zachowanie, aby zaimplementować tutaj <xref:System.ServiceModel.Description.IContractBehavior>. Ponieważ interfejs jest implementowany w <xref:System.Attribute> klasy pochodnej jak pokazano w poniższym kodzie, zachowanie może deklaratywne dodane do wszelkich kontraktu usługi. Zawsze, gdy <xref:System.ServiceModel.ServiceHost> jest otwarty i środowiska uruchomieniowego wysyłania jest wbudowany, wszystkie zachowania znaleziono jako atrybuty kontrakty, operacji i implementacji usługi lub jako element w konfiguracji usługi są automatycznie dodawane, a następnie poproszony o Współtworzenie rozszerzenia lub zmodyfikować domyślną konfigurację.  
  
 Celu skrócenia programu, poniższy fragment kodu przedstawia tylko implementacji metody <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, która ma wpływ zmian w konfiguracji dyspozytora w tym przykładzie. Inne metody nie są wyświetlane, ponieważ powrócą do wywołującego bez wykonywania pracy.  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Po pierwsze, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementacja ustawia słownik wyszukiwania selektor operacji przez Iterowanie po <xref:System.ServiceModel.Description.OperationDescription> elementów w punkcie końcowym usługi <xref:System.ServiceModel.Description.ContractDescription>. Następnie każdy opis operacji jest sprawdzane pod kątem obecności `DispatchBodyElementAttribute` zachowanie, implementacja <xref:System.ServiceModel.Description.IOperationBehavior> również zdefiniowanego w tym przykładzie. Ta klasa jest również zachowanie, jest w stanie pasywnym i nie wpływa aktywnie zmiany konfiguracji do środowiska uruchomieniowego wysyłania. Zwróć wszystkie jego metody do obiektu wywołującego bez żadnych akcji. Zachowanie operacji istnieje tylko dlatego, że metadane wymagane dla nowego wysyłania mechanizmu, a mianowicie kwalifikowana nazwa elementu body w których wystąpienie operacji jest zaznaczone, może być skojarzony z odpowiednich operacji.  
  
 Jeśli zostanie znaleziony takie zachowanie, parę wartości utworzone na podstawie nazwy kwalifikowanej XML (`QName` właściwości) i nazwa operacji (`Name` właściwość) zostanie dodany do słownika.  
  
 Po słowniku zapełnieniu nowej `DispatchByBodyElementOperationSelector` jest skonstruowany przy użyciu tych informacji i Ustaw jako selektor operacji wysyłania środowiska uruchomieniowego:  
  
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
 Zachowanie zaimplementowane w tym przykładzie bezpośrednio wpływa na sposób komunikaty z sieci są interpretowane i wysyłane, które są funkcjami kontraktu usługi. W związku z tym zachowanie powinny zostać zadeklarowane na poziomie kontraktu usługi w celu wykonania usługi, który zdecydował się go użyć.  
  
 Stosuje usługa projekt przykładowy `DispatchByBodyElementBehaviorAttribute` umowę zachowania do `IDispatchedByBody` umowy oraz etykiety dla tych dwóch operacji `OperationForBodyA()` i `OperationForBodyB()` z `DispatchBodyElementAttribute` zachowanie operacji. Po otwarciu usługi hosta dla usługi, który implementuje ten kontrakt metadanych jest pobierana przez konstruktora dyspozytora w sposób opisany wcześniej.  
  
 Selektor operacji wywołuje wyłącznie zależnie od elementu treści komunikatu i ignoruje "Action", dlatego jest wymagany stwierdzić, środowisko uruchomieniowe nie Sprawdź nagłówek "Action" w odpowiedzi zwrócony, przypisując symbol wieloznaczny "*" Aby `ReplyAction` właściwość <xref:System.ServiceModel.OperationContractAttribute>. Ponadto jest wymagane do operacji domyślnej, która ma właściwość "Action" do symbolu wieloznacznego "\*". Operacja domyślne odbiera wszystkie komunikaty, które nie mogą być wysyłane i nie ma `DispatchBodyElementAttribute`:  
  
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
  
 Przykładowe zastosowanie usługi jest bardzo proste. EVERY — metoda opakowuje odebranego komunikatu do komunikatu odpowiedzi i zwraca go do klienta.  
  
## <a name="running-and-building-the-sample"></a>Uruchamianie i budowanie przykładu  
 Po uruchomieniu przykładu, treść odpowiedzi operacji są wyświetlane w oknie konsoli klienta podobne do następujących danych wyjściowych (sformatowanych).  
  
 Klient wysyła wiadomości do usługi której ciała treści, nazwie elementu `bodyA`, `bodyB`, i `bodyX`, odpowiednio. Ponieważ może zostać odroczony z poprzednich opis i kontrakt usługi pokazano, przychodzącego komunikatu o `bodyA` element jest wysyłane do `OperationForBodyA()` metody. Ponieważ nie istnieje żadne miejsce docelowe nie jawnego wysłania komunikatu z `bodyX` elementu body komunikat jest wysyłany do `DefaultOperation()`. Każdej operacji usługi opakowuje treści odebranego komunikatu do określonej metody element i zwraca wartość, która jest przeprowadzane w celu skorelowania danych wejściowych i wyjściowych komunikatów wyraźnie dla tego przykładu:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a>Zobacz też
