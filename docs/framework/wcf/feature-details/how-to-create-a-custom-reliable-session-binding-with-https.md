---
title: "Porady: tworzenie powiązania niestandardowego niezawodnej sesji z protokołu HTTPS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6e891f266a8159a6367a0a936d6ba11197484267
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Porady: tworzenie powiązania niestandardowego niezawodnej sesji z protokołu HTTPS

W tym temacie przedstawiono użycie zabezpieczeń transportu Secure Sockets Layer (SSL) z sesji niezawodnej. Aby użyć niezawodnej sesji przez protokół HTTPS, należy utworzyć niestandardowego powiązania, który używa niezawodnej sesji i transportu HTTPS. Możesz włączyć niezawodnej sesji imperatively przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura używa plików konfiguracji klienta i usługi, aby umożliwić niezawodnej sesji i [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elementu.

Część klucza tej procedury jest to, że  **\<punktu końcowego >** element konfiguracji zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji niestandardowego powiązania o nazwie `reliableSessionOverHttps`. [  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby określić, że niezawodnej sesji i transportu HTTPS są używane przez dołączenie  **\< reliableSession >** i  **\<httpsTransport >** elementów.

Dla źródła kopię w tym przykładzie [niestandardowe powiązanie niezawodnej sesji przez protokół HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Skonfiguruj usługę z CustomBinding do niezawodnej sesji za pomocą protokołu HTTPS

1. Definiowanie kontraktu usługi dla typu usługi.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implementowanie kontraktu usługi w klasie usługi. Należy pamiętać, że informacje powiązania lub adres nie jest określona wewnątrz implementacji usługi. Nie są wymagane do pisania kodu, które można pobrać informacji o adresie lub powiązanie z pliku konfiguracji.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Utwórz *Web.config* pliku do konfigurowania punktu końcowego dla `CalculatorService` z niestandardowego powiązania o nazwie `reliableSessionOverHttps` używającą transportu HTTPS i niezawodnej sesji.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Utwórz *Service.svc* pliku, który zawiera wiersz:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Miejsce *Service.svc* pliku w katalogu wirtualnym programu Internet Information Services (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurowanie klienta z CustomBinding do niezawodnej sesji za pomocą protokołu HTTPS

1. Użyj [narzędzie do obsługi metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Aplikacja wygenerowanego klienta zawiera również implementacja `ClientCalculator`. Należy pamiętać, że informacje adres i powiązanie nie jest określona wewnątrz implementacji usługi. Nie są wymagane do pisania kodu, aby pobrać informacje adres i powiązanie z pliku konfiguracji.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Konfigurowanie niestandardowego powiązania o nazwie `reliableSessionOverHttps` korzystać z transportu HTTPS i niezawodnej sesji.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Utwórz wystąpienie `ClientCalculator` w aplikacji, a następnie wywołać operacji usługi.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Kompilowanie i uruchamianie klienta.  

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework

Ponieważ certyfikat użyty w tym przykładzie jest utworzone za pomocą certyfikatu testowego *Makecert.exe*, alert zabezpieczeń zostanie wyświetlony podczas próby dostępu adres HTTPS, takich jak `https://localhost/servicemodelsamples/service.svc`, w przeglądarce.

## <a name="see-also"></a>Zobacz także

[Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
