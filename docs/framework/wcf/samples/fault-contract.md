---
title: "Kontrakt błędu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf0f615ae338d9ad52cc8c40096e7130fb111ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="fault-contract"></a>Kontrakt błędu
Kontrakt błędu przykładowych pokazano, jak informacje o błędzie z usługi klientowi komunikowanie się. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), niektóre dodatkowy kod dodane do usługi, aby przekonwertować wyjątek wewnętrzny błąd. Klient próbuje wykonać dzielenie przez zero, aby wymusić warunek błędu usługi.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt Kalkulator został zmodyfikowany w celu obejmują <xref:System.ServiceModel.FaultContractAttribute> jak pokazano w poniższym kodzie próbki.  
  
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
  
 <xref:System.ServiceModel.FaultContractAttribute> Atrybut wskazuje, że `Divide` operacji mogą zwracać błąd typu `MathFault`. Błąd może być dowolnego typu, który można serializować. W takim przypadku `MathFault` jest kontraktu danych, w następujący sposób:  
  
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
  
 `Divide` Metoda zgłasza <xref:System.ServiceModel.FaultException%601> występuje wyjątek podczas dzielenia przez zero wyjątek, jak pokazano w poniższym kodzie próbki. Ten wyjątek powoduje błąd są wysyłane do klienta.  
  
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
  
 Kod klienta wymusza błąd przez zażądanie dzielenia przez zero. Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Zobaczysz dzielenia przez zero zgłaszają się jako błąd. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
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
  
 Domyślnie szczegóły nieoczekiwanego wyjątku nie są wysyłane do klienta zapobiegające szczegóły implementacji usługi z anulowanie bezpiecznej granic usługi. `FaultContract`zapewnia sposób błędów w kontrakcie opisywania i oznacz niektórych typów wyjątków odpowiednio do przekazania do klienta. `FaultException<T>`udostępnia mechanizm środowiska wykonawczego wysyłanie błędów do użytkowników.  
  
 Jednak jest przydatne wyświetlić szczegóły wewnętrznego błędu usługi podczas debugowania. Aby wyłączyć bezpieczny zachowanie opisany powyżej, może oznaczać, że szczegóły każdego nieobsługiwany wyjątek na serwerze powinny być objęte usterek, które są wysyłane do klienta. Jest to osiągane przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> do `true`. Można albo ustawiony w kodzie, lub w konfiguracji, jak pokazano w poniższym przykładzie.  
  
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
  
 Ponadto zachowanie może być skojarzony z usługą przez ustawienie `behaviorConfiguration` atrybutu service w pliku konfiguracji, aby "CalculatorServiceBehavior".  
  
 Aby wykryć takie błędy po stronie klienta, inny niż ogólny <xref:System.ServiceModel.FaultException> musi być przechwycony.  
  
 To zachowanie, należy używać tylko na potrzeby debugowania i nigdy nie powinno być włączone w środowisku produkcyjnym.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Zobacz też
