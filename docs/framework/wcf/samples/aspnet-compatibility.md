---
title: "Zgodność platformy ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c8cf38e65bbc917720b1a1c5b604d81ca536c14
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="aspnet-compatibility"></a>Zgodność platformy ASP.NET
W tym przykładzie pokazano, jak włączyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Usługi uruchomione [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności uczestniczyć w pełni [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji potoku i może wykonywać użycie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji, takich jak autoryzacja pliku lub adres URL, stan sesji i <xref:System.Web.HttpContext> klasy. <xref:System.Web.HttpContext> Klasy zezwala na dostęp do plików cookie sesji i innych [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji. Ten tryb wymaga powiązania korzystać z transportu HTTP i musi być obsługiwana przez usługę w usługach IIS.  
  
 W tym przykładzie klient jest aplikacji konsoli (plik wykonywalny), a usługa jest obsługiwana w Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!NOTE]
>  W tym przykładzie wymaga [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] puli aplikacji, aby można było uruchomić. Aby utworzyć nową pulę aplikacji lub zmodyfikować domyślnej puli aplikacji, wykonaj następujące kroki.  
>   
>  1.  Otwórz **Panel sterowania**.  Otwórz **narzędzia administracyjne** apletu w obszarze **System i zabezpieczenia** nagłówka. Otwórz **Internet Information Services (IIS) Manager** apletu.  
> 2.  Rozwiń element treeview w **połączeń** okienka. Wybierz **pul aplikacji** węzła.  
> 3.  Aby ustawić domyślnej puli aplikacji do użycia [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (co może spowodować problemy niezgodności z istniejących lokacji,) kliknij prawym przyciskiem myszy **domyślna pula aplikacji** elementu listy, a następnie wybierz **podstawowych ustawień...** . Ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza).  
> 4.  Aby utworzyć nową pulę aplikacji, która używa [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (Aby zachować zgodność z innych aplikacji), kliknij prawym przyciskiem myszy **pul aplikacji** a następnie wybierz węzeł **Dodawanie puli aplikacji...** . Nazwa nowej puli aplikacji, a następnie ustaw **.Net Framework w wersji** rozwijanego do **.Net Framework v4.0.30128** (lub nowsza). Po uruchomić Instalatora kroków poniżej, kliknij prawym przyciskiem myszy **ServiceModelSamples** aplikacji i wybierz **aplikacji Zarządzanie**, **Zaawansowane ustawienia...** . Ustaw **puli aplikacji** do nowej puli aplikacji.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje usługi Kalkulator. `ICalculator` Kontraktu został zmodyfikowany jako `ICalculatorSession` kontraktu umożliwiają zestaw operacji wykonywanych przy zachowaniu uruchomionych wynik.  
  
```  
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
  
 Usługa zachowuje swój stan, korzystanie z funkcji, dla każdego klienta, jak wiele operacji usługi są wywoływane w celu wykonywania obliczeń. Klient może pobrać bieżący wynik przez wywołanie metody `Result` i wyczyścić wynik, który ma wartość zero, wywołując `Clear`.  
  
 Używane przez usługę [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesji, aby przechowywać wynik dla każdej sesji klienta. Dzięki temu usługę, aby zachować wynik uruchomiony dla każdego klienta w całej wielu wywołań do usługi.  
  
> [!NOTE]
>  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Stan sesji i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesje są bardzo różnych rzeczy.  Zobacz [sesji](../../../../docs/framework/wcf/samples/session.md) szczegółowe informacje na temat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesji.  
  
 Usługa ma zależności jednorodnej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] stan sesji i wymaga [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności, aby mógł działać poprawnie. Te wymagania są wyrażane deklaratywnie przez zastosowanie `AspNetCompatibilityRequirements` atrybutu.  
  
```  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po utworzeniu rozwiązania należy uruchomić pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Katalog ServiceModelSamples powinien zostać wyświetlony jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
