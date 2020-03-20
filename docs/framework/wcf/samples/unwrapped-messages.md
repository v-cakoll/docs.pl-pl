---
title: Nieopakowane komunikaty
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 81592910d8530cea2df5ec1fd8a8b1145350ef78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143736"
---
# <a name="unwrapped-messages"></a>Nieopakowane komunikaty
W tym przykładzie pokazano nieopakowane wiadomości. Domyślnie treść wiadomości jest sformatowany w taki sposób, że parametry operacji usługi są zawijane. W poniższym `Add` przykładzie przedstawiono komunikat żądania do `ICalculator` usługi w trybie zawiniętym.  
  
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
  
 Element `<Add>` w treści wiadomości zawija `n1` parametry i. `n2` Natomiast w poniższym przykładzie przedstawiono równoważny komunikat w trybie rozpakowanym.  
  
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
  
 Nieopakowana wiadomość nie zawija `n1` i `n2` parametrów w element zawierający, są bezpośrednimi elementami podrzędnymi elementu treści mydła.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie nieopakowany komunikat jest <xref:System.ServiceModel.MessageContractAttribute> tworzony przez zastosowanie do typu parametru operacji usługi i zwraca typ wartości, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Aby umożliwić wyświetlanie wiadomości wysyłanych i odbieranych, w tym przykładzie użyto śledzenia. Ponadto <xref:System.ServiceModel.WSHttpBinding> został skonfigurowany bez zabezpieczeń, aby zmniejszyć liczbę komunikatów, które rejestruje.  
  
 Wynikowy dziennik śledzenia (c:\logs\Message.log) można wyświetlić za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Aby wyświetlić zawartość wiadomości, wybierz **pozycję Wiadomości** zarówno po lewej, jak i po prawej stronie narzędzia Podgląd śledzenia usług. Dzienniki śledzenia w tym przykładzie są skonfigurowane do generowania w folderze C:\LOGS. Utwórz ten folder przed uruchomieniem próbki i nadaj użytkownikowi uprawnienie do zapisu usługi sieciowej dla tego katalogu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Utwórz katalog C:\LOGS do rejestrowania wiadomości. Nadaj użytkownikowi uprawnienia do zapisu usługi sieciowej dla tego katalogu.  
  
3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
