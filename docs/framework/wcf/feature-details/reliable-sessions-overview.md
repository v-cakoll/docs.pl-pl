---
title: Omówienie sesji niezawodnych
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: a85a34c5e2ec7928c01586e4b01cdf5e90e896a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601091"
---
# <a name="reliable-sessions-overview"></a>Omówienie sesji niezawodnych

Usługa Windows Communication Foundation (WCF) funkcja niezawodna obsługa protokołu SOAP zapewnia kompleksową niezawodność przesyłania komunikatów między punktami końcowymi protokołu SOAP. Robi to w przypadku sieci, które są wiarygodne przez przechodzące błędy transportu i błędy poziomu komunikatów protokołu SOAP. W szczególności zapewnia oparte na sesji, pojedyncze i (opcjonalnie) uporządkowane dostarczanie komunikatów wysyłanych przez pośredników protokołu SOAP lub transportu. Dostarczanie oparte na sesji zapewnia grupowanie komunikatów w sesji przy użyciu opcjonalnej kolejności komunikatów.

W tym temacie opisano niezawodne sesje, sposób i czas ich używania oraz sposób ich zabezpieczania.

## <a name="wcf-reliable-sessions"></a>Niezawodne sesje WCF

Niezawodne sesje programu WCF to implementacja niezawodnych komunikatów protokołu SOAP, zgodnie z definicją protokołu WS-ReliableMessaging.

Niezawodna obsługa protokołu SOAP WCF zapewnia kompleksową, niezawodną sesję między dwoma punktami końcowymi, niezależnie od liczby lub typu pośredników, które oddzielają punkty końcowe obsługi komunikatów. Dotyczy to wszystkich pośredników transportu, które nie używają protokołu SOAP (na przykład proxy HTTP) ani pośredników korzystających z protokołu SOAP (na przykład routerów lub mostków opartych na protokole SOAP), które są wymagane do przepływu komunikatów między punktami końcowymi. Kanał niezawodnej sesji obsługuje komunikację *interaktywną* , dzięki czemu usługi połączone przez taki kanał działają współbieżnie i wymieniają i przetwarzają komunikaty w warunkach o małym opóźnieniu, czyli w stosunkowo krótkich odstępach czasu. Ten sprzężenie oznacza, że te składniki sprawiają postęp razem lub kończą się niepowodzeniem, dlatego nie jest zapewniona żadna izolacja między nimi.

Niezawodne maski sesji dwa rodzaje awarii:

- Błędy poziomu komunikatów protokołu SOAP, w tym utracone lub zduplikowane komunikaty i komunikaty, które nadeszły w innej kolejności od kolejności, w której zostały wysłane.

- Błędy transportu.

Niezawodna sesja implementuje protokół WS-ReliableMessaging i okno transferu w pamięci w celu zamaskowania błędów na poziomie komunikatu protokołu SOAP i ponownego ustanawiania połączeń w przypadku awarii transportu.

Niezawodna sesja zapewnia komunikaty protokołu SOAP, które są dostępne dla pakietów IP przez protokół TCP. Połączenie gniazda TCP udostępnia pojedynczą, w kolejności transfer pakietów IP między węzłami. Niezawodny kanał zapewnia ten sam typ niezawodnego transferu, ale różni się od niezawodności gniazda TCP w następujący sposób:

- Niezawodność jest na poziomie komunikatu protokołu SOAP, a nie w przypadku niezależnego rozmiaru pakietu bajtów.

- Niezawodność jest niezależne od transportu, a nie tylko za transfer przez TCP.

- Niezawodność nie jest powiązana z konkretną sesją transportową (na przykład jest to sesja, która zapewnia połączenie TCP) i może korzystać z wielu sesji transportu współbieżnie lub sekwencyjnie w okresie istnienia niezawodnej sesji.

- Niezawodna sesja dotyczy punktów końcowych protokołu SOAP nadawcy i odbiornika, niezależnie od liczby połączeń transportowych wymaganych do połączenia między nimi. W skrócie następuje niezawodność protokołu TCP, w której kończy się połączenie transportowe, a Niezawodna sesja zapewnia kompleksową niezawodność.

## <a name="reliable-sessions-and-bindings"></a>Niezawodne sesje i powiązania

Jak wspomniano wcześniej, niezawodnej sesji jest transport neutralny. Ponadto można nawiązać niezawodne sesje za pośrednictwem wielu różnych wzorców wymiany komunikatów, takich jak żądanie-odpowiedź lub dupleks. Niezawodna sesja WCF jest uwidaczniana jako właściwość zestawu powiązań.

Używaj niezawodnej sesji dla punktów końcowych, które używają:

- Standardowe powiązania transportu oparte na protokole HTTP:

  - `WsHttpBinding`i udostępniaj kontrakty żądanie-odpowiedź lub jednokierunkowe.

  - W przypadku korzystania z niezawodnej sesji w ramach żądania odpowiedzi lub prostego kontraktu jednokierunkowego.

  - `WsDualHttpBinding`i udostępniaj dwustronne, odpowiedzi na żądania lub kontrakty jednokierunkowe.

  - `WsFederationHttpBinding`i udostępniaj kontrakty żądanie-odpowiedź lub jednokierunkowe.

- Standardowe powiązania transportu oparte na protokole TCP:

  - `NetTcpBinding`Udostępnianie dupleksu, odpowiedź na żądanie lub kontrakty jednokierunkowe.

Używaj niezawodnej sesji na innych powiązaniach, tworząc niestandardowe powiązanie, takie jak HTTPS (Aby uzyskać więcej informacji o problemach, zobacz <a href="#reliable-sessions-and-security">niezawodne sesje i zabezpieczenia</a>) lub powiązanie nazwanego potoku.

Można układać niezawodną sesję na różnych typach kanałów bazowych, a kształt wyników niezawodnych sesji jest różny. Na kliencie i serwerze typ obsługiwanego kanału niezawodnej sesji zależy od typu używanego kanału. Poniższa tabela zawiera listę typów kanałów sesji obsługiwanych na kliencie jako funkcji typu kanału bazowego.

| Obsługiwane typy kanałów niezawodnej sesji&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Tak               | Tak                      | Tak              | Tak                     |
| `IRequestSessionChannel`                        | Tak               | Tak                      | Nie               | Nie                      |
| `IDuplexSessionChannel`                         | Nie                | Nie                       | Tak              | Tak                     |

&#8224;obsługiwane typy kanałów to wartości dostępne dla wartości parametru generycznego `TChannel` , który jest przesyłany do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

Poniższa tabela zawiera listę typów kanałów sesji obsługiwanych na serwerze jako funkcji typu kanału bazowego.

| Obsługiwane typy kanałów niezawodnej sesji&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Tak             | Tak                    | Tak              | Tak                     |
| `IReplySessionChannel`                          | Tak             | Tak                    | Nie               | Nie                      |
| `IDuplexSessionChannel`                         | Nie              | Nie                     | Tak              | Tak                     |

&#8225;obsługiwane typy kanałów to wartości dostępne dla wartości parametru generycznego `TChannel` , który jest przesyłany do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

## <a name="reliable-sessions-and-security"></a>Niezawodne sesje i zabezpieczenia

Zabezpieczanie niezawodnej sesji jest ważne, aby upewnić się, że osoby komunikujące się (usługa i klient) są uwierzytelniani oraz że komunikaty wymieniane w sesji nie zostały naruszone. Ponadto ważne jest zapewnienie integralności każdej indywidualnej niezawodnej sesji. Niezawodna sesja jest zabezpieczona przez powiązanie jej z kontekstem zabezpieczeń reprezentowanym i zarządzanym przez kanał sesji zabezpieczeń. Kanał zabezpieczeń zawiera sesję zabezpieczeń. Tokeny zabezpieczające wymieniane podczas ustanawiania sesji są następnie używane do zabezpieczania komunikatów w niezawodnej sesji.

Gdy Niezawodna sesja odbywa się za pośrednictwem protokołu TCP-S, sesja TCP jest powiązana z niezawodną sesją. W związku z tym bezpieczeństwo transportu gwarantuje, że zabezpieczenia są również powiązane z niezawodną sesją. W takim przypadku ponowne ustanowienie połączenia jest wyłączone.

Jedynym wyjątkiem jest użycie protokołu HTTPS. Sesja SSL (SSL) nie jest powiązana z niezawodną sesją. Stanowi to zagrożenie, ponieważ sesje współużytkujące kontekst zabezpieczeń (sesja SSL) nie są chronione ze sobą; może to być nieprawdziwe zagrożenie w zależności od aplikacji.

## <a name="using-reliable-sessions"></a>Korzystanie z sesji niezawodnych

Aby korzystać z niezawodnych sesji WCF, należy utworzyć punkt końcowy z powiązaniem obsługującym niezawodną sesję. Użyj jednego z powiązań dostarczonych przez system, które obsługuje usługa WCF z włączonymi niezawodnymi sesjami lub Utwórz własne niestandardowe powiązania.

Zdefiniowane przez system powiązania, które domyślnie obsługują i umożliwiają niezawodne sesje, obejmują:

- <xref:System.ServiceModel.WSDualHttpBinding>

Powiązania dostarczone przez system obsługujące niezawodną sesję jako opcję, ale nie włączaj go domyślnie obejmują:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Aby zapoznać się z przykładem tworzenia niestandardowego powiązania, zobacz [How to: Create an Custom niezawodnej sesji powiązania z protokołem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).

Omówienie powiązań programu WCF, które obsługują niezawodne sesje, można znaleźć w temacie [powiązania dostarczone przez system](../system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Kiedy używać sesji niezawodnych

Ważne jest, aby zrozumieć, kiedy należy używać niezawodnych sesji w aplikacji. WCF obsługuje niezawodne sesje między punktami końcowymi, które są aktywne i działają w tym samym czasie. Jeśli aplikacja wymaga jednego z punktów końcowych, na czas niedostępności, użyj kolejek do osiągnięcia niezawodności.

Jeśli scenariusz wymaga dwóch punktów końcowych połączonych za pośrednictwem protokołu TCP, protokół TCP może być wystarczający do zapewnienia niezawodnej wymiany komunikatów. Mimo że nie jest konieczne używanie niezawodnej sesji, ponieważ protokół TCP zapewnia, że pakiety docierają w kolejności i tylko raz.

Jeśli Twój Scenariusz ma jedną z następujących cech, należy zastanowić się, że należy rozważyć użycie niezawodnej sesji.

- Pośredniki protokołu SOAP, takie jak routery SOAP

- Pośredniczące proxy lub mosty transportowe

- Sporadyczna łączność

- Sesje za pośrednictwem protokołu HTTP

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług i klientów za pomocą powiązań](../using-bindings-to-configure-services-and-clients.md)
- [Sesja niezawodna WS](../samples/ws-reliable-session.md)
