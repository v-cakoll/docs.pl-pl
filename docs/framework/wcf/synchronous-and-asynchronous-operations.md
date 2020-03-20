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
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143216"
---
# <a name="synchronous-and-asynchronous-operations"></a>Operacje synchroniczne i asynchroniczne
W tym temacie omówiono implementowanie i wywoływanie operacji usługi asynchroniczne.  
  
 Wiele aplikacji wywołać metody asynchronicznie, ponieważ umożliwia aplikacji, aby kontynuować wykonywanie przydatnej pracy podczas wykonywania wywołania metody. Usługi i klienci Windows Communication Foundation (WCF) mogą uczestniczyć w asynchronicznym wywołaniach operacyjnych na dwóch różnych poziomach aplikacji, które zapewniają aplikacjom WCF jeszcze większą elastyczność, aby zmaksymalizować przepustowość zrównoważoną względem interaktywności .  
  
## <a name="types-of-asynchronous-operations"></a>Rodzaje operacji asynchronicznych  
 Wszystkie kontrakty serwisowe w WCF, bez względu na typy parametrów i wartości zwracane, użyj atrybutów WCF, aby określić wzorzec wymiany określonego komunikatu między klientem a usługą. WCF automatycznie kieruje przychodzące i wychodzące wiadomości do odpowiedniej operacji usługi lub uruchomionego kodu klienta.  
  
 Klient posiada tylko umowy serwisowej, która określa wzorzec wymiany komunikatów dla określonej operacji. Klienci mogą zaoferować deweloperowi dowolny model programowania, który wybierze, o ile zostanie zaobserwowany wzorzec wymiany wiadomości. Tak też można zaimplementować operacje w dowolny sposób, tak długo, jak określony wzorzec komunikatów jest przestrzegane.  
  
 Niezależność umowy serwisowej od implementacji usługi lub klienta umożliwia następujące formy wykonywania asynchronicznego w aplikacjach WCF:  
  
- Klienci mogą wywoływać operacje żądania/odpowiedzi asynchronicznie przy użyciu synchronicznie wymiany komunikatów.  
  
- Usługi można zaimplementować operację żądania/odpowiedzi asynchronicznie przy użyciu synchronicznie wymiany komunikatów.  
  
- Wymiana komunikatów może być jednokierunkowa, niezależnie od implementacji klienta lub usługi.  
  
### <a name="suggested-asynchronous-scenarios"></a>Sugerowane scenariusze asynchroniczne  
 Użyj podejścia asynchroniiowego w implementacji operacji usługi, jeśli implementacja usługi operacji wywołuje blokowanie, takie jak wykonywanie pracy we/wy. Gdy jesteś w implementacji operacji asynchroniiowej, spróbuj wywołać operacje asynchroniczne i metody, aby rozszerzyć ścieżkę wywołania asynchroniiowego tak daleko, jak to możliwe. Na przykład wywołać `BeginOperationTwo()` `BeginOperationOne()`od wewnątrz .  
  
- Użyj podejścia asynchroniiowego w aplikacji klienta lub wywołującej w następujących przypadkach:  
  
- Jeśli wywołujesz operacje z aplikacji warstwy środkowej. (Aby uzyskać więcej informacji na temat takich scenariuszy, zobacz [Aplikacje klienckie warstwy środkowej](./feature-details/middle-tier-client-applications.md).)  
  
- Jeśli wywołujesz operacje w ASP.NET stronie, użyj stron asynchronicznych.  
  
- Jeśli wywołujesz operacje z dowolnej aplikacji, która jest jednowątkowa, takich jak Windows Forms lub Windows Presentation Foundation (WPF). Podczas korzystania z modelu wywoływania asynchronicznego opartego na zdarzeniach zdarzenie wynik jest wywoływane w wątku interfejsu użytkownika, dodając responsywność do aplikacji bez konieczności obsługi wielu wątków samodzielnie.  
  
- Ogólnie rzecz biorąc, jeśli masz wybór między wywołaniem synchroniowym i asynchronialnym, wybierz wywołanie asynchroniczne.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Implementowanie operacji usługi asynchroniiowej  
 Operacje asynchroniczne można zaimplementować przy użyciu jednej z trzech następujących metod:  
  
1. Wzorzec asynchroniczne oparte na zadaniach  
  
2. Wzorzec asynchroniczne oparte na zdarzeniach  
  
3. Wzór asynchroniczne IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Wzorzec asynchroniczne oparte na zadaniach  
 Wzorzec asynchroniczne oparte na zadaniach jest preferowanym sposobem implementowania operacji asynchronicznych, ponieważ jest najprostszym i najbardziej prostym. Aby użyć tej metody wystarczy zaimplementować\<operację usługi i określić typ zwracany zadania T>, gdzie T jest typem zwróconym przez operację logiczną. Przykład:  
  
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
  
 Operacja SampleMethodTaskAsync zwraca\<ciąg zadań> ponieważ operacja logiczna zwraca ciąg. Aby uzyskać więcej informacji na temat wzorca asynchronicznego opartego na zadaniach, zobacz [Wzorzec asynchroniczne oparte na zadaniach](https://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
> Podczas korzystania z wzorca asynchronicznego opartego na zadaniach może zostać zgłoszony, jeśli wystąpi wyjątek podczas oczekiwania na zakończenie operacji. Wyjątek ten może wystąpić w przypadku klienta lub usług  
  
#### <a name="event-based-asynchronous-pattern"></a>Wzorzec asynchroniczne oparte na zdarzeniach  
 Usługa, która obsługuje wzorzec asynchroniczne oparte na zdarzenia będzie miał jedną lub więcej operacji o nazwie MethodNameAsync. Metody te mogą dublować wersje synchroniczne, które wykonują tę samą operację w bieżącym wątku. Klasa może również mieć MethodNameCompleted zdarzenia i może mieć MethodNameAsyncCancel (lub po prostu CancelAsync) metoda. Klient, który chce wywołać operację, zdefiniuje program obsługi zdarzeń, który ma zostać wywołany po zakończeniu operacji,  
  
 Poniższy fragment kodu ilustruje sposób deklarowania operacji asynchronicznych przy użyciu wzorca asynchronitycznego opartego na zdarzeniach.  
  
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
  
 Aby uzyskać więcej informacji na temat wzorca asynchroniowego opartego na zdarzeniach, zobacz [Wzorzec asynchroniczne oparte na zdarzeniach](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Wzór asynchroniczne IAsyncResult  
 Operację usługi można zaimplementować w sposób asynchroniczne przy użyciu wzorca programowania `<Begin>` asynchronitycznego `true`programu .NET Framework i oznaczania metody z właściwością ustawioną na <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> . W takim przypadku operacja asynchroniza jest widoczna w metadanych w tej samej formie co operacja synchroniczni: jest widoczna jako pojedyncza operacja z komunikatem żądania i komunikatem skorelowanej odpowiedzi. Modele programowania klienta mają wtedy wybór. Mogą reprezentować ten wzorzec jako operację synchronicznie lub jako operację asynchronizacyjną, o ile po wywołaniu usługi odbywa się wymiana komunikatów żądanie-odpowiedź.  
  
 Ogólnie rzecz biorąc, z asynchronialnego charakteru systemów, nie należy przyjmować zależności od wątków.  Najbardziej niezawodnym sposobem przekazywania danych na różnych etapach przetwarzania wysyłki operacji jest użycie rozszerzeń.  
  
 Na przykład zobacz [Jak: Implementowanie operacji usługi asynchroniiowej](how-to-implement-an-asynchronous-service-operation.md).  
  
 Aby zdefiniować `X` operację kontraktu, która jest wykonywana asynchronicznie, niezależnie od tego, jak jest wywoływana w aplikacji klienckiej:  
  
- Zdefiniuj `BeginOperation` dwie `EndOperation`metody za pomocą wzorca i .  
  
- Metoda `BeginOperation` zawiera `in` `ref` i parametry dla operacji <xref:System.IAsyncResult> i zwraca typ.  
  
- Metoda `EndOperation` zawiera <xref:System.IAsyncResult> parametr, a `out` także `ref` parametry i zwraca typ zwracany operacje.  
  
 Na przykład zobacz następującą metodę.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Aby utworzyć operację asynchronizacyjną, dwie metody będą następujące:  
  
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
> Atrybut <xref:System.ServiceModel.OperationContractAttribute> jest stosowany tylko do `BeginDoWork` metody. Wynikowy kontrakt ma jedną operację `DoWork`WSDL o nazwie .  
  
### <a name="client-side-asynchronous-invocations"></a>Wywołania asynchroniczne po stronie klienta  
 Aplikacja kliencka WCF może używać dowolnego z trzech asynchronicznych modeli wywołujących opisanych wcześniej  
  
 Podczas korzystania z modelu opartego na zadaniach wystarczy wywołać operację przy użyciu await słowa kluczowego, jak pokazano w poniższym fragmentie kodu.  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Przy użyciu wzorca asynchroniiowego oparte na zdarzeniach wymaga tylko dodanie programu obsługi zdarzeń, aby otrzymać powiadomienie o odpowiedzi - i wynikowe zdarzenie jest wywoływane w wątku interfejsu użytkownika automatycznie. Aby użyć tego podejścia, należy określić opcje polecenia **/async** i **/tcv:Version35** za pomocą [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)jak w poniższym przykładzie.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Po wykonaniu tej czynności Svcutil.exe generuje klasę klienta WCF z infrastrukturą zdarzeń, która umożliwia aplikacji wywołującej do zaimplementowania i przypisać program obsługi zdarzeń, aby otrzymać odpowiedź i podjąć odpowiednie działania. Aby uzyskać pełny przykład, zobacz [Jak: Wywołanie operacji usługi Asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Model asynchroniczne oparty na zdarzeniach jest jednak dostępny tylko w programach .NET Framework 3.5. Ponadto nie jest obsługiwany nawet w .NET Framework 3.5, gdy kanał klienta <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>WCF jest tworzony przy użyciu . Z WCF obiektów kanału klienta, należy użyć <xref:System.IAsyncResult?displayProperty=nameWithType> obiektów do wywoływania operacji asynchronicznie. Aby użyć tego podejścia, należy określić **/async** opcji polecenia z [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jak w poniższym przykładzie.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 Generuje umowy serwisowej, w którym każda `<Begin>` operacja jest <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> modelowany `true` jako `<End>` metoda z właściwości ustawionej i odpowiedniej metody. Pełny przykład przy <xref:System.ServiceModel.ChannelFactory%601>użyciu , zobacz [Jak: Wywołanie operacji asynchronicznie przy użyciu fabryki kanałów](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 W obu przypadkach aplikacje mogą wywoływać operację asynchronicznie, nawet jeśli usługa jest implementowana synchronicznie, w taki sam sposób, w jaki aplikacja może używać tego samego wzorca do wywoływania asynchronicznie lokalnej metody synchroniczowej. Sposób implementacji operacji nie ma znaczenia dla klienta; po odebraniu komunikatu odpowiedzi jego zawartość jest wywoływana do asynchroniczne <`End`> metody klienta i klient pobiera informacje.  
  
### <a name="one-way-message-exchange-patterns"></a>Wzorce wymiany komunikatów jednokierunkowych  
 Można również utworzyć wzorzec wymiany komunikatów asynchronicznych, w <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> którym `true` operacje jednokierunkowe (operacje, dla których jest nie ma skorelowanej odpowiedzi) mogą być wysyłane w kierunku przez klienta lub usługi niezależnie od drugiej strony. (Spowoduje to użycie wzorca wymiany komunikatów dupleksu z komunikatami jednokierunkowymi). W takim przypadku umowa serwisowa określa jednokierunkową wymianę komunikatów, która każda ze stron może zaimplementować jako wywołania asynchroniczne lub implementacje lub nie, w stosownych przypadkach. Ogólnie rzecz biorąc, gdy umowa jest wymiana komunikatów jednokierunkowych, implementacje mogą być w dużej mierze asynchroniczne, ponieważ po wysłaniu wiadomości aplikacja nie czeka na odpowiedź i może kontynuować wykonywanie innych prac.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Asynchronii klienci i kontrakty wiadomości oparte na zdarzeniach  
 Wytyczne projektowe dla stanu modelu asynchroniowego opartego na zdarzeniach, że jeśli `Result` zwracana jest więcej niż jedna <xref:System.EventArgs> wartość, jedna wartość jest zwracana jako właściwość, a pozostałe są zwracane jako właściwości obiektu. Jednym z wyników jest to, że jeśli klient importuje metadane przy użyciu opcji polecenia asynchronicznego opartego na zdarzeniach, a operacja zwraca więcej niż jedną wartość, domyślny <xref:System.EventArgs> obiekt zwraca jedną wartość jako `Result` właściwość, a pozostała część to właściwości <xref:System.EventArgs> obiektu.  
  
 Jeśli chcesz otrzymać obiekt wiadomości `Result` jako właściwość i mieć zwrócone wartości jako właściwości tego obiektu, użyj opcji polecenia **/messageContract.** Spowoduje to wygenerowanie podpisu, który `Result` zwraca <xref:System.EventArgs> komunikat odpowiedzi jako właściwość na obiekcie. Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikatu odpowiedzi.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
