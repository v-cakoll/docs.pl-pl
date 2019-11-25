---
title: 'Instrukcje: Tworzenie niestandardowego powiązania niezawodnej sesji z protokołem HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 26466a97ae44e6852c189d0b72bdba1b93d86141
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141737"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Instrukcje: Tworzenie niestandardowego powiązania niezawodnej sesji z protokołem HTTPS

W tym temacie przedstawiono sposób korzystania z zabezpieczeń transportu SSL (SSL) z niezawodnymi sesjami. Aby używać niezawodnej sesji za pośrednictwem protokołu HTTPS, należy utworzyć niestandardowe powiązanie, które korzysta z niezawodnej sesji i transportu HTTPS. Niezawodne sesje można wykonać samodzielnie za pomocą kodu lub deklaratywnie w pliku konfiguracji. Ta procedura powoduje użycie plików konfiguracji klienta i usługi w celu włączenia niezawodnej sesji i [ **\<elementu > httpsTransport**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) .

Najważniejszym elementem tej procedury jest, że element konfiguracji **> punktu końcowego\<** zawiera atrybut `bindingConfiguration` odwołujący się do konfiguracji niestandardowego powiązania o nazwie `reliableSessionOverHttps`. Element konfiguracji [ **> powiązania\<** ](../../configure-apps/file-schema/wcf/bindings.md) odwołuje się do tej nazwy, aby określić, że Niezawodna sesja i transport HTTPS są używane przez dołączenie **\<reliableSession >** i **\<httpsTransport >** elementów.

Aby uzyskać kopię źródła tego przykładu, zobacz [niestandardowe powiązania niezawodnej sesji za pośrednictwem protokołu HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie usługi z niestandardową do korzystania z niezawodnej sesji z protokołem HTTPS

1. Zdefiniuj kontrakt usługi dla typu usługi.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Zaimplementuj kontrakt usługi w klasie usługi. Należy zauważyć, że adres lub informacje o powiązaniu nie są określone w implementacji usługi. Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Utwórz plik *Web. config* , aby skonfigurować punkt końcowy dla `CalculatorService` przy użyciu niestandardowego powiązania o nazwie `reliableSessionOverHttps`, który używa niezawodnej sesji i transportu HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Utwórz plik *usługi SVC* , który zawiera wiersz:

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. Umieść plik *Service. svc* w katalogu wirtualnym Internet Information Services (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie klienta z niestandardową do korzystania z niezawodnej sesji z protokołem HTTPS

1. Użyj [Narzędzia metadanych ServiceModel (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Wygenerowany klient zawiera interfejs `ICalculator`, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Wygenerowana aplikacja kliencka zawiera również implementację `ClientCalculator`. Należy zauważyć, że adres i informacje o powiązaniu nie są określone w implementacji usługi. Nie trzeba pisać kodu w celu pobrania informacji o adresie i powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Skonfiguruj niestandardowe powiązanie o nazwie `reliableSessionOverHttps`, aby korzystać z transportu HTTPS i sesji niezawodnych.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie Wywołaj operacje usługi.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Kompiluj i uruchom klienta.  

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym przy użyciu programu *Makecert. exe*, podczas próby uzyskania dostępu do adresu https, takiego jak `https://localhost/servicemodelsamples/service.svc`, w przeglądarce zostanie wyświetlony alert zabezpieczeń.

## <a name="see-also"></a>Zobacz także

- [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
