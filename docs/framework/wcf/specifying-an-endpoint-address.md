---
title: Określanie adresu punktu końcowego
description: Dowiedz się więcej o adresie punktu końcowego, jednej części elementu ServiceEndpoint w programie WCF. Cała komunikacja z usługą WCF odbywa się za pomocą punktów końcowych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: e1bd9e5a27d1bc86d2d3e04ee82221a27a4e1fa8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245988"
---
# <a name="specifying-an-endpoint-address"></a>Określanie adresu punktu końcowego

Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą punktów końcowych. Każdy z nich <xref:System.ServiceModel.Description.ServiceEndpoint> zawiera <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A> , a <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A> i <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> . Kontrakt Określa, które operacje są dostępne. Powiązanie określa sposób komunikacji z usługą, a adres określa miejsce, w którym ma zostać znaleziona usługa. Każdy punkt końcowy musi mieć unikatowy adres. Adres punktu końcowego jest reprezentowany przez <xref:System.ServiceModel.EndpointAddress> klasę, która zawiera Uniform Resource Identifier (URI), który reprezentuje adres usługi, <xref:System.ServiceModel.EndpointAddress.Identity%2A> , która reprezentuje tożsamość zabezpieczeń usługi i kolekcję opcjonalne <xref:System.ServiceModel.EndpointAddress.Headers%2A> . Opcjonalne nagłówki zawierają bardziej szczegółowe informacje dotyczące adresowania, które identyfikują lub współpracują z punktem końcowym. Na przykład nagłówki mogą wskazywać, jak przetwarzać komunikat przychodzący, gdzie punkt końcowy powinien wysłać komunikat odpowiedzi lub którego wystąpienia usługi należy użyć do przetworzenia komunikatu przychodzącego od określonego użytkownika, gdy jest dostępnych wiele wystąpień.

## <a name="definition-of-an-endpoint-address"></a>Definicja adresu punktu końcowego

W programie WCF <xref:System.ServiceModel.EndpointAddress> modeluje odwołanie do punktu końcowego (EPR) zgodnie z definicją w standardzie WS-Addressing.

Identyfikator URI adresu dla większości transportów ma cztery części. Na przykład ten identyfikator URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` ma cztery następujące części:

- Schemat: http:

- Maszynie`www.fabrikam.com`

- Obowiązkowe Port: 322

- Ścieżka:/mathservice.svc/secureEndpoint

Częścią modelu EPR jest to, że każde odwołanie do punktu końcowego może zawierać kilka parametrów referencyjnych, które dodają dodatkowe informacje identyfikacyjne. W programie WCF te parametry odwołania są modelowane jako wystąpienia <xref:System.ServiceModel.Channels.AddressHeader> klasy.

Adres punktu końcowego dla usługi można określić za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi. Ogólnie rzecz biorąc, bardziej praktyczne jest zdefiniowanie punktów końcowych usługi przy użyciu konfiguracji zamiast kodu. Przechowywanie informacji o powiązaniach i adresowaniu poza kodem pozwala im zmieniać bez konieczności ponownego kompilowania i wdrażania aplikacji. Jeśli w kodzie lub w konfiguracji nie określono żadnych punktów końcowych, środowisko uruchomieniowe doda do każdego z nich domyślny punkt końcowy dla każdego kontraktu zaimplementowanego przez usługę.

Istnieją dwa sposoby określania adresów punktów końcowych dla usługi w programie WCF. Można określić adres bezwzględny dla każdego punktu końcowego skojarzonego z usługą lub podać adres podstawowy dla <xref:System.ServiceModel.ServiceHost> usługi, a następnie określić adres dla każdego punktu końcowego skojarzonego z tą usługą, która jest zdefiniowana względem tego adresu podstawowego. Każdą z tych procedur można użyć, aby określić adresy punktów końcowych dla usługi w konfiguracji lub kodzie. Jeśli nie określisz adresu względnego, usługa korzysta z adresu podstawowego. Istnieje również wiele adresów podstawowych dla usługi, ale dla każdej usługi jest dozwolony tylko jeden adres podstawowy dla każdego transportu. Jeśli masz wiele punktów końcowych, z których każdy jest skonfigurowany przy użyciu innego powiązania, ich adresy muszą być unikatowe. Punkty końcowe używające tego samego powiązania, ale różne kontrakty mogą korzystać z tego samego adresu.

W przypadku hostowania za pomocą usług IIS nie można <xref:System.ServiceModel.ServiceHost> samodzielnie zarządzać wystąpieniem. Adres podstawowy jest zawsze adresem określonym w pliku SVC dla usługi podczas hostowania w usługach IIS. W związku z tym należy używać względnych adresów punktów końcowych dla punktów końcowych usług hostowanych przez usługi IIS. Dostarczenie w pełni kwalifikowanego adresu punktu końcowego może prowadzić do błędów we wdrożeniu usługi. Aby uzyskać więcej informacji, zobacz [wdrażanie usługi WCF hostowanej w Internet Information Services](./feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="defining-endpoint-addresses-in-configuration"></a>Definiowanie adresów punktów końcowych w konfiguracji

Aby zdefiniować punkt końcowy w pliku konfiguracji, użyj [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) elementu.

[!code-xml[S_UEHelloWorld#5](./snippets/specifying-an-endpoint-address/serviceapp2.config#5)]

Gdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> wywoływana jest metoda (to jest, gdy aplikacja hostingu próbuje uruchomić usługę), system szuka [\<service>](../configure-apps/file-schema/wcf/service.md) elementu z atrybutem nazwy określającym wartość "UE. Przykłady. HelloService ". Jeśli [\<service>](../configure-apps/file-schema/wcf/service.md) element zostanie znaleziony, system ładuje określoną klasę i tworzy punkty końcowe przy użyciu definicji punktów końcowych dostępnych w pliku konfiguracji. Ten mechanizm pozwala ładować i uruchamiać usługę z dwoma wierszami kodu przy zachowaniu powiązania i adresowania informacji z kodu. Zaletą tego podejścia jest to, że te zmiany mogą być wykonywane bez konieczności ponownego kompilowania lub wdrażania aplikacji.

Opcjonalne nagłówki są deklarowane w [\<headers>](../configure-apps/file-schema/wcf/headers-element.md) . Poniżej przedstawiono przykładowe elementy służące do określania punktów końcowych dla usługi w pliku konfiguracji, który odróżnia dwa nagłówki: klienci "Gold" od `http://tempuri1.org/` i "standardowe" klientów programu `http://tempuri2.org/` . Klient wywołujący tę usługę musi mieć odpowiednie [\<headers>](../configure-apps/file-schema/wcf/headers-element.md) w jego pliku konfiguracji.

[!code-xml[S_UEHelloWorld#1](./snippets/specifying-an-endpoint-address/serviceapp.config#1)]

Nagłówki można także ustawiać dla poszczególnych komunikatów zamiast wszystkich komunikatów w punkcie końcowym (jak pokazano wcześniej). Można to zrobić za pomocą polecenia, <xref:System.ServiceModel.OperationContextScope> Aby utworzyć nowy kontekst w aplikacji klienckiej w celu dodania niestandardowego nagłówka do wiadomości wychodzącej, jak pokazano w poniższym przykładzie.

[!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
[!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]

## <a name="endpoint-address-in-metadata"></a>Adres punktu końcowego w metadanych

Adres punktu końcowego jest reprezentowany w Web Services Description Language (WSDL) jako element WS-Addressing `EndpointReference` (EPR) wewnątrz odpowiedniego elementu punktu końcowego `wsdl:port` . EPR zawiera adres punktu końcowego, a także wszystkie właściwości adresu. Należy zauważyć, że EPR wewnątrz `wsdl:port` zastępuje się `soap:Address` w poniższym przykładzie.

## <a name="defining-endpoint-addresses-in-code"></a>Definiowanie adresów punktów końcowych w kodzie

Adres punktu końcowego można utworzyć w kodzie z <xref:System.ServiceModel.EndpointAddress> klasą. Identyfikator URI określony dla adresu punktu końcowego może być w pełni kwalifikowaną ścieżką lub ścieżką względną względem adresu podstawowego usługi. Poniższy kod ilustruje sposób tworzenia wystąpienia <xref:System.ServiceModel.EndpointAddress> klasy i dodawania go do <xref:System.ServiceModel.ServiceHost> wystąpienia, które obsługuje usługę.

W poniższym przykładzie pokazano, jak określić pełny adres punktu końcowego w kodzie.

[!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]

W poniższym przykładzie pokazano, jak dodać adres względny ("Moje usługi") do adresu podstawowego hosta usługi.

[!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]

> [!NOTE]
> Właściwości <xref:System.ServiceModel.Description.ServiceDescription> w aplikacji usługi nie mogą być modyfikowane po <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodzie <xref:System.ServiceModel.ServiceHostBase> . Niektóre elementy członkowskie, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Właściwość i `AddServiceEndpoint` metody w <xref:System.ServiceModel.ServiceHostBase> i, zgłaszają wyjątek, jeśli są <xref:System.ServiceModel.ServiceHost> modyfikowane po tym punkcie. Inne umożliwiają modyfikowanie ich, ale wynik jest niezdefiniowany.
>
> Analogicznie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint> wartości nie mogą być modyfikowane po wywołaniu metody <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ChannelFactory> . <xref:System.ServiceModel.ChannelFactory.Credentials%2A>Właściwość zgłasza wyjątek, jeśli został zmodyfikowany po tym punkcie. Inne wartości opisu klienta można modyfikować bez błędu, ale wynik jest niezdefiniowany.
>
> Niezależnie od tego, czy dla usługi lub klienta zaleca się zmodyfikowanie opisu przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> .

## <a name="using-default-endpoints"></a>Używanie domyślnych punktów końcowych

Jeśli w kodzie lub w konfiguracji nie określono żadnych punktów końcowych, środowisko uruchomieniowe udostępnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego kontraktu usługi zaimplementowanego przez usługę. Adres podstawowy może być określony w kodzie lub w konfiguracji, a domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana na <xref:System.ServiceModel.ServiceHost> .

Jeśli punkty końcowe są podane jawnie, można nadal dodawać domyślne punkty końcowe, wywołując <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> dla <xref:System.ServiceModel.ServiceHost> przed wywołaniem metody <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> . Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.EndpointAddress>
- [Uwierzytelnianie i tożsamość usług](./feature-details/service-identity-and-authentication.md)
- [Przegląd tworzenia punktów końcowych](endpoint-creation-overview.md)
- [Hosting](./feature-details/hosting.md)
