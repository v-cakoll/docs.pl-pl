---
title: Środki zaradcze Protokoły TLS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e98b447028ef9fa96233a71133aa82184d83cec8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779157"
---
# <a name="mitigation-tls-protocols"></a>Środki zaradcze Protokoły TLS
Począwszy od .NET Framework 4,6, <xref:System.Net.ServicePointManager?displayProperty=nameWithType> klasy i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> mogą korzystać z jednego z trzech następujących protokołów: TLS 1.0, TLS 1.1 lub TLS 1,2. Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ na:  
  
- Każda aplikacja, która używa protokołu SSL do komunikowania się z serwerem HTTPS lub serwerem gniazda przy użyciu dowolnego z następujących <xref:System.Net.Http.HttpClient>typów <xref:System.Net.HttpWebRequest>: <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>,, <xref:System.Net.Security.SslStream>i.  
  
- Wszystkie aplikacje po stronie serwera, których nie można uaktualnić do obsługi protokołów TLS 1.0, TLS 1.1 i TLS 1,2.  
  
## <a name="mitigation"></a>Ograniczenie  
 Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1,2. Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext> można użyć klasy, aby zrezygnować z tej funkcji na dwa sposoby:  
  
- Programowo, przy użyciu fragmentu kodu, takiego jak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <xref:System.Net.ServicePointManager> Ponieważ obiekt jest inicjowany tylko raz, zdefiniowanie tych ustawień zgodności musi być pierwszym działaniem aplikacji.  
  
- Dodając następujący wiersz do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Należy jednak pamiętać, że niezalecane jest, aby zrezygnować z zachowania domyślnego, ponieważ sprawia, że aplikacja jest mniej bezpieczna.  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6.md)
