---
title: Opis wygenerowanego kodu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 8a28b52d786793308d8609704b564b75f23d95d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501359"
---
# <a name="understanding-generated-client-code"></a>Opis wygenerowanego kodu klienta
[Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje kod klienta i pliku konfiguracji aplikacji klienta do użycia z tworzeniem aplikacji klienckich. Ten temat zawiera przegląd przykładów wygenerowanego kodu dla scenariuszy kontraktu usługi standardowa. Aby uzyskać więcej informacji dotyczących tworzenia aplikacji klienta przy użyciu wygenerowanego kodu, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Omówienie  
 Jeśli używasz programu Visual Studio do generowania typów klienta usługi Windows Communication Foundation (WCF) w projekcie, zwykle nie trzeba sprawdzić kod wygenerowanego klienta. Jeśli nie używasz Środowisko deweloperskie, który wykonuje te same usługi dla Ciebie, umożliwia narzędzia, takiego jak Svcutil.exe generowanie kodu klienta, a następnie użyj tego kodu do opracowywania aplikacji klienta.  
  
 Ponieważ Svcutil.exe ma wiele opcji, które modyfikują informacji wygenerowanego typu, w tym temacie omówiono w nim wszystkie scenariusze. Następujące zadania standardowe wymaga jednak lokalizowanie wygenerowanego kodu:  
  
-   Identyfikowanie interfejsy kontraktu usługi.  
  
-   Identyfikowanie klasy klienta WCF.  
  
-   Identyfikowanie typów danych.  
  
-   Identyfikowania na kontraktach wywołania zwrotnego dla usługi dwukierunkowe.  
  
-   Identyfikowanie interfejsu kanału kontraktu usługi pomocnika.  
  
### <a name="finding-service-contract-interfaces"></a>Interfejsy kontraktu usługi wyszukiwanie  
 Aby zlokalizować interfejsów, które modelu kontraktów usług, wyszukaj interfejsów, które są oznaczone ikoną z <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atrybutu. Często ten atrybut może być trudne do zlokalizowania z szybkiego odczytu z powodu obecności innych atrybutów i jawne właściwości ustawione na ten sam atrybut. Należy pamiętać, że interfejsu kontraktu usługi i interfejsu kontraktu klienta są dwa różne typy. Poniższy przykład kodu pokazuje kontrakt usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Poniższy przykład kodu pokazuje ten sam kontrakt usługi, tak jak w przypadku Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Można użyć interfejsu kontraktu usługi wygenerowanego wraz z programem <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> klasy można utworzyć obiektu kanału WCF, z którym do wywołania operacji usługi. Aby uzyskać więcej informacji, zobacz [porady: używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Znajdowanie klasy klienta WCF  
 Aby zlokalizować klasy klienta WCF, która implementuje kontraktu usługi, którego chcesz użyć, wyszukaj rozszerzenie <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, gdzie parametr typu kontraktu usługi interfejs ten można wcześniej znajduje się i który rozszerza interfejs. Poniższy kod przedstawia przykład <xref:System.ServiceModel.ClientBase%601> klasy typu `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Można użyć tej klasy klienta WCF, tworząc nowe wystąpienie i wywoływania metod, które implementuje. Te metody wywołania operacji usługi, z którego został zaprojektowany i skonfigurowane do interakcji. Aby uzyskać więcej informacji, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Jeśli SvcUtil.exe wygeneruje klasy klienta WCF, dodaje <xref:System.Diagnostics.DebuggerStepThroughAttribute> do klasy klienta, który uniemożliwia debugery z krokowe klasy klienta WCF.  
  
### <a name="finding-data-types"></a>Znajdowanie typy danych  
 Aby zlokalizować typów danych w wygenerowanym kodzie, mechanizmu najbardziej podstawowa jest wyszukiwania kodu dla tej deklaracji typu i określ nazwę typu określonymi w umowie. Na przykład następujące kontrakt Określa, że `SampleMethod` może zwrócić błędu protokołu SOAP, którego typ `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Wyszukiwanie `SampleFault` lokalizuje następujące deklaracji typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 W takim przypadku typ danych jest typ szczegółów zgłaszanych przez określony wyjątek na kliencie, <xref:System.ServiceModel.FaultException%601> gdzie parametr typu szczegółów jest `microsoft.wcf.documentation.SampleFault`. Aby uzyskać więcej informacji na temat typów danych, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w klientach, zobacz [wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Znajdowanie kontraktach wywołania zwrotnego dla usługi dwukierunkowe  
 Jeśli zlokalizować kontraktu usługi, dla którego interfejsu kontraktu określa wartość <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> określa kontrakt dupleksowy, właściwości, a następnie tej Umowy. Kontrakty dwukierunkowe wymaga aplikacji klienckiej, aby utworzyć klasę wywołania zwrotnego, która implementuje kontrakt wywołania zwrotnego i przekaż wystąpienie tej klasy do <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> lub <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> używany do komunikacji z usługą. Aby uzyskać więcej informacji o klientach dupleksowy, zobacz [porady: dostęp do usług z kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Następujące kontrakt określa kontrakt wywołania zwrotnego typu `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Wyszukiwanie dla tego kontraktu wywołania zwrotnego lokalizuje który aplikacja kliencka musi implementować interfejsu.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Kanał kontraktu usługi Znajdowanie interfejsów  
 Korzystając z <xref:System.ServiceModel.ChannelFactory> klasy przy użyciu interfejsu kontraktu usługi, należy rzutować do <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejsu jawnie otworzyć, zamknij lub przerwania kanału. Aby ułatwić pracy z narzędzia Svcutil.exe generuje również interfejs pomocnika, który implementuje zarówno interfejs kontrakt usługi i <xref:System.ServiceModel.IClientChannel> umożliwiają interakcję z infrastrukturą kanału klienta bez konieczności rzutowania. Poniższy kod przedstawia definicję pomocnika kanału klienta, który implementuje poprzedniego kontraktu usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
