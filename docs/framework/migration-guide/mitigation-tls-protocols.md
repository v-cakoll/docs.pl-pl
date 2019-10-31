---
title: 'Ograniczenie: protokoły TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 2a2f95be92ec08185f627e862b0f62e40a1d764b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126142"
---
# <a name="mitigation-tls-protocols"></a>Ograniczenie: protokoły TLS
Począwszy od .NET Framework 4,6, klasy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> mogą korzystać z jednego z następujących trzech protokołów: TLS 1.0, TLS 1.1 lub TLS 1,2. Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ na:  
  
- Każda aplikacja, która używa protokołu SSL do komunikowania się z serwerem HTTPS lub serwerem gniazda przy użyciu dowolnego z następujących typów: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>i <xref:System.Net.Security.SslStream>.  
  
- Wszystkie aplikacje po stronie serwera, których nie można uaktualnić do obsługi protokołów TLS 1.0, TLS 1.1 i TLS 1,2.  
  
## <a name="mitigation"></a>Ograniczenie  
 Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1,2. Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, można użyć klasy <xref:System.AppContext>, aby zrezygnować z tej funkcji na jeden z dwóch sposobów:  
  
- Programowo, przy użyciu fragmentu kodu, takiego jak:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Ponieważ obiekt <xref:System.Net.ServicePointManager> jest zainicjowany tylko raz, zdefiniowanie tych ustawień zgodności musi być pierwszym działaniem aplikacji.  
  
- Dodając następujący wiersz do sekcji [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) pliku App. config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Należy jednak pamiętać, że niezalecane jest, aby zrezygnować z zachowania domyślnego, ponieważ sprawia, że aplikacja jest mniej bezpieczna.  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6.md)
