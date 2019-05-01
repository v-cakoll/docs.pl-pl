---
title: 'Środki zaradcze: Protokoły TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70fab3dc418e3eb92e39a7c2b1365e8582b81834
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871260"
---
# <a name="mitigation-tls-protocols"></a>Środki zaradcze: Protokoły TLS
Począwszy od programu .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą użyć jednego z następujących trzech protokołów: Tls1.0, Tls1.1 lub protokołu Tls 1.2. Protokół SSL3.0 i szyfrowania RC4 nie są obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ na:  
  
- Dowolną aplikację, która używa protokołu SSL do komunikacji HTTPS lub serwera gniazda przy użyciu dowolnej z następujących typów: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, i <xref:System.Net.Security.SslStream>.  
  
- Dowolnej aplikacji po stronie serwera, którego nie można uaktualnić do obsługi Tls1.0, Tls1.1 lub protokołu Tls 1.2...  
  
## <a name="mitigation"></a>Ograniczenie  
 Zalecane środki zaradcze jest uaktualnienie aplikacji po stronie serwera do Tls1.0, Tls1.1 lub protokołu Tls 1.2. Jeśli nie jest to możliwe, czy działają aplikacje klienckie <xref:System.AppContext> klasy można zrezygnować z tej funkcji w jednej z dwóch sposobów:  
  
- Programowo korzystając z fragmentu kodu, podobnie do poniższego:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Ponieważ <xref:System.Net.ServicePointManager> obiekt jest zainicjowany tylko raz, definiowania tych ustawień zgodności musi być pierwszą rzeczą, którą aplikacja wykonuje.  
  
- Dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Należy jednak pamiętać, że rezygnacja z domyślnym zachowaniem jest niezalecane, ponieważ dzięki niemu aplikacja mniej bezpieczna opcja.  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
