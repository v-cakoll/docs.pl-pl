---
title: Zgodność platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: a718b3f3bcbfd4bc2b74a14ba8f20cd8c335877f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925277"
---
# <a name="aspnet-compatibility"></a>Zgodność platformy ASP.NET
Ten przykład pokazuje, jak włączyć tryb zgodności ASP.NET w Windows Communication Foundation (WCF). Usługi działające w trybie zgodności ASP.NET uczestniczą w pełni w potoku aplikacji ASP.NET i mogą korzystać z funkcji ASP.NET, takich jak autoryzacja plików/adresów URL, <xref:System.Web.HttpContext> stan sesji i Klasa. <xref:System.Web.HttpContext> Klasa umożliwia dostęp do plików cookie, sesji i innych funkcji ASP.NET. Ten tryb wymaga, aby powiązania korzystały z transportu HTTP i sama usługa musi być hostowana w usługach IIS.  
  
 W tym przykładzie klient jest aplikacją konsolową (plik wykonywalny), a usługa jest hostowana w Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
Aby można było uruchomić [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] ten przykład, wymagana jest pula aplikacji. Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślną pulę aplikacji, wykonaj następujące kroki.  

1. Otwórz **Panel sterowania**.  Otwórz aplet **Narzędzia administracyjne** w nagłówku **system i zabezpieczenia** . Otwórz aplet **menedżer Internet Information Services (IIS)** .  

2. Rozwiń element TreeView w okienku **połączenia** . Wybierz węzeł **Pule aplikacji** .  

3. Aby ustawić domyślną pulę aplikacji, która ma [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] być używana (co może spowodować problemy ze zgodnością z istniejącymi lokacjami), kliknij prawym przyciskiem myszy element listy z opcją **Domyślna** i wybierz pozycję **Ustawienia podstawowe.** . Ustaw ściąganie **wersji programu .NET Framework** w **programie .NET Framework v 4.0.30128** (lub nowszym).  

4. Aby utworzyć nową pulę aplikacji używaną [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] przez program (w celu zachowania zgodności z innymi aplikacjami), kliknij prawym przyciskiem myszy węzeł **Pule aplikacji** i wybierz polecenie **Dodaj pulę aplikacji.** . Nadaj nazwę nowej puli aplikacji, a następnie ustaw opcję ściągania **wersji programu .NET Framework** w **programie .NET Framework v 4.0.30128** (lub nowszym). Po uruchomieniu poniższych kroków instalacji kliknij prawym przyciskiem myszy aplikację **servicemodelsamples** i wybierz pozycję **Zarządzaj aplikacją**, **Ustawienia zaawansowane...** . Ustaw **pulę aplikacji** na nową pulę aplikacji.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługę kalkulatora. Umowa została zmodyfikowana `ICalculatorSession` jako kontrakt, aby zezwolić na wykonywanie zestawu operacji przy zachowaniu uruchomionego wyniku. `ICalculator`  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 Usługa zachowuje stan przy użyciu funkcji dla każdego klienta, jako że wiele operacji usługi jest wywoływanych w celu wykonania obliczeń. Klient może pobrać bieżący wynik, wywołując `Result` i może wyczyścić wynik do zera przez wywołanie metody. `Clear`  
  
 Usługa używa sesji ASP.NET do przechowywania wyników dla każdej sesji klienta. Dzięki temu usługa może zachować wynik działania dla każdego klienta w wielu wywołaniach do usługi.  
  
> [!NOTE]
> Stan sesji ASP.NET i sesje WCF są bardzo różne. Aby uzyskać szczegółowe informacje na temat sesji WCF, zobacz temat [sesja](../../../../docs/framework/wcf/samples/session.md) .
  
 Usługa ma zależność Intimate na stanie sesji ASP.NET i wymaga trybu zgodności ASP.NET w celu poprawnego działania. Te wymagania są wyrażane w sposób deklaratywny `AspNetCompatibilityRequirements` przez zastosowanie atrybutu.  
  
```csharp  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po skompilowaniu rozwiązania Uruchom polecenie Setup. bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7,0. Katalog ServiceModelSamples powinien teraz pojawić się jako aplikacja usług IIS 7,0.  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu i trwałości usługi AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
