---
title: "Błędy klasy XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17fa7da04cd0787577b419c1c9fa3dfc0bc733d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xmlserializer-faults"></a>Błędy klasy XmlSerializer
<xref:System.Xml.Serialization.XmlSerializer> Błąd kontraktu przykładzie pokazano, jak do komunikowania się informacje o błędzie z usługi do klienta przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), niektóre dodatkowy kod dodane do usługi, aby przekonwertować wyjątek wewnętrzny błąd. Klient próbuje wykonać dzielenie przez zero, aby wymusić warunek błędu usługi.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kontrakt Kalkulator został zmodyfikowany w celu obejmują <xref:System.ServiceModel.FaultContractAttribute> jak pokazano w poniższym kodzie próbki. Ponadto <xref:System.ServiceModel.XmlSerializerFormatAttribute> służy do włączania serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> Właściwość jest ustawiona na `true` dla tego atrybutu, który powoduje, że serializator do użycia <xref:System.Xml.Serialization.XmlSerializer> do odczytywania i zapisywania błędów.  
  
```  
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
  
 Podczas generowania kodu dla serwera proxy klienta, należy najpierw zastosować **/UseSerializerForFaults** flaga [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute>  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
