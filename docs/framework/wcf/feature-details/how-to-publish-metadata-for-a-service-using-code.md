---
title: 'Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: db6bca8728789879f9bfea40904bfc80352d1dbe
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144919"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu
Jest to jeden z dwóch tematów, które omawiają Publikowanie metadanych dla usługi Windows Communication Foundation (WCF). Istnieją dwa sposoby, aby określić, w jaki sposób usługa powinna publikować metadane przy użyciu pliku konfiguracji i przy użyciu kodu. W tym temacie przedstawiono sposób publikowania metadanych dla usługi przy użyciu kodu.  
  
> [!CAUTION]
> W tym temacie przedstawiono sposób publikowania metadanych w niezabezpieczony sposób. Dowolny klient może pobrać metadane z usługi. Jeśli wymagasz, aby usługa opublikowała metadane w bezpieczny sposób. Zobacz [Niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Aby uzyskać więcej informacji na temat publikowania metadanych w pliku konfiguracji, zobacz [How to: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Publikowanie metadanych umożliwia klientom Pobieranie metadanych przy użyciu żądania GET WS-transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania. Aby upewnić się, że kod działa, należy utworzyć podstawową usługę WCF. W poniższym kodzie znajduje się podstawowa usługa samodzielna.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Aby opublikować metadane w kodzie  
  
1. W ramach głównej metody aplikacji konsolowej Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu przez przekazanie go do typu usługi i adresu podstawowego.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. Utwórz blok try bezpośrednio poniżej kodu dla kroku 1, który przechwytuje wszystkie wyjątki, które są zgłaszane podczas działania usługi.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Sprawdź, czy host usługi zawiera już <xref:System.ServiceModel.Description.ServiceMetadataBehavior> , jeśli nie, Utwórz nowe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Właściwość na`true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Zawiera <xref:System.ServiceModel.Description.MetadataExporter> Właściwość. <xref:System.ServiceModel.Description.MetadataExporter>Zawiera <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Właściwość. Ustaw wartość <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> . <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Właściwość można również ustawić na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> . Po ustawieniu na wartość w <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> polu Eksport metadanych są generowane informacje o zasadach z metadanymi, które są zgodne z usługą ws-policy 1,5. Gdy jest ustawiony na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> Eksport metadanych, są generowane informacje o zasadach, które są zgodne z usługą ws-policy 1,2.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie do kolekcji zachowań hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Dodaj punkt końcowy wymiany metadanych do hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Dodaj punkt końcowy aplikacji do hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > Jeśli nie dodasz żadnych punktów końcowych do usługi, środowisko uruchomieniowe doda domyślne punkty końcowe. W tym przykładzie, ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawiony na `true` , usługa ma włączone metadane publikowania. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Otwórz hosta usługi i poczekaj na wywołania przychodzące. Gdy użytkownik naciśnie klawisz ENTER, Zamknij hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Skompiluj i uruchom aplikację konsolową.  
  
11. Użyj programu Internet Explorer, aby przejść do adresu podstawowego usługi ( `http://localhost:8001/MetadataSample` w tym przykładzie) i sprawdzić, czy Publikowanie metadanych jest włączone. Powinna zostać wyświetlona strona sieci Web informująca o "prostej usłudze" u góry i bezpośrednio poniżej "została utworzona usługa". Jeśli nie, zostanie wyświetlony komunikat w górnej części strony wyników: "Publikowanie metadanych dla tej usługi jest obecnie wyłączone".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia implementację podstawowej usługi WCF, która publikuje metadane dla usługi w kodzie.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Host samodzielny](../../../../docs/framework/wcf/samples/self-host.md)
- [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
