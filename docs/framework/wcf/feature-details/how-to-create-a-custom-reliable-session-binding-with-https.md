---
title: 'Instrukcje: tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039536"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Instrukcje: tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS

W tym temacie przedstawiono korzystanie z zabezpieczeń transportu protokołu Secure Sockets Layer (SSL) przy użyciu niezawodnej sesji. Aby użyć niezawodnej sesji za pośrednictwem protokołu HTTPS, należy utworzyć niestandardowe powiązanie, które korzysta z niezawodnej sesji i transportu HTTPS. Niezawodna sesja zostanie włączone, obowiązkowo przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura wykorzystuje pliki konfiguracji klienta i usługi, aby umożliwić niezawodnej sesji i [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elementu.

Jest to kluczowa część tej procedury, że  **\<punktu końcowego >** element konfiguracji zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania niestandardowego, o nazwie `reliableSessionOverHttps`. [  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby określić, że transportu HTTPS i niezawodnej sesji są używane przez dołączenie  **\< reliableSession >** i  **\<httpsTransport >** elementów.

Źródło kopię w tym przykładzie można zobaczyć [niestandardowe powiązanie niezawodnej sesji za pośrednictwem protokołu HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie usługi przy użyciu CustomBinding niezawodnej sesji za pomocą protokołu HTTPS

1. Definiowanie kontraktu usługi dla typu usługi.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implementowanie kontraktu usługi, w klasie usługi. Należy pamiętać, że informacji adres lub powiązanie nie jest określona wewnątrz implementacji usługi. Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązania informacji z pliku konfiguracji.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Tworzenie *Web.config* pliku, aby skonfigurować punkt końcowy dla `CalculatorService` za pomocą niestandardowego powiązania o nazwie `reliableSessionOverHttps` używającej transportu HTTPS i niezawodnej sesji.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Tworzenie *Service.svc* pliku zawierające następujący wiersz:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Miejsce *Service.svc* pliku w katalogu wirtualnego Internet Information Services (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie klienta za pomocą CustomBinding niezawodnej sesji za pomocą protokołu HTTPS

1. Użyj [narzędzie do metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod z metadanych usługi.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Aplikacja wygenerowanego klienta zawiera również implementację `ClientCalculator`. Należy pamiętać, że informacje dotyczące adresów i powiązanie nie jest określona wewnątrz implementacji usługi. Nie są wymagane, aby napisać kod, aby pobrać adres i powiązanie informacji z pliku konfiguracji.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Konfigurowanie niestandardowego powiązania o nazwie `reliableSessionOverHttps` używać transportu HTTPS i sesje niezawodne.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Utwórz wystąpienie obiektu `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Kompilowanie i uruchamianie klienta.  

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą certyfikatu testowego *Makecert.exe*, alert zabezpieczeń, zostanie wyświetlony podczas próby dostępu do adres HTTPS, takich jak `https://localhost/servicemodelsamples/service.svc`, z poziomu przeglądarki.

## <a name="see-also"></a>Zobacz także

- [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
