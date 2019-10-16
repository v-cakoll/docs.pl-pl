---
title: Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: eb1cd12c45a276d5c3cb14f89205fff618121abc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320131"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I
Aby skonfigurować punkt końcowy usługi WCF do współdziałania z klientami usługi sieci Web ASP.NET:  
  
- Użyj typu <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> jako typu powiązania dla punktu końcowego usługi.  
  
- Nie używaj funkcji wywołania zwrotnego i kontraktu sesji ani zachowań transakcji w punkcie końcowym usługi  
  
 Opcjonalnie można włączyć obsługę uwierzytelniania przy użyciu protokołu HTTPS i klienta na poziomie transportu.  
  
 Następujące funkcje klasy <xref:System.ServiceModel.BasicHttpBinding> wymagają funkcji poza WS-I Basic Profile 1,1:  
  
- Kodowanie komunikatów mechanizmu optymalizacji transmisji wiadomości (MTOM) kontrolowane przez właściwość <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>. Pozostaw tę właściwość domyślną wartością, która jest <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>, aby nie używać MTOM.  
  
- Zabezpieczenia komunikatów kontrolowane przez wartość <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> zapewnia obsługę WS-Security zgodną z profilem zabezpieczeń WS-I Basic 1,0. Pozostaw tę właściwość domyślną wartością, która jest <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>, aby nie używać usługi WS-Security.  
  
 Aby uzyskać dostęp do metadanych usługi WCF ASP.NET, użyj narzędzi do generowania klienta usługi sieci Web: [narzędzia Web Services Description Language (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), narzędzia do [odnajdywania usług sieci Web (Disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)i funkcji `Add Web Reference` w programie Visual Studio; należy włączyć publikację metadanych. Aby uzyskać więcej informacji, zobacz [Publikowanie punktów końcowych metadanych](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykładowy kod pokazuje, jak dodać punkt końcowy WCF, który jest zgodny z klientami usługi sieci Web ASP.NET w kodzie i, Alternatywnie, w pliku konfiguracji.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z usługami ASP.NET w sieci Web](./feature-details/interop-with-aspnet-web-services.md)
