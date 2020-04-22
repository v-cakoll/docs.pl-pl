---
title: Przegląd klienta programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: b314b61584e45ac5e80a248e639bdac427ba4a57
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021726"
---
# <a name="wcf-client-overview"></a>Omówienie klienta WCF

W tej sekcji opisano, co robią aplikacje klienckie, jak skonfigurować, utworzyć i używać klienta Programu Windows Communication Foundation (WCF) oraz jak zabezpieczyć aplikacje klienckie.  
  
## <a name="using-wcf-client-objects"></a>Korzystanie z obiektów klienta WCF  
 Aplikacja kliencka jest aplikacją zarządzaną, która używa klienta WCF do komunikowania się z inną aplikacją. Tworzenie aplikacji klienckiej dla usługi WCF wymaga następujących kroków:  
  
1. Uzyskaj umowę serwisową, powiązania i informacje adresowe dla punktu końcowego usługi.  
  
2. Utwórz klienta WCF przy użyciu tych informacji.  
  
3. Operacje wywołania.  
  
4. Zamknij obiekt klienta WCF.  
  
W poniższych sekcjach omówiono te kroki i przedstawiono krótkie wprowadzenie do następujących problemów:  
  
- Obsługa błędów.  
  
- Konfigurowanie i zabezpieczanie klientów.  
  
- Tworzenie obiektów wywołania zwrotnego dla usług dupleksu.  
  
- Wywoływanie usług asynchronicznie.  
  
- Wywoływanie usług przy użyciu kanałów klienta.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Uzyskiwanie umowy serwisowej, powiązań i adresów  
 W WCF usług i klientów modelu umów przy użyciu atrybutów zarządzanych, interfejsów i metod. Aby połączyć się z usługą w aplikacji klienckiej, należy uzyskać informacje o typie dla umowy serwisowej. Zazwyczaj informacje o typie umowy serwisowej można uzyskać za pomocą [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe).](servicemodel-metadata-utility-tool-svcutil-exe.md) Narzędzie pobiera metadane z usługi, konwertuje je na plik kodu źródłowego zarządzanego w wybranym języku i tworzy plik konfiguracji aplikacji klienckiej, którego można użyć do skonfigurowania obiektu klienta WCF. Na przykład jeśli zamierzasz utworzyć obiekt klienta WCF `MyCalculatorService`do wywołania , i wiesz, że metadane dla tej usługi są publikowane w , a następnie poniższy `http://computerName/MyCalculatorService/Service.svc?wsdl`przykład kodu pokazuje, jak użyć Svcutil.exe, aby uzyskać `ClientCode.vb` plik, który zawiera umowę serwisową w kodzie zarządzanym.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Można skompilować ten kod umowy do aplikacji klienckiej lub do innego zestawu, którego aplikacja kliencka może następnie użyć do utworzenia obiektu klienta WCF. Za pomocą pliku konfiguracyjnego można skonfigurować obiekt klienta do prawidłowego łączenia się z usługą .  
  
 Na przykład tego procesu zobacz [Jak: Tworzenie klienta](how-to-create-a-wcf-client.md). Aby uzyskać bardziej kompletne informacje o kontraktach, zobacz [Kontrakty](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Tworzenie obiektu klienta WCF  
 Klient WCF jest obiektem lokalnym, który reprezentuje usługę WCF w formularzu, którego klient może używać do komunikowania się z usługą zdalną. Typy klientów WCF implementują docelowy kontrakt serwisowy, więc podczas tworzenia jednego i konfigurowania go, można następnie użyć obiektu klienta bezpośrednio do wywołania operacji usługi. Czas wykonywania WCF konwertuje wywołania metody na wiadomości, wysyła je do usługi, nasłuchuje odpowiedzi i zwraca `out` te `ref` wartości do obiektu klienta WCF jako zwracane wartości lub parametry.  
  
 Można również użyć obiektów kanału klienta WCF do łączenia się z usługami i korzystania z niego. Aby uzyskać szczegółowe informacje, zobacz [Architektura klienta WCF](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Tworzenie nowego obiektu WCF  
 Aby zilustrować użycie <xref:System.ServiceModel.ClientBase%601> klasy, załóżmy, że następująca prosta umowa serwisowa została wygenerowana z aplikacji usługi.  
  
> [!NOTE]
> Jeśli używasz programu Visual Studio do tworzenia klienta WCF, obiekty są ładowane automatycznie do przeglądarki obiektów po dodaniu odwołania usługi do projektu.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Jeśli nie używasz programu Visual Studio, sprawdź wygenerowany kod <xref:System.ServiceModel.ClientBase%601> kontraktu, aby `ISampleService`znaleźć typ, który rozszerza się i interfejs umowy serwisowej . W takim przypadku ten typ wygląda następująco:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tę klasę można utworzyć jako obiekt lokalny przy użyciu jednego z konstruktorów, skonfigurowany, a następnie używany do łączenia się z usługą typu `ISampleService`.  
  
 Zaleca się, aby najpierw utworzyć obiekt klienta WCF, a następnie użyć go i zamknąć go wewnątrz jednego bloku try/catch. Nie należy używać `using` instrukcji`Using` ( w języku Visual Basic), ponieważ może maskować wyjątki w niektórych trybach awarii. Aby uzyskać więcej informacji, zobacz poniższe sekcje, a także [Użyj zamknij i Przerwij, aby zwolnić zasoby klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Kontrakty, powiązania i adresy  
 Przed utworzeniem obiektu klienta WCF należy skonfigurować obiekt klienta. W szczególności musi mieć *punkt końcowy* usługi do użycia. Punkt końcowy jest kombinacją umowy serwisowej, powiązania i adresu. (Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Punkty końcowe: Adresy, powiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Zazwyczaj te informacje znajdują się w [ \<punkcie końcowym>](../configure-apps/file-schema/wcf/endpoint-of-client.md) element w pliku konfiguracji aplikacji klienckiej, takich jak narzędzie Svcutil.exe generuje i jest ładowany automatycznie podczas tworzenia obiektu klienta. Oba typy klientów WCF mają również przeciążenia, które umożliwiają programowe określenie tych informacji.  
  
 Na przykład wygenerowany plik `ISampleService` konfiguracyjny dla używanego w poprzednich przykładach zawiera następujące informacje o punkcie końcowym.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Ten plik konfiguracyjny określa `<client>` docelowy punkt końcowy w elemencie. Aby uzyskać więcej informacji na temat korzystania <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> z <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> wielu punktów końcowych docelowych, zobacz lub konstruktorów.  
  
## <a name="calling-operations"></a>Operacje wywoływania  
 Po utworzeniu i skonfigurowaniu obiektu klienta utwórz blok try/catch, wywołaj operacje w taki sam sposób, jak w przypadku obiektu lokalnego, i zamknij obiekt klienta WCF. Gdy aplikacja kliencka wywołuje pierwszą operację, WCF automatycznie otwiera podstawowy kanał, a kanał bazowy jest zamykany, gdy obiekt jest odtworzeny. (Alternatywnie można również jawnie otworzyć i zamknąć kanał przed lub po wywołaniu innych operacji).  
  
 Na przykład, jeśli masz następującą umowę serwisową:  
  
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
  
 Operacje można wywołać, tworząc obiekt klienta WCF i wywołując jego metody, jak pokazano w poniższym przykładzie kodu. Otwieranie, wywoływanie i zamykanie obiektu klienta WCF występuje w ramach jednego bloku try/catch. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usług przy użyciu klienta WCF](./feature-details/accessing-services-using-a-client.md) i [użyj zamknij i przerwij, aby zwolnić zasoby klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Obsługa błędów  
 Wyjątki mogą wystąpić w aplikacji klienckiej podczas otwierania bazowego kanału klienta (jawnie lub automatycznie przez wywołanie operacji), przy użyciu obiektu klienta lub kanału do wywoływania operacji lub podczas zamykania bazowego kanału klienta. Zaleca się co najmniej, że aplikacje <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> oczekują do obsługi <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> możliwe <xref:System.TimeoutException?displayProperty=nameWithType> i wyjątki oprócz wszelkich obiektów zgłaszanych w wyniku błędów PROTOKOŁU SOAP zwracanych przez operacje. Błędy protokołu SOAP określone w umowie operacji są <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> wywoływane do aplikacji klienckich jako parametr typu jest typem szczegółowym błędu PROTOKOŁU SOAP. Aby uzyskać więcej informacji na temat obsługi warunków błędów w aplikacji klienckiej, zobacz [Wysyłanie i odbieranie błędów](sending-and-receiving-faults.md). Aby uzyskać pełny przykład pokazuje, jak obsługiwać błędy w kliencie, zobacz [Oczekiwane wyjątki](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurowanie i zabezpieczanie klientów  
 Konfigurowanie klienta rozpoczyna się od wymaganego ładowania informacji o docelowym punkcie końcowym dla obiektu klienta lub kanału, zwykle z pliku konfiguracji, chociaż można również załadować te informacje programowo przy użyciu konstruktorów klienta i właściwości. Jednak dodatkowe kroki konfiguracji są wymagane, aby włączyć pewne zachowanie klienta i dla wielu scenariuszy zabezpieczeń.  
  
 Na przykład wymagania dotyczące zabezpieczeń dla umów serwisowych są zadeklarowane w interfejsie umowy serwisowej, a jeśli program Svcutil.exe utworzył plik konfiguracyjny, ten plik zwykle zawiera powiązanie, które może obsługiwać wymagania dotyczące zabezpieczeń usługi. W niektórych przypadkach może być jednak wymagana większa konfiguracja zabezpieczeń, na przykład konfigurowanie poświadczeń klienta. Aby uzyskać pełne informacje na temat konfiguracji zabezpieczeń dla klientów WCF, zobacz [Zabezpieczanie klientów](securing-clients.md).  
  
 Ponadto niektóre niestandardowe modyfikacje mogą być włączone w aplikacjach klienckich, takich jak niestandardowe zachowania w czasie wykonywania. Aby uzyskać więcej informacji na temat konfigurowania niestandardowego zachowania klienta, zobacz [Konfigurowanie zachowań klientów](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Tworzenie obiektów wywołania zwrotnego dla usług dupleksu  
 Usługi dupleksu określają umowę wywołania zwrotnego, którą aplikacja kliencka musi zaimplementować w celu zapewnienia obiektu wywołania zwrotnego dla usługi, aby wywołać zgodnie z wymaganiami umowy. Chociaż obiekty wywołania zwrotnego nie są pełne usługi (na przykład nie można zainicjować kanał z obiektu wywołania zwrotnego), na potrzeby implementacji i konfiguracji mogą być traktowane jako rodzaj usługi.  
  
 Klienci usług dupleksowych muszą:  
  
- Zaimplementuj klasę kontraktu wywołania zwrotnego.  
  
- Utwórz wystąpienie klasy implementacji kontraktu wywołania <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> zwrotnego i użyj go do utworzenia obiektu, który jest przekazytywnie do konstruktora klienta WCF.  
  
- Wywołaj operacje i obsłużyć wywołania zwrotne operacji.  
  
 Obiekty klienta Dupleksu WCF działają podobnie jak ich odpowiedniki niespodzielone, z wyjątkiem tego, że udostępniają one funkcje niezbędne do obsługi wywołań zwrotnych, w tym konfigurację usługi wywołania zwrotnego.  
  
 Na przykład można kontrolować różne aspekty zachowania środowiska uruchomieniowego obiektu <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> wywołania zwrotnego przy użyciu właściwości atrybutu w klasie wywołania zwrotnego. Innym przykładem jest <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> użycie klasy, aby włączyć zwracanie informacji o wyjątku do usług, które wywołują obiekt wywołania zwrotnego. Aby uzyskać więcej informacji, zobacz [Usługi dupleksu](./feature-details/duplex-services.md). Aby uzyskać pełną próbkę, zobacz [Dupleks](./samples/duplex.md).  
  
 Na komputerach z systemem Windows XP z internetowymi usługami informacyjnymi (IIS) <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 5.1 klienci dupleksu muszą określić adres podstawowy klienta przy użyciu klasy lub zostanie zgłoszony wyjątek. Poniższy przykład kodu pokazuje, jak to zrobić w kodzie.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Poniższy kod pokazuje, jak to zrobić w pliku konfiguracyjnym  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Asynchronicznie wywoływanie usług  
 Jak operacje są wywoływane jest całkowicie do dewelopera klienta. Jest tak, ponieważ komunikaty, które tworzą operację mogą być mapowane do metod synchronicznych lub asynchronicznych, gdy wyrażone w kodzie zarządzanym. W związku z tym jeśli chcesz utworzyć klienta, który wywołuje operacje asynchronicznie, można użyć Svcutil.exe `/async` do generowania kodu klienta asynchronicznie przy użyciu opcji. Aby uzyskać więcej informacji, zobacz [Jak: Wywołanie operacji usługi Asynchronicznie](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Wywoływanie usług przy użyciu kanałów klienta WCF  
 Typy klientów WCF <xref:System.ServiceModel.ClientBase%601>rozszerzają <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> , który sam wywodzi się z interfejsu, aby udostępnić podstawowy system kanałów. Usługi można wywołać przy użyciu docelowego <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> kontraktu serwisowego z klasą. Aby uzyskać szczegółowe informacje, zobacz [Architektura klienta WCF](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
