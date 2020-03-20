---
title: Kontrakt błędu
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: c8e93f73d150132c9d6750b81ba2ade944808d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183666"
---
# <a name="fault-contract"></a>Kontrakt błędu
Przykład kontraktu usterki pokazuje, jak przekazać informacje o błędzie z usługi do klienta. Przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md)z pewnym dodatkowym kodem dodanym do usługi, aby przekonwertować wewnętrzny wyjątek na błąd. Klient próbuje wykonać podział przez zero, aby wymusić warunek błędu w usłudze.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt kalkulatora został zmodyfikowany w <xref:System.ServiceModel.FaultContractAttribute> celu uwzględnienia, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 Atrybut <xref:System.ServiceModel.FaultContractAttribute> wskazuje, że `Divide` operacja może zwrócić błąd `MathFault`typu . Błąd może być dowolnego typu, który może być serializowany. W takim przypadku `MathFault` jest kontrakt danych, w następujący sposób:  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 Metoda `Divide` zgłasza <xref:System.ServiceModel.FaultException%601> wyjątek, gdy występuje wyjątek dzielenia przez zero, jak pokazano w poniższym przykładowym kodzie. Ten wyjątek powoduje, że błąd jest wysyłany do klienta.  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 Kod klienta wymusza błąd, żądając podziału przez zero. Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Widzisz podział przez zero jest zgłaszane jako błąd. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient robi to, łapiąc odpowiedni `FaultException<MathFault>` wyjątek:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Domyślnie szczegóły nieoczekiwanych wyjątków nie są wysyłane do klienta, aby zapobiec szczegóły implementacji usługi z ucieczki bezpiecznej granicy usługi. `FaultContract`zapewnia sposób opisywania usterek w umowie i oznaczanie niektórych rodzajów wyjątków, stosownie do przekazywania do klienta. `FaultException<T>`zapewnia mechanizm wykonywania do wysyłania błędów do konsumentów.  
  
 Jednak jest przydatne, aby zobaczyć wewnętrzne szczegóły błędu usługi podczas debugowania. Aby wyłączyć bezpieczne zachowanie wcześniej opisane, można wskazać, że szczegóły każdego nieobsługiwał wyjątek na serwerze powinny być uwzględnione w usterce, która jest wysyłana do klienta. Można to osiągnąć <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> poprzez `true`ustawienie . Można ustawić go w kodzie lub w konfiguracji, jak pokazano w poniższym przykładzie.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Ponadto zachowanie musi być skojarzone z usługą, ustawiając `behaviorConfiguration` atrybut usługi w pliku konfiguracyjnym na "CalculatorServiceBehavior".  
  
 Aby złapać takie błędy na kliencie, <xref:System.ServiceModel.FaultException> nierodzysk należy złapać.  
  
 To zachowanie powinno być używane tylko do celów debugowania i nigdy nie powinny być włączone w produkcji.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
