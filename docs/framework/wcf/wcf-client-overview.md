---
title: Przegląd klienta programu WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 5cb73dfeaac4f1c23724dc71b0f1f5d07fd28b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791238"
---
# <a name="wcf-client-overview"></a>Przegląd klienta programu WCF
W tej sekcji opisano działanie aplikacji klienckich, jak konfigurować, tworzenie i używanie klienta programu Windows Communication Foundation (WCF) oraz sposób zabezpieczania aplikacji klienckich.  
  
## <a name="using-wcf-client-objects"></a>Używanie obiektów klienta WCF  
 Aplikacja kliencka jest zarządzanej aplikacji, która używa klienta programu WCF do komunikowania się z inną aplikacją. Można utworzyć klienta aplikacji dla usługi WCF wymaga wykonania następujących czynności:  
  
1. Uzyskaj kontraktu usługi, powiązania i informacje o adresie dla punktu końcowego usługi.  
  
2. Utworzenie klienta WCF, za pomocą tych informacji.  
  
3. Wywoływanie operacji.  
  
4. Zamknij obiektu klienta programu WCF.  
  
 W poniższych sekcjach omówiono te kroki i podaj krótkie instrukcje na następujące zagadnienia:  
  
- Obsługa błędów.  
  
- Konfigurowanie i Zabezpieczanie klientów.  
  
- Tworzenie obiektów wywołania zwrotnego dla usługi dwukierunkowe.  
  
- Asynchroniczne wywoływanie usługi.  
  
- Wywoływanie usług za pomocą klienta kanałów.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Uzyskaj kontraktu usługi, powiązań i adresów  
 W programie WCF usług i klientów modelu zamówień za pomocą atrybutów zarządzanych, interfejsy i metody. Aby połączyć się z usługą w aplikacji klienckiej, należy uzyskać informacje o typie dla kontraktu usługi. Zazwyczaj można to zrobić za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), co spowoduje pobranie metadanych z usługi, konwertuje go na plik kodu źródłowego zarządzanych w wybranym języku i tworzy klienta plik konfiguracji aplikacji umożliwiają skonfigurowanie obiektu klienta programu WCF. Na przykład, jeśli zamierzasz utworzyć obiekt klienta WCF do wywoływania `MyCalculatorService`, a wiadomo, że metadane dla tej usługi zostanie opublikowana w `http://computerName/MyCalculatorService/Service.svc?wsdl`, a następnie poniższy przykład kodu pokazuje sposób użycia Svcutil.exe w celu uzyskania `ClientCode.vb` pliku, który zawiera kontrakt usługi w kodzie zarządzanym.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Albo można skompilować ten kod umowy, w aplikacji klienckiej lub w innym zestawie, który aplikacja kliencka może następnie użyć do utworzenia obiektu klienta programu WCF. Plik konfiguracji umożliwiają skonfigurowanie obiektu klienta, aby właściwie się z usługą.  
  
 Na przykład ten proces zobacz [jak: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Aby uzyskać bardziej szczegółowe informacje na temat umów zobacz [umów](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Utworzenie obiektu klienta programu WCF  
 Klienta programu WCF jest obiekt lokalny reprezentujący usługi WCF w formularzu, który klient może używać do komunikowania się z usługi zdalnej. Typy klienta WCF implementować docelową usługę kontraktu, dzięki czemu podczas utworzyć i skonfigurować go, następnie można użyć obiektu klienta bezpośrednio do wywołania operacji usługi. Usługi WCF, czas wykonywania konwertuje wywołania metody do wiadomości, wysyła je do usługi, będzie nasłuchiwać pod kątem odpowiedzi i zwraca te wartości do obiektu klienta programu WCF jako wartości zwracane lub `out` lub `ref` parametrów.  
  
 Umożliwia także obiekty kanału klienta programu WCF do nawiązywania połączeń z i korzystania z usług. Aby uzyskać więcej informacji, zobacz [Architektura klienta programu WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Utworzenie nowego obiektu programu WCF  
 Aby zilustrować użytkowania <xref:System.ServiceModel.ClientBase%601> klasy, założono następujące kontraktu usługi simple został wygenerowany z aplikacją usługi.  
  
> [!NOTE]
>  Jeśli używasz programu Visual Studio do utworzenia klienta WCF, obiekty są ładowane automatycznie do przeglądarki obiektów po dodaniu do projektu odwołanie do usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Jeśli nie używasz programu Visual Studio, sprawdź generowanego kodu kontraktu można znaleźć typu, która rozszerza <xref:System.ServiceModel.ClientBase%601> i interfejsu kontraktu usługi `ISampleService`. W tym przypadku tego typu wygląda podobnie do poniższego kodu:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Ta klasa można tworzyć jako obiekt lokalny przy użyciu jednego z konstruktorów, skonfigurować i następnie używane do łączenia się z usługą typu `ISampleService`.  
  
 Zalecane jest, że najpierw utwórz obiekt klienta WCF i następnie użyć go i zamknij go wewnątrz bloku try/catch w jednym. Nie należy używać `using` — instrukcja (`Using` w języku Visual Basic), ponieważ jego może maskować wyjątki, w niektórych trybów awarii. Aby uzyskać więcej informacji, zobacz następujące sekcje także [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Adresy, powiązania i kontrakty  
 Przed utworzeniem obiektu klienta WCF, należy skonfigurować obiekt klienta. W szczególności muszą oferować usługę *punktu końcowego* do użycia. Punkt końcowy jest kombinacją kontraktu usługi, powiązanie i adres. (Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [punktów końcowych: Adresy, powiązania i kontrakty](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Zazwyczaj te informacje znajdują się w [ \<punktu końcowego >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) elementu w pliku konfiguracji aplikacji klienta, takiego jak narzędzia Svcutil.exe generuje i ładowane automatycznie po utworzeniu klienta obiekt. Oba typy klienta WCF mają również przeciążenia, które umożliwiają programowo podać te informacje.  
  
 Na przykład plik konfiguracji wygenerowany dla `ISampleService` używane w poprzednim przykłady zawiera następujące informacje o punkcie końcowym.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Ten plik konfiguracji nie określa docelowy punkt końcowy w `<client>` elementu. Aby uzyskać więcej informacji o korzystaniu z wieloma docelowymi punktami końcowymi, zobacz <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> konstruktorów.  
  
## <a name="calling-operations"></a>Podczas wywoływania operacji  
 Po ma obiektu klienta utworzone i skonfigurowane, Tworzenie bloku try/catch, wywoływanie operacji w taki sam sposób, jak gdyby lokalnego obiektu i zamknij obiektu klienta programu WCF. Gdy aplikacja kliencka wywołuje pierwszą operacją, WCF, automatycznie otwiera kanału źródłowego i kanału źródłowego jest zamykane, gdy obiekt zostanie odtworzona. (Ewentualnie można także jawnie Otwórz i zamknij kanał przed lub po innych operacji podczas wywoływania.)  
  
 Na przykład, jeśli masz następujące kontraktu usługi:  
  
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
  
 Można wywołać operacji przez utworzenie obiektu klienta programu WCF i wywoływania jego metody, jak w poniższym przykładzie kodu pokazano. Należy pamiętać, otwieranie, połączeń i zamknięcia obiektu klienta programu WCF występowanie w bloku try/catch w jednym. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) i [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Obsługa błędów  
 Wyjątki mogą wystąpić w aplikacji klienckiej, gdy klient źródłowy otwierania kanału (czy jawnie lub automatycznie przez wywołanie operacji), przy użyciu obiektu klienta lub kanał do wywoływania operacji, lub podczas zamykania kanału źródłowego klienta. Zalecane jest co najmniej aplikacji chcą obsługi możliwe <xref:System.TimeoutException?displayProperty=nameWithType> i <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> wyjątki dodatek do wszelkich <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów zgłoszony wyniku błędach SOAP zwracanych przez operacje. Błędach SOAP określona w umowie operacji są wywoływane dla aplikacji klienckich jako <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> gdzie parametr typu jest typem szczegółów błędu protokołu SOAP. Aby uzyskać więcej informacji na temat obsługi błędów w aplikacji klienckiej, zobacz [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md). Aby uzyskać kompletny przykładowy pokazuje sposób obsługi błędów w kliencie WPF, zobacz [oczekiwane wyjątki](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurowanie i Zabezpieczanie klientów  
 Konfigurowanie klienta rozpoczyna się od wymagane ładowanie informacji o punkcie końcowym docelowego dla obiektu klienta lub kanał, zwykle z pliku konfiguracji, mimo że można również załadować te informacje, w sposób programowy za pomocą klienta konstruktorów i właściwości. Jednak wykonanie dodatkowych kroków konfiguracji są wymagane do włączenia określone zachowanie klienta i umożliwia obsługę wielu scenariuszy zabezpieczeń.  
  
 Na przykład wymagania dotyczące zabezpieczeń dla kontraktów usług są deklarowane przy użyciu interfejsu kontraktu usługi, a jeśli Svcutil.exe utworzony plik konfiguracji, ten plik zawiera zazwyczaj powiązania, który może obsługiwać wymagania dotyczące zabezpieczeń usługi. W niektórych przypadkach jednak większej liczby czynności konfiguracyjnych zabezpieczeń może być wymagane, na przykład konfigurowania poświadczeń klienta. Aby uzyskać pełne informacje na temat konfiguracji zabezpieczeń dla klientów usługi WCF, zobacz [Zabezpieczanie klientów](../../../docs/framework/wcf/securing-clients.md).  
  
 Ponadto niektóre modyfikacji niestandardowych można włączyć w aplikacjach klienckich, takich jak niestandardowe zachowania w czasie wykonywania. Aby uzyskać więcej informacji o sposobie konfigurowania zachowania klientów niestandardowych, zobacz [Konfigurowanie zachowań klienta](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Tworzenie obiektów wywołania zwrotnego dla usługi dwukierunkowe  
 Usługi dwukierunkowe Określ kontrakt wywołania zwrotnego, która aplikacja klienta należy wdrożyć w celu zapewnienia obiektu wywołania zwrotnego dla usługi do wywołania zgodnie z warunkami umowy. Mimo że obiekty wywołanie zwrotne nie są pełne usługi (na przykład nie można zainicjować kanału za pomocą obiektu wywołania zwrotnego), na potrzeby wdrażania i konfiguracji one mogą być uważane za rodzaj usługi.  
  
 Klienci usługi dwukierunkowe musi:  
  
- Implementowanie klasy kontrakt wywołania zwrotnego.  
  
- Tworzenie wystąpienia klasy implementacji kontrakt wywołania zwrotnego i użyć go do utworzenia <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> obiekt, który zostanie przekazany do konstruktora klienta programu WCF.  
  
- Wywoływanie operacji i obsługi operacji wywołania zwrotne.  
  
 Dwukierunkowe funkcje obiektów klienta WCF, takich jak ich odpowiedniki obsługującej, z wyjątkiem eksponowanie funkcje niezbędne do obsługi wywołań zwrotnych, w tym konfiguracją usługi wywołania zwrotnego.  
  
 Na przykład, można kontrolować różne aspekty zachowania w czasie wykonywania obiektu wywołania zwrotnego za pomocą właściwości <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> atrybut w klasie wywołania zwrotnego. Innym przykładem jest użycie <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> klasy, aby umożliwić powrót informacje o wyjątku do usługi, które wywołują obiektu wywołania zwrotnego. Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md). Aby uzyskać pełny przykład, zobacz [dwukierunkowego](../../../docs/framework/wcf/samples/duplex.md).  
  
 Na komputerach Windows XP z systemem Internet Information Services (IIS) 5.1 dwukierunkowego klienci muszą określić adres podstawowy klienta przy użyciu <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> klasy lub wyjątek jest zgłaszany. Poniższy przykład kodu pokazuje, jak to zrobić w kodzie.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Poniższy kod pokazuje, jak to zrobić w pliku konfiguracji  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Asynchroniczne wywoływanie usługi  
 Jak operacje są zwane zależy od całkowicie dewelopera klienta. Jest to spowodowane wiadomości, które tworzą operacji mogą zostać zmapowane do metod synchronicznych lub asynchronicznych wyrażone w kodzie zarządzanym. W związku z tym, jeśli chcesz skompilować klienta, który wywołuje operacje asynchroniczne, można Svcutil.exe do generowania kodu klienta asynchroniczne za pomocą `/async` opcji. Aby uzyskać więcej informacji, zobacz [jak: Asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Wywoływanie usług za pomocą kanałów klienta WCF  
 Typy klienta WCF rozszerzać <xref:System.ServiceModel.ClientBase%601>, która sama dziedziczy <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejsu do udostępnienia w odpowiednim systemie kanału. Usługi można wywołać za pomocą kontraktu usługi docelowej o <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [Architektura klienta programu WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
