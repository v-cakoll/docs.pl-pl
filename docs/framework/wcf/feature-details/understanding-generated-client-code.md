---
title: Opis wygenerowanego kodu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 6bc921355e54023ead3a308a7877ab609f868221
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968628"
---
# <a name="understanding-generated-client-code"></a>Opis wygenerowanego kodu klienta
[Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje kod klienta i plik konfiguracyjny aplikacji klienckiej do użycia podczas tworzenia aplikacji klienckich. Ten temat zawiera Przewodnik po wygenerowanych przykładach kodu dla standardowych scenariuszy kontraktu usługi. Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej przy użyciu wygenerowanego kodu, zobacz [Omówienie klienta WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Omówienie  
 Jeśli używasz programu Visual Studio do generowania typów klienta Windows Communication Foundation (WCF) dla projektu, zazwyczaj nie musisz analizować wygenerowanego kodu klienta. Jeśli nie używasz środowiska programistycznego, które wykonuje te same usługi, możesz użyć narzędzia, takiego jak Svcutil. exe, aby wygenerować kod klienta, a następnie użyć tego kodu do opracowania aplikacji klienckiej.  
  
 Ponieważ Svcutil. exe zawiera wiele opcji, które modyfikują wygenerowane informacje o typie, w tym temacie nie są omawiane wszystkie scenariusze. Jednak następujące zadania standardowe obejmują lokalizowanie wygenerowanego kodu:  
  
- Identyfikowanie interfejsów kontraktu usługi.  
  
- Identyfikowanie klasy klienta WCF.  
  
- Identyfikowanie typów danych.  
  
- Identyfikowanie kontraktów wywołania zwrotnego dla usług dupleksowych.  
  
- Identyfikowanie interfejsu kanału kontraktu usługi pomocnika.  
  
### <a name="finding-service-contract-interfaces"></a>Znajdowanie interfejsów kontraktu usługi  
 Aby zlokalizować interfejsy, które modelują kontrakt usługi, Wyszukaj interfejsy, które są oznaczone <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atrybutem. Często ten atrybut może być trudny do zlokalizowania z szybkim odczytem ze względu na obecność innych atrybutów i jawnych właściwości ustawionych dla samego atrybutu. Należy pamiętać, że interfejs kontraktu usługi i interfejs kontraktu klienta są dwa różne typy. Poniższy przykład kodu pokazuje oryginalny kontrakt usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Poniższy przykład kodu przedstawia ten sam kontrakt usługi, jak wygenerowany przez Svcutil. exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Możesz użyć wygenerowanego interfejsu kontraktu usługi wraz z klasą, <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> aby utworzyć obiekt kanału WCF, za pomocą którego chcesz wywołać operacje usługi. Aby uzyskać więcej informacji, zobacz [jak: Użyj elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Znajdowanie klas klienta WCF  
 Aby znaleźć klasę klienta WCF implementującą kontrakt usługi, którego chcesz użyć, Wyszukaj rozszerzenie <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, gdzie parametr typu jest interfejsem kontraktu usługi, który został wcześniej zlokalizowany i który rozszerza ten interfejs. Poniższy przykład kodu pokazuje <xref:System.ServiceModel.ClientBase%601> klasę typu. `ISampleService`  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Możesz użyć tej klasy klienta WCF, tworząc nowe wystąpienie i wywołując metody, które implementuje. Metody te wywołują operację usługi, z którą jest zaprojektowana i skonfigurowana do współpracy. Aby uzyskać więcej informacji, zobacz [Omówienie klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
> Gdy Svcutil. exe generuje klasę klienta WCF, dodaje <xref:System.Diagnostics.DebuggerStepThroughAttribute> do klasy klienta, która uniemożliwia debugerom krokowe przechodzenie przez klasę klienta WCF.  
  
### <a name="finding-data-types"></a>Znajdowanie typów danych  
 Aby zlokalizować typy danych w wygenerowanym kodzie, najważniejszym mechanizmem jest zidentyfikowanie nazwy typu określonego w kontrakcie i przeszukanie kodu dla tej deklaracji typu. Na przykład następujący kontrakt Określa, że `SampleMethod` może zwracać błąd protokołu SOAP typu. `microsoft.wcf.documentation.SampleFault`  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 `SampleFault` Wyszukiwanie lokalizuje następującą deklarację typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 W takim przypadku typ danych jest typem szczegółowym generowanym przez konkretny wyjątek na kliencie, <xref:System.ServiceModel.FaultException%601> gdzie `microsoft.wcf.documentation.SampleFault`parametr typu szczegółu. Aby uzyskać więcej informacji na temat typów danych, zobacz [określanie transfer danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w klientach, zobacz [wysyłanie i otrzymywanie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Znajdowanie umów wywołania zwrotnego dla usług dupleksu  
 W przypadku znalezienia kontraktu usługi, dla którego interfejs kontraktu określa wartość <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości, ten kontrakt określa kontrakt dupleksowy. Umowy dupleksowe wymagają od aplikacji klienckiej utworzenia klasy wywołania zwrotnego implementującej kontrakt wywołania zwrotnego i przekazania wystąpienia tej klasy do <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> lub <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> używanego do komunikacji z usługą. Aby uzyskać więcej informacji o klientach dupleksowych, zobacz [How to: Uzyskaj dostęp do usług za pomocą](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)kontraktu dupleksowego.  
  
 Następujący kontrakt określa kontrakt wywołania zwrotnego typu `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Wyszukiwanie tego kontraktu wywołania zwrotnego lokalizuje następujący interfejs, który musi zostać zaimplementowany przez aplikację kliencką.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Znajdowanie interfejsów kanału kontraktu usługi  
 W przypadku używania <xref:System.ServiceModel.ChannelFactory> klasy z interfejsem kontraktu usługi należy rzutować <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> do interfejsu w celu jawnego otwierania, zamykania lub przerywania kanału. Aby ułatwić pracę z programem, narzędzie Svcutil. exe generuje również interfejs pomocnika, który implementuje interfejs kontraktu usługi i <xref:System.ServiceModel.IClientChannel> umożliwia korzystanie z infrastruktury kanału klienta bez konieczności rzutowania. Poniższy kod przedstawia definicję kanału pomocnika klienta, który implementuje poprzedni kontrakt usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
