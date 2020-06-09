---
title: Błędy klasy XmlSerializer
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: ce5aa6d2c579d4776f9505ae694768203e48eecf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584067"
---
# <a name="xmlserializer-faults"></a>Błędy klasy XmlSerializer
<xref:System.Xml.Serialization.XmlSerializer>Przykładowa umowa dotycząca błędu demonstruje sposób przekazywania informacji o błędach z usługi do klienta przy użyciu programu <xref:System.Xml.Serialization.XmlSerializer> . Przykład jest oparty na [wprowadzenie](getting-started-sample.md), z dodatkowym kodem dodanym do usługi w celu przekonwertowania wewnętrznego wyjątku na błąd. Klient próbuje wykonać dzielenie przez zero w celu wymuszenia błędu w usłudze.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt kalkulatora został zmodyfikowany w taki sposób, aby zawierał element <xref:System.ServiceModel.FaultContractAttribute> , jak pokazano w poniższym przykładowym kodzie. Ponadto, służy <xref:System.ServiceModel.XmlSerializerFormatAttribute> do włączania serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> . <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>Właściwość jest ustawiona na `true` dla tego atrybutu, co powoduje, że serializator używa do <xref:System.Xml.Serialization.XmlSerializer> odczytu i zapisu błędów.  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
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
  
 Podczas generowania kodu dla serwera proxy klienta należy zastosować flagę **/UseSerializerForFaults** do [Narzędzia Narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
