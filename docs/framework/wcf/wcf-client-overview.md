---
title: "Przegląd klienta programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d6dd9e34561f397c581e148a549ad85762c81e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-client-overview"></a>Przegląd klienta programu WCF
W tej sekcji opisano, jakie aplikacje klienckie czy i jak konfigurowanie, tworzenie i używanie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] klienta i zabezpieczania aplikacji klienckich.  
  
## <a name="using-wcf-client-objects"></a>Przy użyciu obiektów klienta WCF  
 Aplikacja kliencka zarządzanych aplikacji, która używa [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientom komunikowanie się z inną aplikację. Aby utworzyć aplikację klienta dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi wymaga wykonania następujących czynności:  
  
1.  Uzyskaj kontraktu usługi, powiązania oraz informacji o adresie dla punktu końcowego usługi.  
  
2.  Utwórz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta przy użyciu tych informacji.  
  
3.  Wywoływanie operacji.  
  
4.  Zamknij [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta.  
  
 W poniższych sekcjach omówiono konfigurowanie tych kroków i podaj krótkie instrukcje na następujące zagadnienia:  
  
-   Obsługa błędów.  
  
-   Konfigurowanie i Zabezpieczanie klientów.  
  
-   Tworzenie obiektów wywołania zwrotnego dla usługi dwukierunkowe.  
  
-   Wywołanie usługi w sposób asynchroniczny.  
  
-   Wywoływanie usług za pomocą kanałów klienta.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Uzyskaj kontraktu usługi, powiązań i adresów  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], usług i klientów kontrakty modelu przy użyciu atrybutów zarządzanych, interfejsów i metod. Aby połączyć się z usługi aplikacji klienta, należy uzyskać informacje o typie kontraktu usługi. Zwykle, możesz to zrobić przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), co spowoduje pobranie metadanych z usługi, konwertuje je do pliku kodu źródłowego zarządzanych w wybranym języku i tworzy klienta plik konfiguracji aplikacji, którego można użyć do skonfigurowania programu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta. Na przykład, jeśli zamierzasz utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta do wywołania `MyCalculatorService`, i dowiedzieć się, że metadanych dla tej usługi jest publikowany w `http://computerName/MyCalculatorService/Service.svc?wsdl`, następnie Poniższy przykładowy kod przedstawia sposób umożliwia uzyskanie Svcutil.exe `ClientCode.vb` plik, który zawiera usługę kontraktu w kodzie zarządzanym.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Ten kod kontraktu można kompilować albo do aplikacji klienckiej lub do innego zestawu, który aplikacja kliencka można następnie użyć do utworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta. Plik konfiguracji umożliwia konfigurowanie obiektu klienta, aby poprawnie połączyć się z usługą.  
  
 Na przykład ten proces zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Aby uzyskać więcej informacji o umowach, zobacz [kontrakty](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Utworzony obiekt klienta WCF  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta jest lokalny obiekt, który reprezentuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi w postaci klient może używać do komunikowania się z usługi zdalnej. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]typy klientów implementacji usługi docelowej kontraktu, dlatego podczas należy utworzyć i skonfigurować je, następnie za pomocą obiektu klienta bezpośrednio do wywołania operacji usługi. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Uruchom Konwertuje czas metodę wywołania do wiadomości, wysyła je z usługą nasłuchuje odpowiedzi i zwraca tych wartości [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta jako wartości zwracane lub `out` lub `ref` parametrów.  
  
 Można również użyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiekty kanału klienta do nawiązywania połączeń z i korzystania z usług. Aby uzyskać więcej informacji, zobacz [Architektura klienta WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Tworzenie nowego obiektu WCF  
 Aby zilustrować stosowania <xref:System.ServiceModel.ClientBase%601> klasy, załóżmy następujące kontraktu usługi simple został wygenerowany z aplikacją usługi.  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] do utworzenia sieci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, obiekty są ładowane automatycznie do przeglądarki obiektów podczas dodawania odwołania do usługi do projektu.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Jeśli nie używasz [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sprawdź generowanego kodu kontraktu można znaleźć typu, rozszerzający <xref:System.ServiceModel.ClientBase%601> i interfejsu kontraktu usługi `ISampleService`. W takim przypadku tego typu wygląda podobnie do następującego kodu:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Ta klasa można tworzyć jako obiekt lokalny przy użyciu jednego z konstruktorów, skonfigurowane i następnie używany do łączenia się z usługą typu `ISampleService`.  
  
 Zalecane jest utworzenie użytkownika [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, obiekt i używać go i zamknij go wewnątrz bloku try/catch pojedynczego. Nie należy używać `using` instrukcji (`Using` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ponieważ może maskować wyjątki w trybach niektórych awarii. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]w poniższych sekcjach przedstawiono również jako [unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Adresy, powiązania i kontrakty  
 Aby można było utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta, należy skonfigurować obiekt klienta. W szczególności musi mieć usługi *punktu końcowego* do użycia. Punkt końcowy jest kombinacją kontraktu usługi, powiązanie i adres. ([!INCLUDE[crabout](../../../includes/crabout-md.md)] punktów końcowych, zobacz [punkty końcowe: adresy, wiązania i kontrakty](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Zazwyczaj tych informacji znajduje się w [ \<punktu końcowego >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) elementu w pliku konfiguracji aplikacji klienta, takie jak narzędzia Svcutil.exe generuje i ładowane automatycznie podczas tworzenia klienta obiekt. Zarówno [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienckich typy mają także przeciążenia, które umożliwiają programowe określenie tych informacji.  
  
 Na przykład plik konfiguracji wygenerowany dla `ISampleService` używany w poprzednim przykłady zawiera następujące informacje punktu końcowego.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Ten plik konfiguracji określa punkt końcowy docelowego w `<client>` elementu. [!INCLUDE[crabout](../../../includes/crabout-md.md)]przy użyciu wielu docelowych punktów końcowych, zobacz <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> konstruktorów.  
  
## <a name="calling-operations"></a>Podczas wywoływania operacji  
 Po obiektu klienta utworzony i skonfigurowany, Utwórz bloku try/catch, wywoływania operacji w taki sam sposób, jak gdyby lokalnych i Zamknij obiekt [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta. Gdy aplikacja klient wywołuje pierwszej operacji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatycznie otwiera odpowiadającego kanału i kanału źródłowego jest zamknięty, gdy obiekt zostanie odtworzony. (, Można również jawnie otwarcia i zamknięcia kanału przed lub po wywołaniem innych operacji.)  
  
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
  
 Tworząc można wywołać operacji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta i wywołanie jego metody, jak pokazano w poniższym przykładzie kodu. Należy pamiętać, że otwierania, wywołania i zamykania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta obiekt występuje w bloku try/catch pojedynczego. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) i [co pozwala uniknąć problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Obsługa błędów  
 Wyjątki mogą występować w aplikacji klienckiej podczas otwierania podstawowej klienta kanału (czy jawnie lub automatycznie przez wywołanie operacji), za pomocą obiektu klienta lub kanału do wywoływania operacji, lub podczas zamykania podstawowego kanału klienta. Zalecane jest co najmniej że aplikacji oczekują możliwości obsługi <xref:System.TimeoutException?displayProperty=nameWithType> i <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> wyjątki oprócz żadnego <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> obiektów zgłoszony wyniku błędach SOAP zwracanych przez operacje. Błędach SOAP określona w kontrakt operacji są zgłaszane dla aplikacji klienckich jako <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> gdzie parametr typu jest typ szczegółów błędu protokołu SOAP. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Obsługa błędów w aplikacji klienta, zobacz [wysyłanie i odbieranie błędów](../../../docs/framework/wcf/sending-and-receiving-faults.md). Aby uzyskać kompletny przykładowy pokazuje sposób obsługi błędów w kliencie, zobacz [oczekiwane wyjątki](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurowanie i Zabezpieczanie klientów  
 Konfigurowanie klienta rozpoczyna się od ładowania wymagane informacje o punkcie końcowym docelowego dla obiektu klienta lub kanału, zwykle z pliku konfiguracji, mimo że można również obciążenia tych informacji programowo przy użyciu klienta konstruktory i właściwości. Jednak dodatkowe czynności konfiguracyjne są wymagane do włączenia pewnych zachowanie klienta i w różnych scenariuszach zabezpieczeń.  
  
 Na przykład wymagania dotyczące zabezpieczeń dla kontraktów usług są zadeklarowane w interfejsu kontraktu usługi, a jeśli Svcutil.exe utworzony plik konfiguracji, ten plik zawiera zwykle powiązanie, które może obsłużyć wymagania dotyczące zabezpieczeń usługi. W niektórych przypadkach, jednak więcej zabezpieczeń może być wymagana konfiguracja, takie jak Konfigurowanie poświadczeń klienta. Aby uzyskać pełne informacje o konfiguracji zabezpieczeń dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów, zobacz [Zabezpieczanie klientów](../../../docs/framework/wcf/securing-clients.md).  
  
 Ponadto niektóre niestandardowymi modyfikacjami można włączyć w aplikacjach klienckich, takich jak niestandardowe zachowania czasu wykonywania. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Konfigurowanie zachowania klientów niestandardowych, zobacz [Konfigurowanie zachowań klienta](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Tworzenie obiektów wywołania zwrotnego dla usługi dwukierunkowe  
 Usługi dwukierunkowe Określ kontrakt wywołania zwrotnego, który aplikacja kliencka należy wdrożyć w celu zapewnienia obiektu wywołania zwrotnego dla usługi do wywołania zgodnie z warunkami umowy. Mimo że obiekty wywołania zwrotnego nie są pełne usługi (na przykład nie można zainicjować kanału obiektu wywołania zwrotnego), na potrzeby wykonania i ich można traktować jako rodzaj usługi konfiguracji.  
  
 Klienci usługi dwukierunkowe musi:  
  
-   Implementowanie klasy kontrakt wywołania zwrotnego.  
  
-   Tworzenie wystąpienia klasy implementacji kontraktu wywołania zwrotnego i umożliwia tworzenie <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> obiekt przekazywany do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konstruktora klienta.  
  
-   Wywołanie operacji i obsługi operacji wywołania zwrotne.  
  
 Dupleks [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta obiektów funkcji, takich jak ich odpowiedniki obsługującej, z wyjątkiem, że udostępniają funkcje niezbędne do obsługi wywołań zwrotnych, łącznie z konfiguracji usługi wywołania zwrotnego.  
  
 Na przykład można kontrolować różne aspekty zachowania w czasie wykonywania obiektu wywołania zwrotnego przy użyciu właściwości <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> atrybutu dla klasy wywołania zwrotnego. Innym przykładem jest użycie <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> klasy, aby umożliwić powrót informacji o wyjątkach do usług, które wywołują obiektu wywołania zwrotnego. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md). Dla kompletnego przykładu, zobacz [dupleksu](../../../docs/framework/wcf/samples/duplex.md).  
  
 Na komputerach z systemem Windows XP z systemem Internet Information Services (IIS) 5.1 dupleksu klienci muszą określić adres podstawowy klienta przy użyciu <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> klasy lub wyjątek zostanie zgłoszony. Poniższy przykład kodu pokazuje, jak to zrobić w kodzie.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Poniższy kod przedstawia, jak to zrobić w pliku konfiguracji  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Wywołanie usługi w sposób asynchroniczny  
 Jak są nazywane operacji jest całkowicie zależy deweloperowi klienta. Jest to spowodowane wiadomości, które tworzą operacji mogą być mapowane do metod synchroniczna lub asynchroniczna wyrażone w kodzie zarządzanym. W związku z tym, jeśli chcesz skompilować klienta, który wywołuje asynchronicznie operacje, można Svcutil.exe do generowania kodu klienta asynchronicznych za pomocą `/async` opcji. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Porady: asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Wywoływanie usług za pomocą kanałów klienta WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]rozszerzenie klienta typy <xref:System.ServiceModel.ClientBase%601>, które pochodzi z <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejs do udostępnienia źródłowy system kanału. Usługi można wywołać za pomocą kontraktu usługi docelowej z <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [Architektura klienta WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
