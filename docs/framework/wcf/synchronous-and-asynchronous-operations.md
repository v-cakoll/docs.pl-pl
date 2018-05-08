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
ms.openlocfilehash: 0b64d45797babff2da1649fb7469684342e65d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="synchronous-and-asynchronous-operations"></a>Operacje synchroniczne i asynchroniczne
W tym temacie omówiono Implementowanie i wywoływanie operacji usługi asynchronicznego.  
  
 Wiele aplikacji asynchroniczne wywoływanie metody, ponieważ umożliwia to aplikacji kontynuować pracy przydatne podczas wywołania metody. Usług Windows Communication Foundation (WCF) i klienci mogą uczestniczyć w wywołaniach operację asynchroniczną na dwóch różnych poziomach aplikacji, które zawierają [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji zrównoważone nawet większą elastyczność i możliwość zmaksymalizować przepustowość interakcji.  
  
## <a name="types-of-asynchronous-operations"></a>Typy operacji asynchronicznych  
 Wszystkie usługi umów [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bez względu na typy parametrów i wartości zwracane, użyj [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] atrybutów, aby określić konkretnego wymiany komunikatów między klientem a usługą. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatycznie kieruje komunikaty przychodzące i wychodzące z operacją odpowiednią usługę lub wykonywanie kodu klienta.  
  
 Klient ma tylko kontraktu usługi, która określa wymiany komunikatów dla określonej operacji. Klienci zaoferować dewelopera dowolnego modelu programowania, które decydują, tak długo, jak zaobserwowano podstawowej wymiany komunikatów. Tak zbyt, usługi zaimplementować operacji w jakikolwiek sposób tak długo, jak zaobserwowano wzorzec określonego komunikatu.  
  
 Niezależność od usługi umowy z dowolnej usługi lub klienta implementacja zapewnia następujące rodzaje operacji asynchronicznych w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji:  
  
-   Klienci mogą wywoływać operacje żądania/odpowiedzi asynchronicznie za pomocą exchange komunikatu synchronicznego.  
  
-   Usługi można zaimplementować operacji żądania/odpowiedzi, asynchronicznie za pomocą exchange komunikatu synchronicznego.  
  
-   Wymiany komunikatów może być jednokierunkowe, niezależnie od implementacji klienta lub usługi.  
  
### <a name="suggested-asynchronous-scenarios"></a>Sugerowana scenariusze asynchroniczne  
 Asynchroniczne metody należy użyć w implementacji operacji usługi, jeśli operacja implementacji usługi nawiązuje połączenie blokujące, takie jak podczas pracy we/wy. Podczas pracy w celu wykonania operacji asynchronicznej, spróbuj wywołanie operacji asynchronicznych i metody umożliwiające rozszerzenie ścieżki wywołania asynchronicznego, o ile to możliwe. Na przykład wywołać `BeginOperationTwo()` z poziomu `BeginOperationOne()`.  
  
-   Przy użyciu asynchronicznej metody na kliencie lub aplikacja wywołująca w następujących przypadkach:  
  
-   Jeśli są wywoływanie operacji aplikacji warstwy środkowej. (Aby uzyskać więcej informacji na temat takich scenariuszy, zobacz [aplikacje klienckie warstwy środkowej](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   Jeśli są wywoływania operacji strony ASP.NET, użyj stron asynchronicznego.  
  
-   Jeśli są wywoływanie operacji z poziomu dowolnej aplikacji, która jest pojedynczym wątku, takie jak formularze systemu Windows lub Windows Presentation Foundation (WPF). Korzystając z oparty na zdarzeniach asynchroniczne wywołanie modelu, zdarzenie wynik jest wywoływane w wątku interfejsu użytkownika, dodawanie czas odpowiedzi aplikacji bez konieczności się obsługiwać wiele wątków.  
  
-   Ogólnie rzecz biorąc Jeśli masz wybór między wywołania synchroniczne i asynchroniczne, wybierz wywołania asynchronicznego.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Wdrażanie asynchronicznej operacji usługi  
 Operacje asynchroniczne może być zaimplementowany przez przy użyciu jednej z trzech następujących metod:  
  
1.  Asynchroniczny wzorzec oparty na zadaniach  
  
2.  Asynchroniczny wzorzec oparty na zdarzeniach  
  
3.  Asynchroniczny wzorzec IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Wzorzec asynchroniczny oparty na zadaniach  
 Asynchroniczny wzorzec oparty na zadaniach jest preferowany sposób implementowania operacji asynchronicznych, ponieważ jest najprostsza i większość bezpośrednio do przodu. Aby użyć tej metody po prostu implementuje operację usługi i określić zwracanego typu zadania\<T >, gdzie T jest typem zwracanym przez operacji logicznej. Na przykład:  
  
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
  
 Operacja SampleMethodTaskAsync zwraca zadanie\<ciągu >, ponieważ operacja logiczna zwraca wartość typu ciąg. Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [wzorca asynchronicznego The Task-Based](http://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Podczas korzystania z wzorca asynchronicznego opartego na zadaniach, T:System.AggregateException może zostać zgłoszony, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji. Ten wyjątek może wystąpić na kliencie lub usług  
  
#### <a name="event-based-asynchronous-pattern"></a>Wzorzec asynchroniczny oparty na zdarzeniach  
 Obsługującego wzorzec asynchroniczny oparty na zdarzeniach usługi ma co najmniej jedną operację o nazwie MethodNameAsync. Te metody mogą duplikatów synchroniczne wersje, które do tej samej operacji w bieżącym wątku. Klasa może być również zdarzeń MethodNameCompleted i może mieć MethodNameAsyncCancel (lub po prostu CancelAsync) metody. Klient chcą wywołaj operację określi program obsługi zdarzeń ma być wywoływana po zakończeniu operacji  
  
 Poniższy fragment kodu ilustruje sposób zadeklarować operacji asynchronicznych za pomocą wzorca asynchronicznego opartego na zdarzeniach.  
  
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
  
 Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zdarzeniach, zobacz [wzorca asynchronicznego The Event-Based](http://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Wzorzec projektowy IAsyncResult  
 Operacja usługi może być wdrożonych w sposób asynchroniczny przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programowania wzorca asynchronicznego i oznaczenie `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> ustawioną właściwość `true`. W takim przypadku operacja asynchroniczna jest widoczna w metadanych, w tym samym formularzu jako operacja synchroniczna: jest uwidaczniany jako jedna operacja z komunikatu żądania i komunikat odpowiedzi skorelowane. Modele programowania klient następnie mają wybór. Reprezentują tego wzorca jako operacja synchroniczna lub asynchroniczne jedna tak długo, jak długo po wywołaniu usługi wymiany komunikatów żądań i odpowiedzi ma miejsce.  
  
 Ogólnie rzecz biorąc z asynchronicznego charakter systemów, możesz nie powinna przyjmować zależności na wątki.  Najbardziej niezawodnym sposobem przekazywanie danych do różnych etapów przetwarzania wysyłania operacji jest używanie rozszerzeń.  
  
 Na przykład zobacz [porady: Implementowanie asynchronicznej operacji usługi](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 Aby zdefiniować operacja kontraktu `X` asynchronicznie wykonywane niezależnie od tego, jak jest to aplikacja klienta:  
  
-   Zdefiniuj dwie metody przy użyciu wzorca `BeginOperation` i `EndOperation`.  
  
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
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationContractAttribute> Atrybut jest stosowany tylko do `BeginDoWork` metody. Wynikowa kontraktu ma jedną operację WSDL o nazwie `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>Asynchroniczne wywołania po stronie klienta  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta aplikacji można użyć dowolnego z trzy modele wywołanie asynchroniczne opisanych powyżej  
  
 Gdy używany jest model oparty na zadaniach, po prostu wywołaj operację przy użyciu — słowo kluczowe await, jak pokazano w poniższy fragment kodu.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Za pomocą wzorca asynchronicznego opartego na zdarzeniach wymaga tylko dodanie przez program obsługi zdarzeń, aby otrzymać powiadomienie o odpowiedź--i wynikowy zdarzenie jest wywoływane w wątku interfejsu użytkownika automatycznie. Aby użyć tej metody, należy określić zarówno **/async** i **/tcv:Version35** polecenie Opcje z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykład.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Po zakończeniu Svcutil.exe generuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klasy klienta przy użyciu infrastruktury zdarzeń, który umożliwia wywołanie aplikacji do wdrożenia i przypisać program obsługi zdarzeń do odbierania odpowiedzi i podejmij odpowiednie działanie. Pełny przykład, zobacz [porady: wywołania operacji usługi asynchronicznie](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Oparty na zdarzeniach modelu asynchroniczne, jednak jest dostępna tylko w [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Ponadto nie jest obsługiwane nawet w [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] podczas [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanału klienta jest tworzona przy użyciu <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiekty kanału klienta, należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do asynchronicznego wywołania operacji. Aby użyć tej metody, podaj **/async** polecenia opcji [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Spowoduje to wygenerowanie kontraktu usługi, w której każda operacja ma formę `<Begin>` metody z <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> ustawioną właściwość `true` i odpowiadające mu `<End>` — metoda. Aby uzyskać pełny przykład za pomocą <xref:System.ServiceModel.ChannelFactory%601>, zobacz [jak: wywołanie operacji asynchronicznie przy użyciu fabryki kanałów](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 W obu przypadkach aplikacji można wywołać operacji asynchronicznie, nawet wtedy, gdy usługa jest wdrażana synchronicznie, w taki sam sposób, że aplikacja może użyć tego samego wzorca do asynchronicznego wywołania lokalnego metoda synchroniczna. Implementowania operacji nie jest znacząca klientowi; Po odebraniu wiadomości odpowiedzi, jego zawartość jest wysyłane do klienta asynchroniczne <`End`> Metoda i klient pobiera informacje.  
  
### <a name="one-way-message-exchange-patterns"></a>Komunikat jednokierunkowy wzorce programu Exchange  
 Asynchroniczne wymiany komunikatów można też utworzyć, w których operacji jednokierunkowych (operacje, dla którego <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> jest `true` mieć żadnej odpowiedzi skorelowane) mogą być wysyłane przez klienta lub usługę, niezależnie od drugiego w żadnym kierunku Strona. (Używa dupleksu wymiany komunikatów o jednokierunkowe komunikaty.) W takim przypadku kontrakt usługi Określa komunikat jednokierunkowy programu exchange, które można wdrożyć obok jako wywołania asynchroniczne lub implementacje lub nie, zależnie od potrzeb. Ogólnie rzecz biorąc gdy kontrakt jest wymiany jednokierunkowe komunikaty, implementacje przede wszystkim można asynchronicznego, ponieważ po wysłaniu komunikatu aplikacji bez oczekiwania na odpowiedź i można kontynuować wykonywania innych zadań.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Oparty na zdarzeniach asynchroniczne klientów i kontrakty komunikatów  
 Wskazówek dotyczących modelu asynchroniczny oparty na zdarzeniach stanu, że jeśli zostanie zwrócony więcej niż jedną wartość, jedna wartość jest zwracana jako `Result` właściwości, a inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu. Jeden wynik tego jest to, że jeśli klient importuje metadanych za pomocą opcji polecenia asynchroniczny oparty na zdarzeniach i operacji zwraca więcej niż jedną wartość, domyślna <xref:System.EventArgs> obiektu zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.  
  
 Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mieć zwracanych wartości jako właściwości tego obiektu, użyj **/messageContract** — opcja polecenia. Spowoduje to wygenerowanie podpisie, który zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzny zwracanych wartości są następnie właściwości obiektu komunikatu odpowiedzi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
