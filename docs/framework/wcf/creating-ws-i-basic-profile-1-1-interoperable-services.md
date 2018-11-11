---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: f32308a17e2934b6884140307074f97e6b51f5f9
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982857"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
Aby skonfigurować punkt końcowy usługi WCF do współdziałać z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obsługi klientów w sieci Web:  
  
-   Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typ jako typ powiązania punktu końcowego usługi.  
  
-   Nie używaj wywołania zwrotnego i funkcje kontraktu sesji lub zachowania transakcji do punktu końcowego usługi  
  
 Opcjonalnie można włączyć obsługę protokołu HTTPS i uwierzytelniania klienta na poziomie transportu w powiązaniu.  
  
 Poniższe funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcji równoważenia obciążenia po przekroczeniu WS-I Basic Profile 1.1:  
  
-   Kodowanie komunikatu mechanizmu optymalizacji transmisji (MTOM) komunikatu w wartości clientauthtrustmode <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> właściwości. Pozostaw tę właściwość jako wartość domyślną, czyli <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> nieużywanie MTOM.  
  
-   Zabezpieczenia w wartości clientauthtrustmode wiadomości <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> wartość zapewnia obsługę protokołu WS-Security zgodne z protokołu WS-I Basic 1.0 profilu zabezpieczeń. Pozostaw tę właściwość jako wartość domyślną, czyli <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> nieużywanie WS-Security.  
  
 Aby udostępnić metadanych dla usługi WCF [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], użyj narzędzia generowania klienta usługi sieci Web: [narzędzia języka opisu usługi sieci Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [narzędzia odnajdywania usług sieci Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)i `Add Web Reference` funkcja w programie Visual Studio; należy włączyć publikowanie metadanych. Aby uzyskać więcej informacji, zobacz [publikowanie punktów końcowych metadanych](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu demonstruje sposób dodawania punktu końcowego WCF, która jest zgodna z [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sieci Web obsługi klientów w kodzie, a także w pliku konfiguracji.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z usługami ASP.NET w sieci Web](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
