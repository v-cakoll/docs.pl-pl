---
title: "Omówienie sesji niezawodnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ddec86fac46da7a93d17ecd55f292471fac2ee5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions-overview"></a>Omówienie sesji niezawodnych

[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Niezawodna obsługa komunikatów SOAP zapewnia niezawodność transferu wiadomości na trasie między punktami końcowymi protokołu SOAP. Dzieje się tak w sieciach, które są zawodnych rozwiązywania błędów transportu i błędów poziom komunikatu SOAP. W szczególności zapewnia oparte na sesji, pojedynczego i (opcjonalnie) uporządkowane dostarczania wiadomości przesyłane za pośrednictwem pośredników SOAP lub transportu. Oparte na sesji dostarczania zapewnia grupowanie wiadomości w sesji z opcjonalne kolejności komunikatów.

W tym temacie opisano niezawodnej sesji, jak i kiedy należy używać ich oraz jak je zabezpieczyć.

## <a name="wcf-reliable-sessions"></a>Niezawodne sesje WCF

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]niezawodne sesje jest implementacją protokołu SOAP niezawodnej obsługi komunikatów, zgodnie z definicją protokołu WS-ReliableMessaging.

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Niezawodna obsługa komunikatów SOAP zawiera niezawodnej sesji na trasie między dwoma punktami końcowymi, niezależnie od liczby i typ pośredników oddzielające komunikatów punktów końcowych. Dotyczy to również wszelkich pośredników transportu, które nie używają protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników korzystających z protokołu SOAP (np. routery opartego na protokole SOAP lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Kanał niezawodnej sesji obsługuje *interakcyjne* komunikacji, aby usługi połączone przez kanał taki uruchamiać jednocześnie i komunikaty o stanie programu exchange i procesu w warunkach niskim opóźnieniem, oznacza to, w ramach stosunkowo krótkich przedziały czasu. Ta sprzężenia oznacza, że te składniki postęp razem lub się nie powieść, więc nie ma bez izolacji udostępniane między nimi.

Niezawodnej sesji maski dwa rodzaje błędów:

- Błędy poziom komunikatu SOAP, co obejmuje wiadomości utraconych lub zduplikowane i komunikaty przychodzące w innej kolejności w kolejności, w jakiej zostały wysłane.

- Transport błędów.

Niezawodnej sesji implementuje okno transfer w pamięci na awarie maska poziom komunikatu protokołu SOAP i protokołu WS-ReliableMessaging i ponownie nawiązuje połączenia w przypadku awarii transportu.

Niezawodnej sesji zawiera wiadomości SOAP protokołu TCP zapewnia dla pakietów IP. Połączenie gniazda TCP zapewnia pojedynczego, w kolejności transferu pakietów IP między węzłami. Niezawodny kanał zawiera ten sam typ transferu niezawodne, ale różni się od niezawodności gniazda TCP w następujący sposób:

- Niezawodność jest wglądu do wiadomości SOAP poziomu, nie dla arbitralnie rozmiarze pakiecie bajtów.

- Niezawodność jest transport niezależny od, nie tylko na transfer za pośrednictwem protokołu TCP.

- Niezawodność nie jest powiązany z sesją danego transportu (na przykład sesji, który zapewnia połączenie TCP) i może używać wiele sesji transportu jednocześnie lub sekwencyjnie w okresie istnienia niezawodnej sesji.

- Niezawodna sesja jest między nadawcą i odbiorcą punktów końcowych SOAP, niezależnie od liczby wymaganych do łączności między nimi połączenia transportu. Krótko mówiąc niezawodności TCP kończy się, gdy połączenie transportu kończy się, gdy niezawodnej sesji zawiera niezawodności end-to-end.

## <a name="reliable-sessions-and-bindings"></a>Niezawodne sesje i powiązania

Jak wspomniano wcześniej, niezawodnej sesji jest obojętny transportu. Ponadto można utworzyć niezawodnej sesji przez wielu wzorców wymiany wiadomości, takich jak żądanie odpowiedź lub dupleks. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodnej sesji jest udostępniany jako właściwość zestawu powiązań.

Użyj niezawodnej sesji dla punktów końcowych używających:

- Standardowe powiązania transportu oparte na protokole HTTP:

  - `WsHttpBinding`i ujawnia żądanie odpowiedź lub kontraktów jednokierunkowych.

  - Przy użyciu niezawodnej sesji przez żądanie odpowiedź lub kontrakt usługi jednokierunkowe proste.

  - `WsDualHttpBinding`i ujawnia dupleks, żądanie odpowiedź lub kontraktów jednokierunkowych.

  - `WsFederationHttpBinding`i ujawnia żądanie odpowiedź lub kontraktów jednokierunkowych.

- Standardowe powiązania transportu TCP na podstawie:

  - `NetTcpBinding`i ujawnia dupleks, odpowiedź na żądanie lub kontraktów jednokierunkowych.

Użyj niezawodnej sesji w pozostałych powiązaniach przez utworzenie niestandardowego powiązania, takich jak protokół HTTPS (Aby uzyskać więcej informacji dotyczących problemów, zobacz <a href="#reliable-sessions-and-security">niezawodnej sesji i zabezpieczeń</a>) lub powiązania nazwanego potoku.

Można stosu niezawodnej sesji na różnych typach kanału źródłowego, a wynikowy kształtu kanału niezawodnej sesji może być różna. Na kliencie i serwerze typ kanału niezawodnej sesji obsługuje zależy od typu podstawowego kanału używany. W poniższej tabeli wymieniono rodzaje kanały sesji obsługiwane na kliencie funkcji podstawowy typ kanału.

| Obsługiwane typy kanału sesji niezawodnej &#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Tak               | Tak                      | Tak              | Tak                     |
| `IRequestSessionChannel`                        | Tak               | Tak                      | Nie               | Nie                      |
| `IDuplexSessionChannel`                         | Nie                | Nie                       | Tak              | Tak                     |

&#8224; Typów kanałów obsługiwane są dostępne dla ogólnych wartości `TChannel` wartości parametru, która została przekazana do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

W poniższej tabeli wymieniono rodzaje kanały sesji obsługiwane na serwerze funkcji podstawowy typ kanału.

| Obsługiwane typy kanału sesji niezawodnej &#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Tak             | Tak                    | Tak              | Tak                     |
| `IReplySessionChannel`                          | Tak             | Tak                    | Nie               | Nie                      |
| `IDuplexSessionChannel`                         | Nie              | Nie                     | Tak              | Tak                     |

&#8225; Typów kanałów obsługiwane są dostępne dla ogólnych wartości `TChannel` wartości parametru, która została przekazana do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

## <a name="reliable-sessions-and-security"></a>Niezawodne sesje i zabezpieczenia

Zabezpieczanie niezawodnej sesji ważne jest upewnić się, że są uwierzytelniane komunikującymi się stronami (usługa i klient) i wiadomości wymieniane w sesji nie są przez niepowołane. Ponadto jest ważne w celu zapewnienia integralności każdego poszczególnych niezawodnej sesji. Niezawodnej sesji jest chroniona przez powiązanie go do kontekstu zabezpieczeń, który ma reprezentowane i zarządzane przez kanał sesji zabezpieczeń. Bezpieczny kanał zapewnia sesji zabezpieczeń. Tokeny zabezpieczające podczas ustanawiania sesji są następnie używane do zabezpieczania komunikatów w niezawodnej sesji.

W przypadku niezawodnej sesji przez protokół TCP-S, sesji TCP jest powiązany niezawodnej sesji. W związku z tym zabezpieczeń transportu gwarantuje, że zabezpieczeń jest także powiązany niezawodnej sesji. W przypadku ponownego ustanowienia połączenia jest wyłączona.

Jedynym wyjątkiem jest przy użyciu protokołu HTTPS. Sesji protokołu Secure Sockets Layer (SSL) nie jest powiązana z niezawodnej sesji. Nakłada zagrożenie, ponieważ sesje, które współużytkują kontekstu zabezpieczeń (sesji SSL) nie są chronione z innych; to może lub nie może być prawdziwe zagrożenia w zależności od aplikacji.

## <a name="using-reliable-sessions"></a>Przy użyciu sesji niezawodnych

Aby użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodne sesje, tworzenie punktu końcowego z powiązaniem, który obsługuje niezawodnej sesji. Użyj jednej z powiązania dostarczane przez system który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia niezawodnej sesji włączona lub utworzyć własne niestandardowe powiązanie, w tym.

Powiązania zdefiniowane przez system obsługi, które domyślnie włączone niezawodnej sesji zawiera:

- <xref:System.ServiceModel.WSDualHttpBinding>

Powiązania dostarczane przez system, które obsługują niezawodnej sesji jako opcja, ale nie włączysz jedną domyślnie obejmują:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Na przykład sposobu tworzenia niestandardowego powiązania zobacz [porady: Tworzenie niestandardowego wiązania niezawodnej sesji z protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Omówienie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązań, które obsługuje niezawodnej sesji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Kiedy należy używać niezawodnej sesji

Należy zrozumieć, kiedy należy używać niezawodnej sesji w aplikacji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje niezawodnej sesji między punktami końcowymi, które są aktywne i aktywności w tym samym czasie. Jeśli aplikacja wymaga jednego z punktów końcowych, które jest niedostępna do czasu, a następnie użyj kolejki, aby osiągnąć niezawodności.

Jeśli scenariusz wymaga dwa punkty końcowe połączone za pośrednictwem protokołu TCP, TCP może być wystarczające, aby zapewnić wymiany komunikatów niezawodnej. Chociaż nie trzeba używać niezawodnej sesji, ponieważ protokołu TCP zapewnia, że pakiety są odbierane w kolejności i tylko jeden raz.

W przypadku danego scenariusza ma jakiekolwiek z następujących właściwości, następnie należy poważnie skonfigurować przy użyciu niezawodnej sesji.

- Pośredników SOAP, takich jak routery SOAP

- Serwer proxy pośredników lub mostków transportu

- Niestabilne połączenie

- Sesje za pośrednictwem protokołu HTTP

## <a name="see-also"></a>Zobacz także

[Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
[Sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
