---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 06a59c7457c0367d421cb46e33cb67f8fa039c7d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879183"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
Aby skonfigurować punkt końcowy usługi WCF do współdziałać z klientami usługi ASP.NET w sieci Web:  
  
- Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ powiązania punktu końcowego usługi.  
  
- Nie używaj wywołania zwrotnego i funkcje kontraktu sesji lub zachowania transakcji do punktu końcowego usługi  
  
 Opcjonalnie można włączyć obsługę protokołu HTTPS i uwierzytelniania klienta na poziomie transportu w powiązaniu.  
  
 Poniższe funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcji równoważenia obciążenia po przekroczeniu WS-I Basic Profile 1.1:  
  
- Kodowanie komunikatu mechanizmu optymalizacji transmisji (MTOM) komunikatu w wartości clientauthtrustmode <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwości. Pozostaw tę właściwość jako wartość domyślną, czyli <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nieużywanie MTOM.  
  
- Zabezpieczenia w wartości clientauthtrustmode wiadomości <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> wartość zapewnia obsługę protokołu WS-Security zgodne z protokołu WS-I Basic 1.0 profilu zabezpieczeń. Pozostaw tę właściwość jako wartość domyślną, czyli <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nieużywanie WS-Security.  
  
 Aby udostępnić metadanych dla usługi WCF do platformy ASP.NET, należy użyć narzędzia generowania klienta usługi sieci Web: [Narzędzia języka opisu usługi (Wsdl.exe) w sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [narzędzia odnajdywania usług sieci Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)i `Add Web Reference` funkcja w programie Visual Studio; należy włączyć publikowanie metadanych. Aby uzyskać więcej informacji, zobacz [publikowanie punktów końcowych metadanych](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu pokazuje, jak można dodać punktu końcowego WCF, która jest zgodna z klientami usługi sieci Web platformy ASP.NET w kodzie, a także w pliku konfiguracji.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z usługami ASP.NET w sieci Web](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
