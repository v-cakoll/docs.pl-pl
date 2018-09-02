---
title: Określanie adresu punktu końcowego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 718a0c086181546ba7b7fb3b31fce0732dd99382
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401770"
---
# <a name="specifying-an-endpoint-address"></a>Określanie adresu punktu końcowego
Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pośrednictwem jego punktów końcowych. Każdy <xref:System.ServiceModel.Description.ServiceEndpoint> zawiera <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>, a <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Kontrakt określa, jakie operacje są dostępne. Powiązanie określa sposób komunikowania się z usługą i określa adres, gdzie można znaleźć tę usługę. Każdy punkt końcowy musi mieć unikatowy adres. Adres punktu końcowego jest reprezentowany przez <xref:System.ServiceModel.EndpointAddress> klasy, która zawiera jednolite zasobów identyfikator (URI) reprezentujący adres usługi, <xref:System.ServiceModel.EndpointAddress.Identity%2A>, która reprezentuje tożsamość zabezpieczeń usługi, a kolekcja opcjonalne <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Opcjonalne nagłówki zawierają więcej szczegółowych informacji adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym. Na przykład nagłówków, można wskazać sposób przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania wiadomości przychodzących konkretnego użytkownika, jeśli wiele wystąpień są dostępne.  
  
## <a name="definition-of-an-endpoint-address"></a>Definicja adresu punktu końcowego  
 W programie WCF <xref:System.ServiceModel.EndpointAddress> modele odwołania do punktu końcowego (EPR), zgodnie z definicją w standardzie WS-Addressing.  
  
 Adres URI dla większości transportu ma cztery części. Na przykład, ten identyfikator URI, `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` ma następujące cztery części:  
  
-   Schemat: http:  
  
-   Maszyny: `www.fabrikam.com`  
  
-   (Opcjonalnie) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
 Częścią modelu EPR jest, że odwołania do każdego punktu końcowego może wykonywać niektóre parametry odwołań, dodających informacje identyfikacyjne dodatkowych. W programie WCF, parametry te odwołania są modelowane jako wystąpień obiektu <xref:System.ServiceModel.Channels.AddressHeader> klasy.  
  
 Adres punktu końcowego usługi można określić obowiązkowo przy użyciu kodu lub deklaratywne przy użyciu konfiguracji. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana. Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu. Zachowanie powiązania i adresowanie z kodu pozwala zmienić bez konieczności ponownego kompilowania i ponownego wdrażania aplikacji. Jeśli nie określono żadnych punktów końcowych w kodzie lub w konfiguracji, następnie środowiska uruchomieniowego dodaje jeden domyślny punkt końcowy na każdy adres podstawowy dla każdej umowy implementowane przez usługę.  
  
 Istnieją dwa sposoby, aby określić adresy punktów końcowych usługi w programie WCF. Można określić adresu bezwzględnego dla każdego punktu końcowego związane z usługą lub możesz podać adres bazowy <xref:System.ServiceModel.ServiceHost> usługi, a następnie określ adres dla każdego punktu końcowego skojarzonego z tą usługą, która jest zdefiniowana względem tej bazy adres. Aby określić adresy punktów końcowych usługi w konfiguracji czy kodu, można użyć każdej z tych procedur. Jeśli nie określisz adresu względnego, usługa korzysta z adresu podstawowego. Mogą też istnieć wiele adresami podstawowymi dla usługi, ale każda usługa jest dozwolony tylko jeden adres podstawowy dla każdego transportu. Jeśli masz wiele punktów końcowych, z których każdy jest skonfigurowany przy użyciu różnych powiązania, ich adresy muszą być unikatowe. Punkty końcowe, które używać tego samego powiązania, ale z różnymi umowami można użyć tego samego adresu.  
  
 W przypadku hostowania za pomocą programu IIS, nie jest zarządzana <xref:System.ServiceModel.ServiceHost> wystąpienia samodzielnie. Adres podstawowy jest zawsze adres podany w pliku svc usługi, w przypadku hostowania w usługach IIS. Dlatego należy użyć adresy punktów końcowych względną dla punktów końcowych usług hostowanych przez usługi IIS. Podając w pełni kwalifikowany adres punktu końcowego może prowadzić do błędów we wdrożeniu usługi. Aby uzyskać więcej informacji, zobacz [wdrażanie usługi WCF Internet Information Services-Hosted](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Definiowanie adresy punktów końcowych w konfiguracji  
 Aby zdefiniować punkt końcowy w pliku konfiguracji, należy użyć [ \<punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Gdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> (to znaczy, gdy aplikacja macierzysta podejmowana jest próba uruchomienia usługi), wywoływana jest metoda, system wyszukuje [ \<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) element z atrybutem nazwę, która określa "UE. Samples.HelloService". Jeśli [ \<usługi >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) element zostanie znaleziony, system ładuje określoną klasę i tworzy punkty końcowe, korzystając z definicji punktu końcowego w pliku konfiguracji. Ten mechanizm pozwala na ładowanie, a następnie uruchom usługę za pomocą dwóch wierszy kodu przy jednoczesnym zachowaniu powiązania i adresowanie poza swój kod. Zaletą tego podejścia jest to, że tych zmian bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.  
  
 Opcjonalne nagłówki są deklarowane w [ \<nagłówki >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Oto przykład służącego do określania punktów końcowych usługi w pliku konfiguracji, który rozróżnia dwa nagłówki: "Złota" klientów z `http://tempuri1.org/` i "Standardowy" klientów z `http://tempuri2.org/`. Klient wywoływanie tej usługi, musi mieć odpowiednie [ \<nagłówki >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) w jego pliku konfiguracji.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Nagłówki można również ustawić na poszczególne wiadomości zamiast wszystkie komunikaty w punkcie końcowym (jak pokazano wcześniej). Jest to wykonywane przy użyciu <xref:System.ServiceModel.OperationContextScope> Aby utworzyć nowy kontekst w aplikacji klienckiej, aby dodać niestandardowy nagłówek do wysyłanej wiadomości, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Adres punktu końcowego metadanych  
 Adres punktu końcowego jest reprezentowana w sieci Web Services Description Language (WSDL) jako usługi WS-Addressing `EndpointReference` — element (EPR) wewnątrz odpowiedni punkt końcowy `wsdl:port` elementu. EPR zawiera adres punktu końcowego oraz wszelkie właściwości adresu. Należy pamiętać, że EPR wewnątrz `wsdl:port` zastępuje `soap:Address` jak pokazano w poniższym przykładzie.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Definiowanie adresy punktów końcowych w kodzie  
 Adres punktu końcowego można utworzyć w kodzie za pomocą <xref:System.ServiceModel.EndpointAddress> klasy. Adres punktu końcowego określonego identyfikatora URI może być w pełni kwalifikowanej ścieżki lub ścieżki, który jest określany względem adresu podstawowego usługi. Poniższy kod ilustruje sposób tworzenia wystąpienia <xref:System.ServiceModel.EndpointAddress> klasy i dodać go do <xref:System.ServiceModel.ServiceHost> wystąpienie hostujące usługi.  
  
 Poniższy przykład pokazuje, jak określić adres punktu końcowego pełnego w kodzie.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 Poniższy przykład pokazuje, jak dodać adresu względnego ("MyService") na adres bazowy hosta usługi.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Właściwości <xref:System.ServiceModel.Description.ServiceDescription> w usłudze aplikacji nie mogą zostać zmodyfikowane subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metody <xref:System.ServiceModel.ServiceHostBase>. Niektóre elementy członkowskie, takich jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości i `AddServiceEndpoint` metod <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, zgłosić wyjątek, jeśli zmodyfikowane od tego momentu. Inne pozwala na ich modyfikować, ale wynik jest niezdefiniowany.  
>   
>  Podobnie, na komputerze klienckim <xref:System.ServiceModel.Description.ServiceEndpoint> wartości nie mogą zostać zmodyfikowane po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli modyfikowany po tym punkcie. Inne wartości Opis klienta można zmodyfikować bez błędów, ale wynik jest niezdefiniowany.  
>   
>  Czy usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Przy użyciu domyślnych punktów końcowych  
 Jeśli nie określono żadnych punktów końcowych w kodzie lub w konfiguracji następnie środowisko wykonawcze zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy na każdy adres podstawowy dla każdej umowy serwisowej implementowane przez usługę. Adres podstawowy, można określić w kodzie lub w konfiguracji i domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana w <xref:System.ServiceModel.ServiceHost>.  
  
 Jeśli punkty końcowe są podane jawnie, nadal można dodać domyślnych punktów końcowych przez wywołanie metody <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.EndpointAddress>  
 [Uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hosting](../../../docs/framework/wcf/feature-details/hosting.md)
