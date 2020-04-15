---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389764"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
Aby skonfigurować punkt końcowy usługi WCF jako interoperacyjny z klientami usługi sieci Web ASP.NET:  
  
- Użyj <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> typu jako typ powiązania dla punktu końcowego usługi.  
  
- Nie należy używać funkcji wywołania zwrotnego i umowy sesji ani zachowań transakcji w punkcie końcowym usługi  
  
Opcjonalnie można włączyć obsługę https i uwierzytelniania klienta na poziomie transportu na powiązanie.  
  
Następujące funkcje <xref:System.ServiceModel.BasicHttpBinding> klasy wymagają funkcjonalności poza profilem podstawowym WS-I 1.1:  
  
- Kodowanie komunikatów mechanizmu optymalizacji transmisji wiadomości <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> (MTOM) kontrolowane przez właściwość. Pozostaw tę właściwość według <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> wartości domyślnej, która nie ma używać MTOM.  
  
- Zabezpieczenia wiadomości kontrolowane <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> przez wartość zapewnia ws-security wsparcie zgodne z WS-I Basic Security Profile 1.0. Pozostaw tę właściwość według <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> wartości domyślnej, która nie ma używać programu WS-Security.  
  
Aby udostępnić metadane usługi WCF ASP.NET, użyj narzędzi do generowania klienta usługi [sieci Web: Narzędzia języka opisu usług sieci Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Narzędzie odnajdowania usług sieci Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)i funkcja **Dodaj odwołanie do sieci Web** w programie Visual Studio. Włącz publikację metadanych. Aby uzyskać więcej informacji, zobacz [Publikowanie punktów końcowych metadanych](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykładowy kod pokazuje, jak dodać punkt końcowy WCF, który jest zgodny z ASP.NET klientami usługi sieci Web w kodzie i, alternatywnie, w pliku konfiguracji.  
  
### <a name="code"></a>Code  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Współdziałanie z usługami ASP.NET w sieci Web](./feature-details/interop-with-aspnet-web-services.md)
