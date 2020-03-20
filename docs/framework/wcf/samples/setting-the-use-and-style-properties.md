---
title: Ustawianie przykładów właściwości Użyj i Styl
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144035"
---
# <a name="setting-the-use-and-style-properties"></a>Ustawianie właściwości Use i Style

W tym przykładzie pokazano, jak używać Use <xref:System.ServiceModel.XmlSerializerFormatAttribute> i <xref:System.ServiceModel.DataContractFormatAttribute>Style właściwości na i . Te właściwości wpływają na sposób formatowania wiadomości. Domyślnie treść wiadomości jest sformatowana <xref:System.ServiceModel.OperationFormatStyle.Document>ze stylem ustawionym na . Te ustawienia można określić na poziomie umowy serwisowej lub na poziomie kontraktu operacji.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Właściwość <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style określa sposób formatowania metadanych WSDL dla usługi. Możliwe wartości <xref:System.ServiceModel.OperationFormatStyle.Document>to <xref:System.ServiceModel.OperationFormatStyle.Rpc>, i . RPC oznacza, że reprezentacja WSDL wiadomości wymienianych na operację zawiera parametry tak, jakby było to zdalne wywołanie procedury. Poniżej przedstawiono przykład.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Ustawienie stylu <xref:System.ServiceModel.OperationFormatStyle.Document> oznacza, że reprezentacja WSDL zawiera pojedynczy element, który reprezentuje dokument, który jest wymieniany na operację, jak pokazano w poniższym przykładzie.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

Właściwość <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> określa format wiadomości. Możliwe wartości <xref:System.ServiceModel.OperationFormatUse.Literal> <xref:System.ServiceModel.OperationFormatUse.Encoded>są i ; wartością domyślną jest <xref:System.ServiceModel.OperationFormatUse.Literal>. Literal oznacza, że wiadomość jest dosłownym wystąpieniem schematu w WSDL, jak pokazano w poniższym przykładzie Document/ Literal.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Zakodowane oznacza, że schematy w WSDL są specyfikacje abstrakcyjne, które są zakodowane zgodnie z regułami znalezionymi w soap 1.1 sekcji 5. Poniżej przedstawiono przykład RPC/Encoded.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

Profil podstawowy WS-I 1.0 zabrania <xref:System.ServiceModel.OperationFormatUse.Encoded> używania go i należy go używać tylko wtedy, gdy jest to wymagane przez starsze usługi. Format `Encoded` wiadomości jest dostępny tylko w przypadku korzystania z XmlSerializer.

Aby umożliwić wyświetlanie wysyłanych i odbieranych wiadomości, ten przykład jest oparty na [śledzeniu i rejestrowaniu wiadomości.](tracing-and-message-logging.md) Konfiguracja usługi i kod źródłowy zostały zmodyfikowane, aby włączyć i korzystać z śledzenia i rejestrowania wiadomości. Ponadto <xref:System.ServiceModel.WSHttpBinding> został skonfigurowany bez zabezpieczeń, dzięki czemu rejestrowane wiadomości mogą być wyświetlane w formacie niezaszyfrowanym. Wynikowe dzienniki śledzenia (System.ServiceModel.e2e i Message.log) powinny być przeglądane za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer.exe).](../service-trace-viewer-tool-svctraceviewer-exe.md) Ślady są skonfigurowane do tworzenia w folderze C:\LOGS. Utwórz folder przed uruchomieniem próbki. Aby wyświetlić zawartość wiadomości w narzędziu Podgląd śledzenia, wybierz pozycję **Wiadomości** zarówno w lewym, jak i prawym okienku narzędzia.

Poniższy kod przedstawia umowę <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> serwisową <xref:System.ServiceModel.OperationFormatUse> z właściwością ustawioną na i <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>format treści wiadomości zmienioną z domyślnej na .

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

Aby zobaczyć różnicę między <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> różnymi ustawieniami, zmodyfikuj je w usłudze, ponownie wygeneruj klienta, uruchom próbkę i sprawdź plik c:\logs\message.logs za pomocą narzędzia Podgląd śledzenia usług. Obserwuj również wpływ na metadane, przeglądając `http://localhost/ServiceModelSamples/service.svc?wsdl`. Metadane dla usług są zazwyczaj podzielone na wiele stron. Główna strona wsdl zawiera powiązania WSDL, `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` ale widok do przestrzegania definicji wiadomości.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](one-time-setup-procedure-for-the-wcf-samples.md).

2. Utwórz katalog C:\LOGS do rejestrowania wiadomości. Nadaj użytkownikowi uprawnienia do zapisu usługi sieciowej dla tego katalogu.

3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](building-the-samples.md).

4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](running-the-samples.md).

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
