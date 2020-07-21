---
title: 'Ograniczenie: protokoły TLS'
description: Dowiedz się więcej na temat wpływu i łagodzenia zmian protokołu TLS, zaczynając od .NET Framework 4,6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475362"
---
# <a name="mitigation-tls-protocols"></a>Ograniczenie: protokoły TLS
Począwszy od .NET Framework 4,6, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> klasy i mogą <xref:System.Net.Security.SslStream?displayProperty=nameWithType> korzystać z jednego z następujących trzech protokołów: TLS 1.0, TLS 1.1 lub TLS 1,2. Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ na:  
  
- Każda aplikacja, która używa protokołu SSL do komunikowania się z serwerem HTTPS lub serwerem gniazda przy użyciu dowolnego z następujących typów: <xref:System.Net.Http.HttpClient> , <xref:System.Net.HttpWebRequest> ,, <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient> i <xref:System.Net.Security.SslStream> .  
  
- Wszystkie aplikacje po stronie serwera, których nie można uaktualnić do obsługi protokołów TLS 1.0, TLS 1.1 i TLS 1,2.  
  
## <a name="mitigation"></a>Ograniczanie ryzyka  
 Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1,2. Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext> można użyć klasy, aby zrezygnować z tej funkcji na dwa sposoby:  
  
- Programowo, przy użyciu fragmentu kodu, takiego jak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Ponieważ <xref:System.Net.ServicePointManager> obiekt jest inicjowany tylko raz, zdefiniowanie tych ustawień zgodności musi być pierwszym działaniem aplikacji.  
  
- Dodając następujący wiersz do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Należy jednak pamiętać, że niezalecane jest, aby zrezygnować z zachowania domyślnego, ponieważ sprawia, że aplikacja jest mniej bezpieczna.  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
