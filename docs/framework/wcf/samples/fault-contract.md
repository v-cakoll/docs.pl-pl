---
title: Kontrakt błędu
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 5b3348f31d239d6bf7e64852ba02010115062669
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625246"
---
# <a name="fault-contract"></a>Kontrakt błędu
Przykładowe kontrakt błędu pokazuje, jak komunikować informacje o błędzie z usługi do klienta. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), za pomocą dodatkowy kod dodany do usługi, aby przekonwertować wyjątek wewnętrzny błąd. Klient próbuje wykonać dzielenie przez zero, aby wymusić warunek błędu usługi.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Kontrakt Kalkulator została zmodyfikowana, aby uwzględnić <xref:System.ServiceModel.FaultContractAttribute> jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
  
 <xref:System.ServiceModel.FaultContractAttribute> Atrybut wskazuje, że `Divide` operacja może zwrócić błąd typu `MathFault`. Awarii może być dowolnego typu, który może być serializowany. W tym przypadku `MathFault` jest kontraktu danych, w następujący sposób:  
  
```  
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
  
 `Divide` Metoda zgłasza wyjątek <xref:System.ServiceModel.FaultException%601> występuje wyjątek podczas dzielenia przez zero wyjątek, jak pokazano w poniższym przykładowym kodzie. Ten wyjątek powoduje błąd, są wysyłane do klienta.  
  
```  
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
  
 Kod klienta powoduje błąd przez zażądanie dzielenia przez zero. Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Zobaczysz dzielenia przez zero, które zgłaszają się jako błąd. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient robi to przez odpowiednie `FaultException<MathFault>` wyjątek:  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Domyślnie szczegółowe informacje o nieoczekiwane wyjątki nie są wysyłane do klienta zapobiegające szczegółowe informacje o implementacji usługi ucieczce granicę bezpiecznej usługi. `FaultContract` zapewnia sposób opisania usterek w umowie i oznaczania niektórych rodzajów wyjątków zgodnie z potrzebami w celu przesłania go do klienta. `FaultException<T>` udostępnia mechanizm środowiska wykonawczego wysyłanie błędów do odbiorców.  
  
 Jest przydatne podczas debugowania, zobacz szczegóły wewnętrznego błędu usługi. Aby wyłączyć to zachowanie bezpiecznych opisany wcześniej, można wskazać, że należy uwzględnić szczegółowe informacje o każdym nieobsługiwany wyjątek na serwerze w domenach błędów, które są wysyłane do klienta. Jest to realizowane przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> do `true`. Można ustawić go w kodzie lub w konfiguracji, jak pokazano w następującym przykładzie.  
  
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
  
 Ponadto zachowanie musi być skojarzony z usługą, ustawiając `behaviorConfiguration` atrybut usługi w pliku konfiguracji "CalculatorServiceBehavior".  
  
 Aby wykryć takie błędy na kliencie, inną niż ogólna <xref:System.ServiceModel.FaultException> musi być przechwycony.  
  
 To zachowanie można stosować tylko na potrzeby debugowania i nigdy nie powinna być włączona w środowisku produkcyjnym.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Zobacz też
