---
title: Ustawianie właściwości Use i Style
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: c4cee5fac84d8fb47565cc4ebde47f04365b989e
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836855"
---
# <a name="setting-the-use-and-style-properties"></a>Ustawianie właściwości Use i Style
W tym przykładzie pokazano, jak korzystać z właściwości Use i Style na <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>. Te właściwości mają wpływ na sposób sformatowanych wiadomości. Domyślnie, treść komunikatu jest sformatowany przy użyciu stylu równa <xref:System.ServiceModel.OperationFormatStyle.Document>. Te ustawienia można określić na poziomie kontraktu usługi lub poziomu kontrakt operacji.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Właściwość stylu określa sposób formatowania metadanych WSDL usługi. Możliwe wartości to <xref:System.ServiceModel.OperationFormatStyle.Document>, i <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC oznacza, że reprezentacja WSDL komunikatów wymienianych operacji zawiera parametry, tak jakby zdalnego wywołania procedury. Oto przykład.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element, który reprezentuje dokument, który są wymieniane dla danej operacji, jak pokazano w poniższym przykładzie.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Właściwość określa format wiadomości. Możliwe wartości to <xref:System.ServiceModel.OperationFormatUse.Literal> i <xref:System.ServiceModel.OperationFormatUse.Encoded>; wartość domyślna to <xref:System.ServiceModel.OperationFormatUse.Literal>. Literał oznacza, że komunikat jest literału wystąpienia schematu w formacie WSDL, jak pokazano w następującym dokumencie / literału przykładu.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 Zakodowany oznacza, że schematy w formacie WSDL są abstrakcyjne specyfikacje, które są zakodowane zgodnie z regułami w SOAP 1.1 sekcji 5. Oto przykład RPC/zakodowane.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 WS-I Basic 1.0 profilu zabraniają używania <xref:System.ServiceModel.OperationFormatUse.Encoded> i należy używać tylko ją, gdy jest to wymagane przez starszej wersji usługi. `Encoded` Format komunikatu jest dostępna tylko, gdy za pomocą elementu XmlSerializer.  
  
 Aby umożliwić wyświetlanie komunikatów wysyłanych i odbieranych, ten przykład jest oparty na [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). Aby włączyć i wykorzystywać śledzenie i rejestrowanie komunikatów zostały zmodyfikowane konfiguracji usługi i kod źródłowy. Ponadto <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> została skonfigurowana bez bezpieczeństwa dlatego zarejestrowane komunikaty mogą być wyświetlane w postaci niezaszyfrowanej. Wynikowy dzienniki śledzenia (System.ServiceModel.e2e i Message.log) powinna być przeglądana przy użyciu [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Ślady są skonfigurowane do utworzony w folderze C:\LOGS. Utwórz folder przed uruchomieniem przykładu. Zaznacz, aby wyświetlić zawartość wiadomości za pomocą narzędzia podglądu śledzenia **wiadomości** zarówno po lewej stronie, jak i prawego okienka narzędzia.  
  
 Poniższy kod przedstawia kontraktu usługi o <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> właściwością <xref:System.ServiceModel.OperationFormatUse> i format treści wiadomości, zmienić domyślną opcję <xref:System.ServiceModel.OperationFormatStyle> do <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,   
                                 Use = OperationFormatUse.Encoded)]  
public interface IUseAndStyleCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Aby zobaczyć różnicę między różnymi <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> i <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ustawienia, zmodyfikuj je w usłudze, ponownie wygenerować klienta, uruchom aplikację przykładową i zapoznaj się z plikiem c:\logs\message.logs za pomocą narzędzia przeglądarki danych śledzenia usługi. Również obserwować wpływ na metadane, wyświetlając `http://localhost/ServiceModelSamples/service.svc?wsdl`. Metadane dla usług jest zazwyczaj dzielone na wielu stronach. Na stronie głównej wsdl zawiera powiązania WSDL, ale wyświetlać `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` do obserwowania definicje wiadomości.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Zobacz też
