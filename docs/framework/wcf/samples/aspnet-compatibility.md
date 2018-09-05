---
title: Zgodność platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
ms.openlocfilehash: eeb09914fc90848c987127c789379549917063f6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659516"
---
# <a name="aspnet-compatibility"></a>Zgodność platformy ASP.NET
Niniejszy przykład pokazuje, jak włączyć tryb zgodności ASP.NET w Windows Communication Foundation (WCF). Usługi działające w zgodność platformy ASP.NET, tryb uczestniczą w pełni potoku platformy ASP.NET w aplikacji i ułatwia korzystanie z funkcji programu ASP.NET, takich jak plik lub adres URL autoryzacji, stan sesji i <xref:System.Web.HttpContext> klasy. <xref:System.Web.HttpContext> Klasy zezwala na dostęp do plików cookie, sesje i inne funkcje platformy ASP.NET. Ten tryb wymaga powiązania użyj transportu HTTP i usługi muszą być hostowane w usługach IIS.  
  
 W tym przykładzie klient to aplikacja konsoli (plik wykonywalny), a usługa jest hostowana w Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
Ten przykładowy skrypt wymaga [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] puli aplikacji, aby można było uruchomić. Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślnej puli aplikacji, wykonaj następujące kroki.  

1.  Otwórz **Panel sterowania**.  Otwórz **narzędzia administracyjne** apletu w obszarze **System i zabezpieczenia** nagłówka. Otwórz **Internet Information Services (IIS) Manager** apletu.  

2.  Rozwiń węzeł treeview w **połączeń** okienka. Wybierz **pul aplikacji** węzła.  

3.  Do ustawiania domyślnej puli aplikacji do użycia [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (która może powodować problemów niezgodność z istniejących witryn), kliknij prawym przyciskiem myszy **DefaultAppPool** elementu listy, a następnie wybierz pozycję **podstawowych ustawień...** . Ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).  

4.  Aby utworzyć nową pulę aplikacji, która używa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (w celu zachowania zgodności dla innych aplikacji), kliknij prawym przyciskiem myszy **pul aplikacji** a następnie wybierz węzeł **Dodawanie puli aplikacji...** . Nadaj nazwę nowej puli aplikacji, a następnie ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza). Po instalujący kroki poniżej, kliknij prawym przyciskiem myszy **ServiceModelSamples** aplikacji i wybierz **Zarządzanie aplikacją**, **ustawienia zaawansowane...** . Ustaw **puli aplikacji** do nowej puli aplikacji.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługę kalkulatora. `ICalculator` Kontraktu została zmodyfikowana jako `ICalculatorSession` kontraktu zezwolić na zestaw operacji wykonywanych przy jednoczesnym zachowaniu wynik uruchomionych.  
  
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
  
 Usługa zapewnia stanu, korzystanie z funkcji dla każdego klienta, jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń. Klient może pobrać bieżący wynik, wywołując `Result` i wyczyścić wynik, który ma wartość zero, wywołując `Clear`.  
  
 Usługa używa sesji programu ASP.NET, aby przechować wynik dla każdej sesji klienta. Dzięki temu usługa do obsługi uruchomionych wyników dla każdego klienta w wielu wywołań do usługi.  
  
> [!NOTE]
> Stan sesji programu ASP.NET i WCF sesji są bardzo różnych rzeczy. Zobacz [sesji](../../../../docs/framework/wcf/samples/session.md) szczegółowe informacje dotyczące sesji usługi WCF.
  
 Usługa ma zależność obsługi stanu sesji platformy ASP.NET i wymaga tryb zgodności ASP.NET, aby działo poprawnie. Te wymagania są wyrażone w sposób deklaratywny, stosując `AspNetCompatibilityRequirements` atrybutu.  
  
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
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po rozwiązaniu został utworzony, uruchom Setup.bat jest, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Katalog ServiceModelSamples teraz powinny się wyświetlać jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
