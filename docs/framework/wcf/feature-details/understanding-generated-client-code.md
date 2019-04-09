---
title: Opis wygenerowanego kodu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 226b77d1c638ec4f8505140332ad35d4029ef0b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189162"
---
# <a name="understanding-generated-client-code"></a>Opis wygenerowanego kodu klienta
[Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje kod klienta i pliku konfiguracji aplikacji klienta do użycia podczas tworzenia aplikacji klienckich. Ten temat zawiera przewodnik po przykładach wygenerowanego kodu dla scenariuszy umowy usług w warstwie standardowa. Aby uzyskać więcej informacji dotyczących tworzenia aplikacji klienckiej, za pomocą wygenerowanego kodu, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Omówienie  
 Jeśli używasz programu Visual Studio do generowania typów klientów usługi Windows Communication Foundation (WCF) w projekcie, zwykle nie trzeba badanie kodu wygenerowanego klienta. Jeśli nie używasz środowiska programowania, który wykonuje te same usługi dla Ciebie, można użyć narzędzia, takiego jak Svcutil.exe do generowania kodu klienta, a następnie użyj tego kodu do tworzenia aplikacji klienckiej.  
  
 Ponieważ Svcutil.exe ma kilka opcji, które modyfikują informacje o typie wygenerowanym, w tym temacie nie omówiono wszystkich scenariuszy. Jednak następujące zadania standard obejmują lokalizowanie wygenerowanego kodu:  
  
-   Identyfikowanie interfejsy kontraktu usługi.  
  
-   Identyfikowanie Klasa klienta programu WCF.  
  
-   Identyfikowanie typów danych.  
  
-   Identyfikowanie kontrakty wywołania zwrotnego dla usługi dwukierunkowe.  
  
-   Identyfikowanie interfejsu kanału kontraktu usługi pomocnika.  
  
### <a name="finding-service-contract-interfaces"></a>Interfejsy kontraktu usługi wyszukiwania  
 Aby zlokalizować interfejsów, które modelują kontraktów usług, wyszukaj interfejsów, które są oznaczone <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atrybutu. Często ten atrybut może być trudne do zlokalizowania z szybkiego odczytu z powodu obecności innych atrybutów i jawne właściwości ustawione dla samego atrybutu. Należy pamiętać, że interfejs kontrakt usługi i interfejsu umowy klienta są dwa różne typy. Poniższy przykład kodu pokazuje kontrakt usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Poniższy przykład kodu pokazuje ten sam kontrakt usługi, tak jak w przypadku Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Można użyć interfejsu kontraktu usługi wygenerowane wraz z <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> klasy, aby utworzyć obiekt kanału WCF, za pomocą którego do wywołania operacji usługi. Aby uzyskać więcej informacji, zobacz [jak: Używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Znajdowanie klasy klienta WCF  
 Aby zlokalizować klasy klienta WCF, która implementuje ten kontrakt usługi, którego chcesz użyć, wyszukaj rozszerzenie <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, gdzie parametr typu interfejsu, wcześniej kontraktu usługi znajduje się i rozszerzający tego interfejsu. Poniższy kod przedstawia przykład <xref:System.ServiceModel.ClientBase%601> klasy typu `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Można użyć tej klasy klienta WCF, tworząc nowe wystąpienie i wywołania metody, które implementuje. Te metody wywołania operacji usługi za pomocą którego został zaprojektowany i skonfigurowany tak, aby wchodzić w interakcje. Aby uzyskać więcej informacji, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Gdy SvcUtil.exe wygeneruje klasy klienta WCF, dodaje <xref:System.Diagnostics.DebuggerStepThroughAttribute> do klasy klienta, który uniemożliwia debugery wchodzi za pośrednictwem klasy klienta programu WCF.  
  
### <a name="finding-data-types"></a>Znajdowanie typów danych  
 Aby zlokalizować typy danych w wygenerowanym kodzie, najbardziej podstawowy mechanizm jest wyszukiwania kodu dla tej deklaracji typu i zidentyfikować nazwę typu z określonymi w umowie. Na przykład, następujące kontrakt Określa, że `SampleMethod` może zwrócić błąd protokołu SOAP, typu `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Trwa wyszukiwanie `SampleFault` lokalizuje następującą deklarację typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 W takim przypadku typem danych jest typ szczegółów wygenerowanych przez określony wyjątek na kliencie, <xref:System.ServiceModel.FaultException%601> gdzie parametr typu szczegółów jest `microsoft.wcf.documentation.SampleFault`. Aby uzyskać więcej informacji na temat typów danych, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w klientach, zobacz [wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Wyszukiwanie kontrakty wywołania zwrotnego dla usługi dwukierunkowe  
 Jeśli zlokalizować kontraktu usługi, dla którego interfejsu kontraktu określa wartość dla <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> określa kontrakt dupleksowy, właściwości, a następnie tej Umowy. Kontrakty dwukierunkowe wymaga aplikacja kliencka, aby utworzyć klasę wywołania zwrotnego, która implementuje ten kontrakt wywołania zwrotnego i przekaż wystąpienie tej klasy, aby <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> lub <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> używany do komunikacji z usługą. Aby uzyskać więcej informacji o klientach dupleksowy, zobacz [jak: Uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Następujące kontrakt określa kontrakt wywołania zwrotnego typu `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Wyszukaj ten kontrakt wywołania zwrotnego lokalizuje następujący interfejs, który muszą implementować aplikacji klienckiej.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Interfejsy kanał kontraktu usługi wyszukiwania  
 Korzystając z <xref:System.ServiceModel.ChannelFactory> klasy przy użyciu interfejsu kontraktu usługi, należy rzutować do <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejsu jawnie otwierać, zamknij lub Przerwij kanału. W celu ułatwienia pracy z narzędzia Svcutil.exe generuje również interfejs pomocnika, który implementuje zarówno interfejs kontrakt usługi i <xref:System.ServiceModel.IClientChannel> umożliwiające interakcję z infrastrukturą kanału klienta bez rzutowania. Poniższy kod przedstawia definicję kanału klienta pomocnika, który implementuje poprzedniego kontraktu usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
