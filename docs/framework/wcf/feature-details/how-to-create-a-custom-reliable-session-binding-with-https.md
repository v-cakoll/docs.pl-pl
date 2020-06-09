---
title: 'Instrukcje: tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 70f8f4f33626ab0d1705e03750bfd9baa324e60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598999"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Instrukcje: tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS

W tym temacie przedstawiono sposób korzystania z zabezpieczeń transportu SSL (SSL) z niezawodnymi sesjami. Aby używać niezawodnej sesji za pośrednictwem protokołu HTTPS, należy utworzyć niestandardowe powiązanie, które korzysta z niezawodnej sesji i transportu HTTPS. Niezawodne sesje można wykonać samodzielnie za pomocą kodu lub deklaratywnie w pliku konfiguracji. Ta procedura powoduje użycie plików konfiguracji klienta i usługi w celu włączenia niezawodnej sesji i [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) elementu.

Kluczową częścią tej procedury jest to, że **\<endpoint>** element Configuration zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji niestandardowego powiązania o nazwie `reliableSessionOverHttps` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element konfiguracji odwołuje się do tej nazwy, aby określić, że Niezawodna sesja i transport HTTPS są używane przez włączenie **\<reliableSession>** **\<httpsTransport>** elementów i.

Aby uzyskać kopię źródła tego przykładu, zobacz [niestandardowe powiązania niezawodnej sesji za pośrednictwem protokołu HTTPS](../samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie usługi z niestandardową do korzystania z niezawodnej sesji z protokołem HTTPS

1. Zdefiniuj kontrakt usługi dla typu usługi.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Zaimplementuj kontrakt usługi w klasie usługi. Należy zauważyć, że adres lub informacje o powiązaniu nie są określone w implementacji usługi. Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Utwórz plik *Web. config* w celu skonfigurowania punktu końcowego dla `CalculatorService` niestandardowego powiązania o nazwie `reliableSessionOverHttps` , który używa niezawodnej sesji i transportu HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Utwórz plik *usługi SVC* , który zawiera wiersz:

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. Umieść plik *Service. svc* w katalogu wirtualnym Internet Information Services (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie klienta z niestandardową do korzystania z niezawodnej sesji z protokołem HTTPS

1. Użyj [Narzędzia metadanych ServiceModel (*Svcutil. exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Wygenerowana aplikacja kliencka zawiera również implementację programu `ClientCalculator` . Należy zauważyć, że adres i informacje o powiązaniu nie są określone w implementacji usługi. Nie trzeba pisać kodu w celu pobrania informacji o adresie i powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Skonfiguruj niestandardowe powiązanie o nazwie `reliableSessionOverHttps` do korzystania z transportu HTTPS i sesji niezawodnych.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Utwórz wystąpienie elementu `ClientCalculator` w aplikacji, a następnie Wywołaj operacje usługi.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Kompiluj i uruchom klienta.  

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym za pomocą *Makecert. exe*, podczas próby uzyskania dostępu do adresu https, takiego jak `https://localhost/servicemodelsamples/service.svc` , z przeglądarki, pojawia się Alert zabezpieczeń.

## <a name="see-also"></a>Zobacz też

- [Niezawodne sesje](reliable-sessions.md)
