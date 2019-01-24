---
title: Omówienie sesji niezawodnych
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 6dd90ef800daf236d77c419d48c0857ac2d78aa2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548027"
---
# <a name="reliable-sessions-overview"></a>Omówienie sesji niezawodnych

Windows Communication Foundation (WCF) niezawodnej obsługi wiadomości SOAP zapewnia niezawodność transferu wiadomości end-to-end między punktami końcowymi protokołu SOAP. Dzieje się tak w sieciach, które nie jest gwarantowane przez płynną błędów transportu i awarie poziom komunikatu protokołu SOAP. W szczególności zapewnia oparte na sesji pojedynczego i (opcjonalnie) uporządkowane dostarczania wiadomości przesyłane za pośrednictwem pośredników SOAP lub transportu. Oparte na sesji dostarczania zawiera grupowanie komunikatów w sesji z opcjonalnych kolejność komunikatów.

W tym temacie opisano niezawodne sesje, jak i kiedy ich używać oraz jak je zabezpieczyć.

## <a name="wcf-reliable-sessions"></a>Niezawodne sesje programu WCF

Sesje niezawodnej usługi WCF jest implementacją protokołu SOAP niezawodnej obsługi komunikatów, zgodnie z definicją protokołu WS-ReliableMessaging.

Niezawodna obsługa komunikatów WCF SOAP zapewnia end-to-end niezawodnej sesji między dwoma punktami końcowymi, niezależnie od liczby i typu pośredników rozdzielających komunikatów punktów końcowych. Dotyczy to również wszelkich pośredników transportu, które nie używają protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników, które używają protokołu SOAP (na przykład opartego na protokole SOAP routery lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Kanał niezawodnej sesji obsługuje *interaktywne* komunikacji, aby usługi połączone przez kanał taki uruchamiać jednocześnie i wymianę i przetwarzanie komunikatów w warunkach małych opóźnień, oznacza to, w ramach stosunkowo krótka odstępach czasu. To sprzężenia oznacza, że te składniki postęp razem lub zakończyć się niepowodzeniem ze sobą, dlatego bez izolacji udostępniane między nimi.

Sesja niezawodna maskuje dwa rodzaje błędów:

- Protokołu SOAP wiadomości niespodziewanymi awariami, co obejmuje wiadomości utracone lub zduplikowane i komunikaty przychodzące w innej kolejności niż kolejność, w jakiej zostały wysłane.

- Transport błędów.

Sesja niezawodna implementuje protokół WS-ReliableMessaging i okno transfer w pamięci na awarie maska poziom komunikatu protokołu SOAP i ponownie nawiązuje połączenia w przypadku błędów transportu.

Sesja niezawodna zawiera komunikaty protokołu SOAP protokół TCP zapewnia dla pakietów IP. Połączenie gniazda TCP zapewnia liczbie pojedynczej, w określonej kolejności przesyłanie pakietów IP między węzłami. Niezawodny kanał zawiera ten sam typ transferu niezawodne, ale różni się od niezawodności gniazda TCP w następujący sposób:

- Niezawodność wynosi komunikatu protokołu SOAP poziomu, nie dla pakietu arbitralnie wielkości bajtów.

- Niezawodność, jest transport niezależny od, nie tylko dla transferu za pośrednictwem protokołu TCP.

- Niezawodność nie jest powiązany z sesją danego transportu (na przykład sesji połączenia protokołu TCP zapewnia) i można użyć wielu sesji transportu jednocześnie lub sekwencyjnie w okresie istnienia sesji.

- Niezawodna sesja jest między nadawcą i odbiorcą punktów końcowych protokołu SOAP, niezależnie od tego, liczba połączeń wymaganych dla łączności między nimi. Krótko mówiąc niezawodność TCP kończy się, gdy połączenie transportu zostaje zakończona, a niezawodnej sesji zapewnia niezawodność end-to-end.

## <a name="reliable-sessions-and-bindings"></a>Niezawodne sesje i powiązania

Jak wspomniano wcześniej, niezawodnej sesji jest neutralne transportu. Ponadto można utworzyć niezawodnej sesji za pośrednictwem wielu wzorców wymiany wiadomości, takich jak żądanie odpowiedź lub dupleks. Usługi WCF niezawodnej sesji jest udostępniany jako właściwość zestawu powiązania.

Użyj niezawodnej sesji dla punktów końcowych używających:

- Standardowa powiązania transportu oparty na protokole HTTP:

  - `WsHttpBinding` i udostępnić "żądanie-odpowiedź" lub kontraktów jednokierunkowych.

  - Korzystając z niezawodnej sesji za pośrednictwem "żądanie-odpowiedź" lub kontrakt prostą usługę jednokierunkowe.

  - `WsDualHttpBinding` i udostępnić dupleks, "żądanie-odpowiedź" lub kontraktów jednokierunkowych.

  - `WsFederationHttpBinding` i udostępnić "żądanie-odpowiedź" lub kontraktów jednokierunkowych.

- Standardowa powiązania transportu oparte na protokole TCP:

  - `NetTcpBinding` i udostępnić dupleks, odpowiedź na żądanie lub kontraktów jednokierunkowych.

Użyj niezawodnej sesji na innych powiązań, tworzenie niestandardowego powiązania, taki jak HTTPS (Aby uzyskać więcej informacji na temat problemów, zobacz <a href="#reliable-sessions-and-security">sesje niezawodnej i zabezpieczenia</a>) lub powiązania nazwanego potoku.

Użytkownik może utworzyć stos niezawodnej sesji na różnych typów podstawowych kanału i różni się w wynikowej kształtu kanału niezawodnej sesji. Na kliencie i serwerze typ kanału niezawodnej sesji obsługiwane zależy od typu podstawowego kanał używany. W poniższej tabeli wymieniono typy kanałów sesji obsługiwana na komputerze klienckim, w zależności od typu podstawowego kanału.

| Obsługiwane typy kanału niezawodnej sesji&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Tak               | Yes                      | Yes              | Yes                     |
| `IRequestSessionChannel`                        | Yes               | Yes                      | Nie               | Nie                      |
| `IDuplexSessionChannel`                         | Nie                | Nie                       | Yes              | Tak                     |

&#8224;Typy obsługiwanym kanałem są dostępne dla ogólnej wartości `TChannel` wartość parametru, która została przekazana do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

W poniższej tabeli wymieniono typy kanałów sesji obsługiwany na serwerze, w zależności od podstawowego typu kanału.

| Obsługiwane typy kanału niezawodnej sesji&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Tak             | Yes                    | Yes              | Yes                     |
| `IReplySessionChannel`                          | Yes             | Yes                    | Nie               | Nie                      |
| `IDuplexSessionChannel`                         | Nie              | Nie                     | Yes              | Tak                     |

&#8225;Typy obsługiwanym kanałem są dostępne dla ogólnej wartości `TChannel` wartość parametru, która została przekazana do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

## <a name="reliable-sessions-and-security"></a>Niezawodne sesje i zabezpieczenia

Zabezpieczanie niezawodnej sesji ważne jest zapewnienie uwierzytelnieniu komunikujące się strony (usługa i klient) i że nie są w nieuprawniony wiadomości wymieniane w sesji. Ponadto jest ważne, aby zapewnić integralność każdego poszczególnych niezawodnej sesji. Sesja niezawodna jest zabezpieczony przez powiązanie go z kontekstu zabezpieczeń, który reprezentowane i zarządzane przez bezpieczny kanał sesji. Kanał zabezpieczeń zapewnia sesji zabezpieczeń. Tokeny zabezpieczające podczas ustanawiania sesji są następnie używane do zabezpieczenia wiadomości w niezawodnej sesji.

Po niezawodnej sesji za pośrednictwem protokołu TCP-S sesji TCP jest powiązany niezawodnej sesji. W związku z zabezpieczeń transportu gwarantuje, że zabezpieczeń jest także powiązane niezawodnej sesji. W przypadku ponownego ustanowienia połączenia jest wyłączona.

Jedynym wyjątkiem jest, gdy przy użyciu protokołu HTTPS. Sesji protokołu Secure Sockets Layer (SSL) nie jest powiązany z niezawodnej sesji. Nakłada za zagrożenie, ponieważ nie są chronione sesje, które udostępniono w kontekście zabezpieczeń (sesji SSL), od siebie; może to spowodować lub może nie być prawdziwym zagrożeniem w zależności od aplikacji.

## <a name="using-reliable-sessions"></a>Przy użyciu niezawodnej sesji

Aby użyć sesje niezawodnej usługi WCF, należy utworzyć punkt końcowy przy użyciu powiązania, który obsługuje niezawodnej sesji. Użyj jednego z powiązań dostarczanych przez system, udostępnianych przez usługi WCF z niezawodnej sesji włączona lub utworzyć własne niestandardowe powiązanie, które wykonuje to.

Powiązań zdefiniowanych przez system, które obsługują i włączyć domyślne niezawodnej sesji obejmują:

- <xref:System.ServiceModel.WSDualHttpBinding>

Powiązania dostarczane przez system, które obsługują niezawodnej sesji jako opcja, ale nie włączysz jeden domyślnie obejmują:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Na przykład sposobu tworzenia niestandardowego powiązania zobacz [jak: Tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Omówienie powiązań WCF, które obsługuje sesji uwierzytelnianych, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Kiedy należy używać sesji niezawodnych

Należy zrozumieć, kiedy należy używać niezawodnej sesji w aplikacji. Usługi WCF obsługuje niezawodne sesje między punktami końcowymi, które są aktywne i aktywne, w tym samym czasie. Jeśli aplikacja wymaga jednego z punktów końcowych, które być niedostępna przez dany okres czasu, a następnie użyć kolejki, aby osiągnąć niezawodność.

Jeśli scenariusz wymaga dwa punkty końcowe połączone za pośrednictwem protokołu TCP, TCP może być wystarczające, aby zapewnić niezawodne komunikatów. Mimo że nie trzeba używać niezawodnej sesji, ponieważ protokół TCP zapewnia, że pakiety pojawić się w kolejności i tylko jeden raz.

W przypadku danego scenariusza ma jakiekolwiek z następujących właściwości, następnie należy naszych użytkowników bardzo poważnie skonfigurować przy użyciu niezawodnej sesji.

- Pośredników SOAP, takich jak routery protokołu SOAP

- Serwer proxy pośredników lub mostków transportu

- Sporadycznej łączności

- Sesje za pośrednictwem protokołu HTTP

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
