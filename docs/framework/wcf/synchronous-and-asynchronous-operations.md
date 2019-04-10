---
title: Operacje synchroniczne i asynchroniczne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 3d7e44a468388f6d9a8f30d7fea29ec465cd8664
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297710"
---
# <a name="synchronous-and-asynchronous-operations"></a>Operacje synchroniczne i asynchroniczne
W tym temacie omówiono wdrażanie i wywoływanie operacji usługi asynchronicznego.  
  
 Wiele aplikacji asynchroniczne wywoływanie metod, ponieważ umożliwia aplikacji do kontynuowania wykonywania użytecznej pracy podczas wykonywania wywołania metody. Usług Windows Communication Foundation (WCF) i klientów, które mogą uczestniczyć w operacji asynchronicznej wywołań na dwóch różnych poziomach aplikacji, zapewniający jeszcze większą elastyczność w celu zmaksymalizowania wydajności zrównoważone interakcję aplikacji WCF .  
  
## <a name="types-of-asynchronous-operations"></a>Rodzaje operacji asynchronicznych  
 Wszystkie usługi kontraktów w programie WCF, bez względu na to typy parametrów i wartości zwracane, użyj atrybutów usługi WCF do określenia wymiany komunikatów określonej między klientem a usługą. Usługi WCF automatycznie kieruje komunikaty przychodzące i wychodzące operacji odpowiednie usługi lub uruchamianie kodu klienta.  
  
 Klient ma tylko kontraktu usługi, który określa wymiany komunikatów dla określonej operacji. Klienci mogą zaoferować łączność dewelopera model programowania, które postanowili, tak długo, jak zostanie wykryty bazowego wymiany komunikatów. Dlatego, można usług implementowania operacji w jakikolwiek sposób, tak długo, jak zostanie wykryty wzorzec określony komunikat.  
  
 Niezależność od implementacji usługi lub klienta kontraktu usługi umożliwia następujące rodzaje operacji asynchronicznych w aplikacjach usługi WCF:  
  
-   Klientów można wywołać operacji żądania/odpowiedzi asynchronicznie za pomocą wymiany synchronicznego komunikatu.  
  
-   Usługi można zaimplementować operację żądania/odpowiedzi asynchronicznie przy użyciu synchronicznej wiadomości programu exchange.  
  
-   Wymianę komunikatów może być jednokierunkowych, niezależnie od implementacji klienta lub usługi.  
  
### <a name="suggested-asynchronous-scenarios"></a>Scenariusze asynchroniczne z sugerowanych  
 Asynchroniczne metody należy użyć w implementacji operacji usługi, jeśli operacja implementacji usługi sprawia, że wywołania blokowania, takich jak praca operacji We/Wy. Podczas pracy w celu wykonania operacji asynchronicznej, spróbuj wywołać operacji asynchronicznych i metody, aby rozszerzyć ścieżki wywołania asynchronicznego, o ile to możliwe. Na przykład wywołać `BeginOperationTwo()` z poziomu `BeginOperationOne()`.  
  
-   Użyj podejścia asynchroniczne w kliencie lub aplikacja wywołująca w następujących przypadkach:  
  
-   Jeśli są wywoływanie operacji z aplikacji średniego poziomu. (Aby uzyskać więcej informacji na temat takich scenariuszy, zobacz [aplikacje klienckie warstwy środkowej](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   Jeśli są wywoływanie operacji w obrębie strony ASP.NET, należy użyć strony asynchronicznego.  
  
-   Jeśli są wywoływanie operacji z dowolnej aplikacji, która ma jeden wątków, takich jak Windows Forms lub Windows Presentation Foundation (WPF). Korzystając z opartego na zdarzeniach asynchronicznych wywoływania modelu, zdarzenie wynik jest wywoływane w wątku interfejsu użytkownika, dodając czas odpowiedzi do aplikacji bez konieczności obsługi wielu wątków, samodzielnie.  
  
-   Ogólnie rzecz biorąc należy dokonać wyboru między wywołania synchroniczne i asynchroniczne, jeśli wywołania asynchronicznego.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Wdrażanie asynchronicznej operacji usługi  
 Operacje asynchroniczne można zaimplementować przy użyciu jednej z trzech poniższych metod:  
  
1. Wzorca asynchronicznego opartego na zadaniach  
  
2. Asynchroniczny wzorzec oparty na zdarzeniach  
  
3. Wzorzec asynchroniczny IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Wzorzec asynchroniczny oparty na zadanie  
 Wzorca asynchronicznego opartego na zadaniach jest preferowany sposób implementowania asynchronicznych operacji, ponieważ jest najłatwiejszym i najbardziej bardzo proste. Aby użyć tej metody po prostu implementuje operację usługi i określ typu zwracanego zadania\<T >, gdzie T jest typem zwracanym przez operacji logicznej. Na przykład:  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 Operacja SampleMethodTaskAsync zwraca zadanie\<ciągu > ponieważ operacja logiczna zwraca wartość typu ciąg. Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [wzorca asynchronicznego The Task-Based](https://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Korzystając z wzorca asynchronicznego opartego na zadaniach, T:System.AggregateException mogą być generowane, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji. Ten wyjątek może wystąpić na kliencie lub usług  
  
#### <a name="event-based-asynchronous-pattern"></a>Wzorzec asynchroniczny oparty na zdarzeniach  
 Obsługującego wzorzec asynchroniczny oparty na zdarzeniach usługi ma co najmniej jednej operacji o nazwie MethodNameAsync. Te metody mogą dublować synchroniczne wersjach, które do tej samej operacji w bieżącym wątku. Klasa może mieć również zdarzenia MethodNameCompleted i może mieć MethodNameAsyncCancel (lub po prostu CancelAsync) metody. Klient dążące do wywołania operacji będą definiować program obsługi zdarzeń ma być wywoływana po zakończeniu tej operacji  
  
 Poniższy fragment kodu ilustruje sposób deklarowania operacji asynchronicznych z użyciem wzorca asynchronicznego opartego na zdarzeniach.  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zdarzeniach zobacz [wzorca asynchronicznego The Event-Based](https://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Wzorzec asynchroniczny IAsyncResult  
 Operacja usługi może być implementowany w sposób asynchroniczny za pomocą [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronicznego programowania wzorca i oznaczanie `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwością `true`. W takim przypadku operacja asynchroniczna jest uwidaczniany w metadanych, w tym samym formularzu jako operacja synchroniczna: Jest ona uwidoczniona jako jedną operację przy użyciu komunikatu żądania i komunikat odpowiedzi skorelowane. Modele programowania klient następnie dokonać wyboru. Mogą one reprezentować tego wzorca jako operacji synchronicznych lub asynchronicznych, co tak długo, jak podczas wywoływania usługi wymianę komunikatów żądań i odpowiedzi ma miejsce.  
  
 Ogólnie rzecz biorąc za pomocą asynchronicznego charakter tych systemów, możesz nie powinna przyjmować zależności na wątki.  Najbardziej niezawodnym sposobem przekazywanie danych do różnych etapów przetwarzania wysyłania operacji jest korzystanie z rozszerzeń.  
  
 Aby uzyskać przykład, zobacz [jak: Implementowanie asynchronicznej operacji usługi](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 Aby zdefiniować operacji kontraktu `X` asynchronicznie wykonywane niezależnie od tego, jak jest to aplikacja kliencka:  
  
-   Zdefiniowanie dwóch metod przy użyciu wzorca `BeginOperation` i `EndOperation`.  
  
-   `BeginOperation` Metoda zawiera `in` i `ref` parametrów operacji i zwraca <xref:System.IAsyncResult> typu.  
  
-   `EndOperation` Metoda zawiera <xref:System.IAsyncResult> parametru, jak również `out` i `ref` parametrów i zwraca operacje typ zwracany.  
  
 Na przykład zobacz następującą metodę.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Aby utworzyć operację asynchroniczną, będzie dwóch metod:  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationContractAttribute> Atrybut jest stosowany tylko do `BeginDoWork` metody. Kontrakt wynikowy ma jedną operację WSDL o nazwie `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>Wywołania asynchroniczne po stronie klienta  
 Aplikacja klienta WCF można użyć dowolnego z trzy modele wywołania asynchronicznego opisanych powyżej  
  
 Korzystając z modelu opartego na zadaniach, wystarczy wywołać operację, używając słowa kluczowego await, jak pokazano w poniższym fragmencie kodu.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Za pomocą wzorca asynchronicznego opartego na zdarzeniach wymaga tylko dodanie, którego program obsługi zdarzeń, aby otrzymać powiadomienie w odpowiedzi — i wynikowy zdarzenie jest wywoływane w wątku interfejsu użytkownika automatycznie. Aby użyć tej metody, należy określić zarówno **/async** i **/tcv:Version35** opcji za pomocą polecenia [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w następujących przykład.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Po zakończeniu tej operacji Svcutil.exe wygeneruje klasy klienta WCF, za pomocą infrastruktury zdarzeń, który umożliwia aplikacji wywołującej zaimplementować i przypisać program obsługi zdarzeń, odebranie odpowiedzi i podejmij odpowiednie działanie. Aby uzyskać kompletny przykład, zobacz [jak: Asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Oparte na zdarzeniach modelu asynchronicznego, jednak jest dostępna tylko w [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Ponadto nie jest obsługiwana nawet w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] po utworzeniu kanału klienta programu WCF za pomocą <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Za pomocą obiektów kanału klienta WCF, należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do wywołania operacji asynchronicznie. Aby użyć tej metody, należy określić **/async** opcja za pomocą polecenia [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Spowoduje to wygenerowanie kontraktu usługi, w którym każda operacja ma formę `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> właściwością `true` i odpowiadający mu `<End>` metody. Aby uzyskać kompletny przykład za pomocą <xref:System.ServiceModel.ChannelFactory%601>, zobacz [jak: Wywoływanie operacji asynchronicznie za pomocą fabryki kanałów](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 W obu przypadkach aplikacje mogą wywołać operację asynchronicznie, nawet wtedy, gdy usługa jest wdrażana synchronicznie, w taki sam sposób, który aplikacja może użyć tego samego wzorca do wywołania asynchronicznego lokalnego metoda synchroniczna. Jak zaimplementowano operacji nie jest istotny dla klienta; Po odebraniu komunikatu odpowiedzi jego zawartość jest wysyłane do klienta asynchronicznego <`End`> Metoda i klient pobiera informacje.  
  
### <a name="one-way-message-exchange-patterns"></a>Komunikat jednokierunkowy Exchange wzorców  
 Można też utworzyć wymiany komunikatów asynchronicznych, w jakie operacje jednokierunkowe (operacji, dla którego <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> jest `true` nie skorelowany odpowiedź) mogą być wysyłane przez klienta lub usługę niezależnie w dowolnym kierunku Strona. (To za pomocą wymiany komunikatów dwukierunkowego jednokierunkowe komunikaty.) W tym przypadku kontrakt usługi Określa komunikat jednokierunkowy programu exchange, który po obu stronach można zaimplementować jako wywołania asynchronicznego lub implementacji lub nie, zgodnie z potrzebami. Ogólnie rzecz biorąc gdy kontrakt jest wymiany jednokierunkowe komunikaty, implementacje stopniu można asynchronicznego ponieważ po wysłaniu komunikatu aplikacji nie czeka na odpowiedź i można kontynuować inne prace.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Oparte na zdarzeniach asynchronicznych klientów i kontrakty komunikatów  
 Dotyczących projektowania opartego na zdarzeniach modelu asynchronicznego stanu, że jeśli zwracana jest więcej niż jedną wartość, jedną wartość jest zwracana jako `Result` właściwości i inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu. Jeden wynik tego jest to, że jeśli klient importuje metadane przy użyciu opcji oparte na zdarzeniach asynchronicznych polecenia, a operacja zwraca więcej niż jedną wartość, wartość domyślna <xref:System.EventArgs> zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.  
  
 Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mają zwracanych wartości, jak używać właściwości dla tego obiektu **/messageContract** opcja polecenia. Spowoduje to wygenerowanie sygnaturę, która zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikat odpowiedzi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
