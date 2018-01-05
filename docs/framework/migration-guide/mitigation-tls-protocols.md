---
title: "Ograniczenie: protokoły TLS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a1100e40edb700d51fe907d3dc94c6216c4ebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-tls-protocols"></a>Ograniczenie: protokoły TLS
W programie .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą użyć jednego z trzech następujących protokołów: Tls1.0, Tls1.1 lub protokołu Tls 1.2. Protokół SSL3.0 i szyfrowania RC4 nie są obsługiwane.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana wpływa na:  
  
-   Dowolną aplikację, która używa protokołu SSL do komunikowania się HTTPS lub serwera gniazda przy użyciu dowolnego z następujących typów: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, i <xref:System.Net.Security.SslStream>.  
  
-   Dowolną aplikację po stronie serwera, którego nie można uaktualnić do obsługi Tls1.0, Tls1.1 lub protokołu Tls 1.2.  
  
## <a name="mitigation"></a>Ograniczenie  
 Ograniczenie zalecane jest uaktualnienie aplikacji po stronie serwera do Tls1.0, Tls1.1 lub protokołu Tls 1.2. Jeśli nie jest to możliwe, czy aplikacje klienckie są dzielone, <xref:System.AppContext> klasy można zrezygnować z tej funkcji w jeden z dwóch sposobów:  
  
-   Programowo używając fragment kodu, takie jak następujące:  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     Ponieważ <xref:System.Net.ServicePointManager> obiekt został zainicjowany tylko raz, definiowania tych ustawień zgodności należy najpierw jest aplikacja.  
  
-   Dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 Należy jednak pamiętać, że rezygnacja z domyślne zachowanie nie jest zalecane, ponieważ ułatwia aplikacji mniej bezpieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
