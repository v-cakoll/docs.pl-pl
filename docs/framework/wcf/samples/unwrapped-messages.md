---
title: Nieopakowane komunikaty
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: a3f3548e8dc8a85127eae3d080888c304bfa4b90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623134"
---
# <a name="unwrapped-messages"></a>Nieopakowane komunikaty
Niniejszy przykład pokazuje nieopakowane komunikaty. Domyślnie treść komunikatu jest sformatowany w taki sposób, że zostaną opakowane parametrów do operacji usługi. Następujące przykładowe pokazuje `Add` komunikat żądania do `ICalculator` usługi w trybie opakowana.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 `<Add>` Opakowuje element w treści komunikatu `n1` i `n2` parametrów. Natomiast poniższy przykład pokazuje równoważne komunikatu w trybie odkodowany.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 Nieopakowane wiadomości nie jest zawijany `n1` i `n2` parametrów w elemencie zawierającego, są one bezpośrednie elementy podrzędne elementu treści protokołu soap.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W tym przykładzie tworzona jest wiadomość nieopakowanych, stosując <xref:System.ServiceModel.MessageContractAttribute> typem parametru operacji usługi i typ zwracanej wartości, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 Aby umożliwić wyświetlanie komunikatów wysyłanych i odbieranych, w tym przykładzie użyto śledzenia. Ponadto <xref:System.ServiceModel.WSHttpBinding> została skonfigurowana bez zabezpieczeń w celu zmniejszenia liczby wiadomości, które rejestruje.  
  
 Wynikowy dziennika śledzenia (c:\logs\Message.log) mogą być wyświetlane za pomocą [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Zaznacz, aby wyświetlić zawartość wiadomości **wiadomości** zarówno po lewej stronie, jak i prawego okienka narzędzi przeglądarki danych śledzenia usługi. Dzienniki śledzenia w tym przykładzie są skonfigurowane do wygenerowania w folderze C:\LOGS. Utwórz ten folder przed uruchomieniem przykładu i przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Utwórz katalog C:\LOGS rejestrowanie komunikatów. Przyznać użytkownikowi uprawnienia do tego katalogu zapisu usługi sieciowej.  
  
3.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a>Zobacz także
