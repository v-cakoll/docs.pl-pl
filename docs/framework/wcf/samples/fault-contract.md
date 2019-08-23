---
title: Kontrakt błędu
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 914ac85d0aaecfaec84eeacc12461bd3c7023e54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961410"
---
# <a name="fault-contract"></a>Kontrakt błędu
Przykładowa umowa dotycząca błędu demonstruje sposób komunikacji z klientem informacji o błędach z usługi. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), z dodatkowym kodem dodanym do usługi w celu przekonwertowania wewnętrznego wyjątku na błąd. Klient próbuje wykonać dzielenie przez zero w celu wymuszenia błędu w usłudze.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt kalkulatora został zmodyfikowany w taki sposób, <xref:System.ServiceModel.FaultContractAttribute> aby zawierał element, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Ten <xref:System.ServiceModel.FaultContractAttribute> atrybut wskazuje `Divide` , że operacja może zwrócić błąd typu `MathFault`. Błąd może być dowolnego typu, który może być serializowany. W tym przypadku `MathFault` jest to kontrakt danych w następujący sposób:  
  
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
  
 `Divide` Metoda<xref:System.ServiceModel.FaultException%601> zgłasza wyjątek, gdy wystąpi wyjątek dzielenia przez zero, jak pokazano w poniższym przykładowym kodzie. Ten wyjątek powoduje, że błąd jest wysyłany do klienta.  
  
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
  
 Kod klienta wymusza błąd, żądając dzielenia przez zero. Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Zobaczysz, że dzielenie przez zero zostanie zgłoszone jako błąd. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient wykonuje to poprzez przechwycenie odpowiedniego `FaultException<MathFault>` wyjątku:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Domyślnie szczegóły nieoczekiwanych wyjątków nie są wysyłane do klienta, aby zapobiec szczegółom implementacji usługi z ucieczki bezpiecznej granicy usługi. `FaultContract`zapewnia sposób opisywania błędów w kontrakcie i oznaczania niektórych typów wyjątków zgodnie z potrzebami do przesyłania danych do klienta. `FaultException<T>`zapewnia mechanizm czasu wykonywania do wysyłania błędów do odbiorców.  
  
 Jednak podczas debugowania warto zobaczyć wewnętrzne szczegóły błędu usługi. Aby wyłączyć wcześniej opisane bezpieczne zachowanie, można wskazać, że szczegóły każdego nieobsługiwanego wyjątku na serwerze powinny być dołączone do błędu wysyłanego do klienta programu. Jest to realizowane przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>. `true` Można ustawić ją w kodzie lub w konfiguracji, jak pokazano w poniższym przykładzie.  
  
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
  
 Ponadto zachowanie musi być skojarzone z usługą przez ustawienie `behaviorConfiguration` atrybutu usługi w pliku konfiguracji na "CalculatorServiceBehavior".  
  
 Aby przechwytywać takie błędy na kliencie, należy przechwycić nieogólne <xref:System.ServiceModel.FaultException> .  
  
 Takie zachowanie powinno być używane tylko do celów debugowania i nigdy nie powinno być włączone w środowisku produkcyjnym.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
