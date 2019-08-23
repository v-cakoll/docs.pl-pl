---
title: Ustawianie właściwości use i style — przykłady WCF
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 946f8f6aab253eb881faaba7adfdc68dc54d7f0b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958802"
---
# <a name="setting-the-use-and-style-properties"></a>Ustawianie właściwości Use i Style

Ten przykład ilustruje sposób użycia właściwości use i style w <xref:System.ServiceModel.XmlSerializerFormatAttribute> <xref:System.ServiceModel.DataContractFormatAttribute>i. Te właściwości wpływają na sposób formatowania komunikatów. Domyślnie treść komunikatu jest formatowana stylem ustawionym na <xref:System.ServiceModel.OperationFormatStyle.Document>. Te ustawienia można określić na poziomie kontraktu usługi lub na poziomie kontraktu operacji.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Właściwość <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style określa sposób formatowania metadanych WSDL dla usługi. Możliwe wartości to <xref:System.ServiceModel.OperationFormatStyle.Document>, i <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC oznacza, że reprezentacja WSDL komunikatów wymienianych dla operacji zawiera parametry tak, jakby były zdalnego wywołania procedury. Oto przykład.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element reprezentujący dokument wymieniany dla operacji, jak pokazano w poniższym przykładzie.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Właściwość określa format wiadomości. Możliwe wartości to <xref:System.ServiceModel.OperationFormatUse.Literal> i <xref:System.ServiceModel.OperationFormatUse.Encoded>; wartość domyślna to <xref:System.ServiceModel.OperationFormatUse.Literal>. Literał oznacza, że komunikat jest wystąpieniem literału schematu w języku WSDL, jak pokazano w poniższym przykładzie dokumentu/literału.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Zakodowane oznacza, że schematy w języku WSDL są specyfikacjami abstrakcyjnymi, które są kodowane zgodnie z regułami znalezionymi w sekcji SOAP 1,1 sekcja 5. Poniżej znajduje się przykład RPC/Encoded.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

Profil WS-I Basic 1,0 zabrania korzystania z programu <xref:System.ServiceModel.OperationFormatUse.Encoded> i należy go używać tylko wtedy, gdy jest to wymagane przez starsze usługi. Format `Encoded` wiadomości jest dostępny tylko w przypadku korzystania z elementu XmlSerializer.

Aby umożliwić wyświetlanie wysyłanych i odbieranych komunikatów, ten przykład jest oparty na [śledzeniu i rejestrowaniu komunikatów](tracing-and-message-logging.md). Konfiguracja usługi i kod źródłowy zostały zmodyfikowane w celu włączenia śledzenia i rejestrowania komunikatów. Ponadto program <xref:System.ServiceModel.WSHttpBinding> został skonfigurowany bez zabezpieczeń, dlatego zarejestrowane komunikaty można wyświetlać w nieszyfrowanym formacie. Wynikowe dzienniki śledzenia (System. ServiceModel. e2e i Message. log) powinny być przeglądane przy użyciu [narzędzia Podgląd śledzenia usługi (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Ślady są konfigurowane do utworzenia w folderze C:\LOGS. Utwórz folder przed uruchomieniem przykładu. Aby wyświetlić zawartość wiadomości w narzędziu Podgląd śledzenia, wybierz pozycję **komunikaty** w lewym okienku narzędzia.

Poniższy kod <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> przedstawia kontrakt usługi z właściwością ustawioną na <xref:System.ServiceModel.OperationFormatUse> i format treści wiadomości zmienia się z domyślnej <xref:System.ServiceModel.OperationFormatStyle> na <xref:System.ServiceModel.OperationFormatStyle.Document>.

```csharp
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

Aby zobaczyć różnicę między różnymi <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> i <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ustawieniami, zmodyfikuj je w usłudze, ponownie Wygeneruj klienta, uruchom przykład i sprawdź plik c:\logs\Message.Logs za pomocą narzędzia Podgląd śledzenia usługi. Zwróć uwagę na wpływ na metadane przez wyświetlenie `http://localhost/ServiceModelSamples/service.svc?wsdl`. Metadane usług są zwykle podzielone na wiele stron. Główna strona WSDL zawiera powiązania WSDL, ale widok `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` , aby obserwować definicje komunikatów.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Utwórz katalog C:\LOGS na potrzeby rejestrowania komunikatów. Nadaj użytkownikom uprawnienia do zapisu w tym katalogu.

3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
