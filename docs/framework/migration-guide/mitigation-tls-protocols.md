---
title: 'Ograniczenie: protokoły TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457840"
---
# <a name="mitigation-tls-protocols"></a>Ograniczenie: protokoły TLS
Począwszy od .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą używać jednego z następujących trzech protokołów: Tls1.0, Tls1.1 lub Tls 1.2. Protokół SSL3.0 i szyfr RC4 nie są obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana dotyczy:  
  
- Każda aplikacja, która używa protokołu SSL do rozmów z serwerem HTTPS <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest>lub <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient>serwerem gniazd przy użyciu dowolnego z następujących typów: , , , i <xref:System.Net.Security.SslStream>.  
  
- Każda aplikacja po stronie serwera, których nie można uaktualnić do obsługi tls1.0, Tls1.1 lub Tls 1.2..  
  
## <a name="mitigation"></a>Środki zaradcze  
 Zalecane ograniczenie jest uaktualnienie aplikacji po stronie sever do Tls1.0, Tls1.1 lub Tls 1.2. Jeśli nie jest to możliwe lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext> klasa może służyć do rezygnacji z tej funkcji na dwa sposoby:  
  
- Programowo, używając fragmentu kodu, takiego jak następujące:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Ponieważ <xref:System.Net.ServicePointManager> obiekt jest inicjowany tylko raz, definiowanie tych ustawień zgodności musi być pierwszą rzeczą, jaką robi aplikacja.  
  
- Dodając następujący wiersz do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Należy jednak pamiętać, że rezygnacja z domyślnego zachowania nie jest zalecane, ponieważ sprawia, że aplikacja mniej bezpieczne.  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
