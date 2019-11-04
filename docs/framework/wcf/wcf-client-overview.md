---
title: Przegląd klienta programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 180de3f571426441155a19b98ab750fcdbb3888e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420656"
---
# <a name="wcf-client-overview"></a>Przegląd klienta programu WCF
W tej sekcji opisano, jakie aplikacje klienckie, jak konfigurować, tworzyć i korzystać z klienta Windows Communication Foundation (WCF) oraz jak zabezpieczać aplikacje klienckie.  
  
## <a name="using-wcf-client-objects"></a>Korzystanie z obiektów klienta WCF  
 Aplikacja kliencka to zarządzana aplikacja, która używa klienta WCF do komunikowania się z inną aplikacją. Aby utworzyć aplikację kliencką dla usługi WCF, należy wykonać następujące czynności:  
  
1. Uzyskaj kontrakt usługi, powiązania i informacje o adresie dla punktu końcowego usługi.  
  
2. Utwórz klienta WCF przy użyciu tych informacji.  
  
3. Wywołania operacji.  
  
4. Zamknij obiekt klienta WCF.  
  
 W poniższych sekcjach omówiono te kroki i przedstawiono krótkie wprowadzenie do następujących problemów:  
  
- Obsługa błędów.  
  
- Konfigurowanie i Zabezpieczanie klientów.  
  
- Tworzenie obiektów wywołania zwrotnego dla usług dupleksowych.  
  
- Asynchroniczne wywoływanie usług.  
  
- Wywoływanie usług przy użyciu kanałów klienta.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Uzyskiwanie kontraktu, powiązań i adresów usługi  
 W programie WCF, usługi i klienci modelują kontrakty przy użyciu atrybutów zarządzanych, interfejsów i metod. Aby nawiązać połączenie z usługą w aplikacji klienckiej, należy uzyskać informacje o typie dla kontraktu usługi. Zazwyczaj można to zrobić za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), które pobiera metadane z usługi, konwertuje je na plik zarządzanego kodu źródłowego w wybranym języku i tworzy plik konfiguracji aplikacji klienckiej. za pomocą programu można skonfigurować obiekt klienta WCF. Na przykład jeśli zamierzasz utworzyć obiekt klienta WCF w celu wywołania `MyCalculatorService` i wiesz, że metadane dla tej usługi są publikowane w `http://computerName/MyCalculatorService/Service.svc?wsdl`, Poniższy przykład kodu pokazuje, jak używać programu Svcutil. exe do uzyskania pliku `ClientCode.vb` zawierającego usługę kontrakt w kodzie zarządzanym.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Możesz skompilować ten kod kontraktu do aplikacji klienckiej lub do innego zestawu, którego aplikacja kliencka może następnie użyć do utworzenia obiektu klienta WCF. Możesz użyć pliku konfiguracji, aby skonfigurować obiekt klienta do prawidłowego połączenia z usługą.  
  
 Przykład tego procesu można znaleźć w temacie [How to: Create an Client](how-to-create-a-wcf-client.md). Aby uzyskać więcej informacji na temat umów, zobacz [kontrakt](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Tworzenie obiektu klienta WCF  
 Klient WCF jest obiektem lokalnym, który reprezentuje usługę WCF w formie, z której może korzystać klient do komunikowania się z usługą zdalną. Typy klientów WCF implementują kontrakt usługi docelowej, dlatego po jego utworzeniu i skonfigurowaniu można użyć obiektu klienta bezpośrednio do wywołania operacji usługi. Czas wykonywania WCF konwertuje metodę wywołań na komunikaty, wysyła je do usługi, nasłuchuje odpowiedzi i zwraca te wartości do obiektu klienta WCF jako wartości zwracane lub `out` lub `ref` parametrów.  
  
 Za pomocą obiektów kanału klienta WCF można także łączyć się z usługami i korzystać z nich. Aby uzyskać szczegółowe informacje, zobacz [Architektura klienta WCF](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Tworzenie nowego obiektu WCF  
 Aby zilustrować użycie klasy <xref:System.ServiceModel.ClientBase%601>, założono, że w aplikacji usługi został wygenerowany następujący prosty kontrakt usługi.  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio do utworzenia klienta WCF, obiekty są ładowane automatycznie do przeglądarki obiektów po dodaniu do projektu odwołania do usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Jeśli nie używasz programu Visual Studio, sprawdź wygenerowany kod kontraktu, aby znaleźć typ, który rozszerza <xref:System.ServiceModel.ClientBase%601> i `ISampleService`interfejs kontraktu usługi. W tym przypadku ten typ wygląda podobnie do następującego kodu:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Ta klasa może być tworzona jako obiekt lokalny przy użyciu jednego z konstruktorów, skonfigurowany, a następnie używany do nawiązywania połączenia z usługą typu `ISampleService`.  
  
 Zalecane jest, aby najpierw utworzyć obiekt klienta WCF, a następnie użyć go i zamknąć wewnątrz pojedynczego bloku try/catch. Nie należy używać instrukcji `using` (`Using` w Visual Basic), ponieważ może ona maskować wyjątki w pewnych trybach awarii. Aby uzyskać więcej informacji, zapoznaj się z następującymi sekcjami, [a także Użyj Zamknij i Przerwij, aby zwolnić zasoby klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Kontrakty, powiązania i adresy  
 Aby można było utworzyć obiekt klienta WCF, należy skonfigurować obiekt Client. W każdym przypadku musi on mieć *punkt końcowy* usługi do użycia. Punkt końcowy to kombinacja kontraktu usługi, powiązania i adresu. (Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [punkty końcowe: adresy, powiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md)). Zazwyczaj te informacje znajdują się w elemencie [\<endpoint >](../configure-apps/file-schema/wcf/endpoint-of-client.md) w pliku konfiguracyjnym aplikacji klienta, na przykład w ramach narzędzia Svcutil. exe, które generuje i jest ładowany automatycznie podczas tworzenia obiektu klienckiego. Oba typy klientów programu WCF mają również przeciążenia, które umożliwiają programistyczne Określanie tych informacji.  
  
 Na przykład wygenerowany plik konfiguracyjny dla `ISampleService` użyty w powyższych przykładach zawiera następujące informacje o punkcie końcowym.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Ten plik konfiguracji określa docelowy punkt końcowy w elemencie `<client>`. Aby uzyskać więcej informacji o używaniu wielu docelowych punktów końcowych, zobacz <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> konstruktorów.  
  
## <a name="calling-operations"></a>Operacje wywołujące  
 Po utworzeniu i skonfigurowaniu obiektu klienckiego Utwórz blok try/catch, a następnie Wywołaj operacje w taki sam sposób, jak gdyby obiekt był lokalny, i Zamknij obiekt klienta WCF. Gdy aplikacja kliencka wywołuje pierwszą operację, usługa WCF automatycznie otwiera podstawowy kanał, a kanał źródłowy jest zamykany podczas odtwarzania obiektu. (Alternatywnie można również jawnie otworzyć i zamknąć kanał przed wywołaniem innych operacji lub po nim.)  
  
 Na przykład jeśli masz następujący kontrakt usługi:  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
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
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 Możesz wywołać operacje, tworząc obiekt klienta WCF i wywołując jego metody, jak pokazano w poniższym przykładzie kodu. Należy zauważyć, że otwieranie, wywoływanie i zamykanie obiektu klienta WCF odbywa się w jednym bloku try/catch. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług za pomocą klienta WCF](./feature-details/accessing-services-using-a-client.md) i [Używanie funkcji Close i Abort w celu zwolnienia zasobów klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Obsługa błędów  
 Wyjątki mogą wystąpić w aplikacji klienckiej podczas otwierania bazowego kanału klienta (bez względu na to, czy jest to jawnie czy automatycznie przez wywołanie operacji), przy użyciu obiektu klienta lub kanału do wywoływania operacji lub podczas zamykania bazowego kanału klienta. Zaleca się, aby aplikacje, które oczekują w obsłudze ewentualnych wyjątków <xref:System.TimeoutException?displayProperty=nameWithType> i <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, oprócz wszystkich obiektów <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> zgłaszanych w wyniku błędów SOAP zwracanych przez operacje. Błędy SOAP określone w kontrakcie operacji są zgłaszane do aplikacji klienckich jako <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>, gdzie parametr typu jest typem szczegółowym błędu SOAP. Aby uzyskać więcej informacji na temat obsługi błędów w aplikacji klienckiej, zobacz [wysyłanie i otrzymywanie błędów](sending-and-receiving-faults.md). Pełny przykład pokazuje, jak obsłużyć błędy w kliencie, zobacz [oczekiwane wyjątki](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurowanie i Zabezpieczanie klientów  
 Konfigurowanie klienta programu rozpoczyna się od wymaganego ładowania informacji o docelowym punkcie końcowym dla obiektu klienta lub kanału, zazwyczaj z pliku konfiguracji, chociaż można również ładować te informacje programowo przy użyciu konstruktorów i właściwości klienta. Należy jednak wykonać dodatkowe czynności konfiguracyjne, aby włączyć określone zachowanie klienta i wiele scenariuszy zabezpieczeń.  
  
 Na przykład wymagania dotyczące zabezpieczeń dla kontraktów usług są deklarowane w interfejsie kontraktu usługi, a plik konfiguracji programu Svcutil. exe został utworzony w celu zapewnienia obsługi wymagań dotyczących zabezpieczeń usługi. Jednak w niektórych przypadkach może być wymagana większa Konfiguracja zabezpieczeń, na przykład skonfigurowanie poświadczeń klienta. Aby uzyskać pełne informacje na temat konfiguracji zabezpieczeń dla klientów programu WCF, zobacz [Zabezpieczanie klientów](securing-clients.md).  
  
 Ponadto niektóre modyfikacje niestandardowe można włączyć w aplikacjach klienckich, takich jak niestandardowe zachowania w czasie wykonywania. Aby uzyskać więcej informacji na temat konfigurowania zachowania klienta niestandardowego, zobacz [Konfigurowanie zachowań klienta](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Tworzenie obiektów wywołania zwrotnego dla usług dupleks  
 Usługi dupleksowe określają kontrakt wywołania zwrotnego, który musi zostać zaimplementowany przez aplikację kliencką w celu zapewnienia obiektowi wywołania zwrotnego dla usługi zgodnie z wymaganiami kontraktu. Mimo że obiekty wywołania zwrotnego nie są pełnymi usługami (na przykład nie można zainicjować kanału z obiektem wywołania zwrotnego), na potrzeby implementacji i konfiguracji można traktować ich jako rodzaj usługi.  
  
 Klienci usług dupleksowych muszą:  
  
- Zaimplementuj klasę kontraktu wywołania zwrotnego.  
  
- Utwórz wystąpienie klasy implementacji kontraktu wywołania zwrotnego i użyj jej do utworzenia obiektu <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> przekazanego do konstruktora klienta WCF.  
  
- Wywołaj operacje i obsługują wywołania zwrotne operacji.  
  
 Obiekty klienta WCF w trybie dupleksu działają podobnie jak ich odpowiedniki niedupleksowe, z wyjątkiem tego, że uwidaczniają funkcje niezbędne do obsługi wywołań zwrotnych, w tym konfiguracji usługi wywołania zwrotnego.  
  
 Na przykład można kontrolować różne aspekty zachowania środowiska uruchomieniowego obiektów wywołania zwrotnego przy użyciu właściwości <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> atrybutu dla klasy wywołania zwrotnego. Innym przykładem jest użycie klasy <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> w celu włączenia powrotu informacji o wyjątku do usług wywołujących obiekt wywołania zwrotnego. Aby uzyskać więcej informacji, zobacz [usługi dupleksowe](./feature-details/duplex-services.md). Aby uzyskać pełny przykład, zobacz [Duplex](./samples/duplex.md).  
  
 Na komputerach z systemem Windows XP z Internet Information Services (IIS) 5,1 klienci dupleksowi muszą określić adres podstawowy klienta przy użyciu klasy <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> lub zostanie zgłoszony wyjątek. Poniższy przykład kodu pokazuje, jak to zrobić w kodzie.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Poniższy kod pokazuje, jak to zrobić w pliku konfiguracji  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Asynchroniczne wywoływanie usług  
 Sposób wywoływania operacji jest całkowicie do dewelopera klienta. Wynika to z faktu, że komunikaty wchodzące w skład operacji można zamapować na metody synchroniczne lub asynchroniczne, gdy wyrażasz w kodzie zarządzanym. W związku z tym, jeśli chcesz skompilować klienta, który wywołuje operacje asynchronicznie, możesz użyć programu Svcutil. exe do generowania kodu klienta asynchronicznego przy użyciu opcji `/async`. Aby uzyskać więcej informacji, zobacz [jak: wywołania operacji usługi asynchronicznej](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Wywoływanie usług przy użyciu kanałów klienta WCF  
 Typy klientów WCF rozszerzając <xref:System.ServiceModel.ClientBase%601>, które same pochodzą z interfejsu <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>, aby uwidocznić podstawowy system kanałów. Możesz wywoływać usługi przy użyciu kontraktu usługi docelowej z klasą <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Aby uzyskać szczegółowe informacje, zobacz [Architektura klienta WCF](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
