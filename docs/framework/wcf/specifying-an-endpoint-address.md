---
title: Określanie adresu punktu końcowego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 784b0fe3e2b23287d458f9aa4d8276e10dd6ed97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-an-endpoint-address"></a>Określanie adresu punktu końcowego
Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez jego punktów końcowych. Każdy <xref:System.ServiceModel.Description.ServiceEndpoint> zawiera <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>, a <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Kontrakt określa, jakie operacje są dostępne. Powiązanie określa sposób komunikowania się z usługą, a adres Określa, gdzie można znaleźć usługi. Każdy punkt końcowy musi mieć unikatowy adres. Adres punktu końcowego jest reprezentowana przez <xref:System.ServiceModel.EndpointAddress> klasy, która zawiera zasób identyfikator URI (Uniform) reprezentujący adres usługi, <xref:System.ServiceModel.EndpointAddress.Identity%2A>, reprezentuje tożsamości zabezpieczeń usługi, a kolekcja opcjonalne <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Opcjonalne nagłówki zawierają bardziej szczegółowe informacje adresowania do identyfikacji użytkownika lub interakcji z punktem końcowym. Na przykład nagłówków można wskazać sposobu przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania komunikat przychodzący z konkretnego użytkownika, jeśli dostępnych jest wiele wystąpień.  
  
## <a name="definition-of-an-endpoint-address"></a>Definicja adresu punktu końcowego  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], <xref:System.ServiceModel.EndpointAddress> modele odwołanie do punktu końcowego (EPR) zgodnie z definicją w standardzie WS-Addressing.  
  
 Adres URI dla transportu większości ma cztery części. Na przykład ten identyfikator URI, "http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" zawiera następujące cztery części:  
  
-   Schemat: http:  
  
-   Machine: www.fabrikam.com  
  
-   (Opcjonalnie) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
 Część modelu EPR jest, że odwołanie do każdego punktu końcowego może przenosić niektórych parametrów odwołania, które dodać informacje identyfikacyjne bardzo. W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], te parametry odwołania są modelowane jako wystąpienia <xref:System.ServiceModel.Channels.AddressHeader> klasy.  
  
 Imperatively przy użyciu kodu lub deklaratywnie przy użyciu konfiguracji można określić adres punktu końcowego usługi. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane. Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu. Utrzymywanie powiązania i adresowanie poza kod pozwala na zmianę bez konieczności ponowne skompilowanie i wdrożenie aplikacji. Jeżeli nie określono żadnych punktów końcowych w kodzie, lub w konfiguracji, następnie środowiska uruchomieniowego dodaje jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy zaimplementowanych przez usługę.  
  
 Istnieją dwa sposoby, aby określić adres punktu końcowego usługi w programie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Można określić jako adres bezwzględny dla każdego punktu końcowego związane z usługą lub możesz podać adres podstawowy <xref:System.ServiceModel.ServiceHost> usługi, a następnie określ adres dla każdego punktu końcowego skojarzone z tą usługą, która jest zdefiniowana względem tej bazy adres. Aby określić adres punktu końcowego usługi w konfiguracji lub kod, można użyć każdego z tych procedur. Jeśli nie określisz adresu względnego, usługa używa adres podstawowy. Może istnieć wiele adresami podstawowymi dla usługi, ale każda usługa jest dozwolony tylko jeden adres podstawowy dla każdego transportu. Jeśli masz wiele punktów końcowych, z których każdy ma skonfigurowane inne powiązanie, adresy muszą być unikatowe. Punkty końcowe, które używać tego samego powiązania, ale różnymi umowami można użyć tego samego adresu.  
  
 Jeśli obsługa za pomocą usług IIS, nie jest zarządzana <xref:System.ServiceModel.ServiceHost> wystąpienie samodzielnie. Adres podstawowy jest zawsze adresem określonym w pliku svc usługi odnośnie do hostowania w usługach IIS. Dlatego należy użyć adresy punktów końcowych względną dla punktów końcowych usług hostowanych przez usługi IIS. Podając w pełni kwalifikowany adres punktu końcowego może prowadzić do błędów w ramach wdrożenia usługi. Aby uzyskać więcej informacji, zobacz [wdrażanie usługi WCF Internet Information Services-Hosted](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Definiowanie adresy punktów końcowych w konfiguracji  
 Aby zdefiniować punkt końcowy w pliku konfiguracji, należy użyć [ \<punktu końcowego >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Gdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda jest wywoływana (Jeśli aplikacja macierzysta podejmowana jest próba uruchomienia usługi), system wyszukuje [ \<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) element z atrybutem nazwy, która określa "UE. Samples.HelloService". Jeśli [ \<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) element zostanie znaleziony, system ładuje określonej klasy i tworzy punktów końcowych przy użyciu definicji punktu końcowego zawarty w pliku konfiguracji. Mechanizm ten umożliwia obciążenia i uruchomić usługę przy użyciu dwóch wierszy kodu podczas aktualizowania powiązania i adresowanie poza swój kod. Zaletą tej metody jest, że te zmiany mogą być wprowadzane bez konieczności ponowne skompilowanie lub ponownego wdrażania aplikacji.  
  
 Opcjonalne nagłówki są zadeklarowane w [ \<nagłówki >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Poniżej przedstawiono przykład elementów używany do określenia punktów końcowych dla usługi w pliku konfiguracji, która odróżnia między dwa nagłówki: "Złota" klientów z http://tempuri1.org/ i "Standardowy" klientów z http://tempuri2.org/. Wywoływanie tej usługi Klient musi mieć odpowiednie [ \<nagłówki >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) w pliku konfiguracji.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Nagłówki można również ustawić na poszczególne wiadomości zamiast wszystkie wiadomości w punkcie końcowym (jak pokazano wcześniej). Jest to zrobić za pomocą <xref:System.ServiceModel.OperationContextScope> Aby utworzyć nowy kontekst w aplikacji klienckiej, aby dodać niestandardowego nagłówka do wysyłanej wiadomości, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Adres punktu końcowego w metadanych  
 Adres punktu końcowego jest reprezentowana w sieci Web Services Description Language (WSDL) jako usługi WS-Addressing `EndpointReference` (EPR) element wewnątrz odpowiedniego punktu końcowego `wsdl:port` elementu. EPR zawiera adres punktu końcowego, a także wszystkie właściwości adresu. Należy pamiętać, że EPR wewnątrz `wsdl:port` zastępuje `soap:Address` jak pokazano w poniższym przykładzie.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Definiowanie adresy punktów końcowych w kodzie  
 Adres punktu końcowego można tworzyć w kodzie z <xref:System.ServiceModel.EndpointAddress> klasy. Identyfikator URI dla danego adresu punktu końcowego może być w pełni kwalifikowaną ścieżkę lub ścieżką względną wobec adres podstawowy usługi. Poniższy kod ilustruje sposób tworzenia wystąpienia <xref:System.ServiceModel.EndpointAddress> klasy i dodaj go do <xref:System.ServiceModel.ServiceHost> wystąpienia obsługującego usługę.  
  
 W poniższym przykładzie pokazano, jak określać adres punktu końcowego pełna w kodzie.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 W poniższym przykładzie pokazano sposób dodawania adres względny ("Moja_usługa") na adres podstawowy usługi hosta.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Właściwości <xref:System.ServiceModel.Description.ServiceDescription> w usłudze aplikacji nie można modyfikować subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda <xref:System.ServiceModel.ServiceHostBase>. Niektóre elementy, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości i `AddServiceEndpoint` metod na <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, Zgłoś wyjątek, jeśli zmodyfikowane po tym momencie. Inne pozwala na ich modyfikacji, ale wynik jest niezdefiniowany.  
>   
>  Podobnie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint> nie można modyfikować wartości po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli zmodyfikowane po tym momencie. Inne wartości klienta opis można zmodyfikować bez błędów, ale wynik jest niezdefiniowany.  
>   
>  Czy dla usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Przy użyciu domyślnych punktów końcowych  
 Jeśli nie określono żadnych punktów końcowych w kodzie, lub w konfiguracji następnie środowiska uruchomieniowego zawiera domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej zaimplementowanych przez usługę. Adres podstawowy można określić w kodzie, lub w konfiguracji i domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana na <xref:System.ServiceModel.ServiceHost>.  
  
 W przypadku punktów końcowych są jawnie, nadal można dodać domyślne punkty końcowe przez wywołanie metody <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.EndpointAddress>  
 [Uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hosting](../../../docs/framework/wcf/feature-details/hosting.md)
