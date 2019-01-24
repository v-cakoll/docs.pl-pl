---
title: 'Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: ad09f49b933edfc4df107a02e124eaaa5ddd3d73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608537"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu
Jest to jedna z dwóch tematy porad, które mówią o Publikowanie metadanych dla usługi Windows Communication Foundation (WCF). Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i przy użyciu kodu. W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu kodu.  
  
> [!CAUTION]
>  W tym temacie przedstawiono sposób Publikowanie metadanych w niezabezpieczony sposób. Dowolny klient może pobierać metadanych z usługi. Jeśli potrzebujesz usługi w celu publikowania metadanych w bezpieczny sposób. zobacz [niestandardowy bezpieczny punkt końcowy metadanych](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Aby uzyskać więcej informacji na temat publikowania metadanych w pliku konfiguracji, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Publikowanie metadanych zezwala klientom na pobieranie metadanych za pomocą ROZPOCZYNANIE transferu WS żądania lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania. Należy upewnić się, że działa kod, możesz utworzyć podstawowe usługi WCF. Podstawowa usługa Self-Hosted znajduje się w poniższym kodzie.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Publikowanie metadanych w kodzie  
  
1.  W metodzie głównej aplikacji konsoli, należy utworzyć wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu, przekazując typ usługi i adres podstawowy.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  Tworzenie bloku try bezpośrednio poniżej kodu w kroku 1, to przechwytuje wszystkie wyjątki, które Pobierz zgłaszany, gdy usługa jest uruchomiona.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Sprawdź, czy host usługi zawiera już <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, jeśli nie, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Zawiera <xref:System.ServiceModel.Description.MetadataExporter> właściwości. <xref:System.ServiceModel.Description.MetadataExporter> Zawiera <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości. Ustaw wartość <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Właściwość można ustawić <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Po ustawieniu <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> eksportu metadanych generuje informacje o zasadach z metadanymi, "jest zgodny do wersji 1.5 usługi WS-Policy. Po ustawieniu <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> eksportu metadanych generuje informacje o zasadach, który jest zgodny z 1.2 WS-Policy.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie kolekcji zachowań hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Dodaj punkt końcowy wymiany metadanych do hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Dodawanie punktu końcowego aplikacji do hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Jeśli nie dodasz żadnych punktów końcowych do usługi, środowiska uruchomieniowego dodaje domyślne punkty końcowe. W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> równa `true`, usługa ma Publikowanie metadanych włączone. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Otworzyć hosta usługi i zaczekaj na połączenia przychodzące. Gdy użytkownik naciśnie klawisz ENTER, zamknij hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Skompiluj i uruchom aplikację konsolową.  
  
11. Aby przejść do podstawowego adresu usługi w programie Internet Explorer (http://localhost:8001/MetadataSample w tym przykładzie) i sprawdź, czy Publikowanie metadanych jest włączona. Powinien zostać wyświetlony strona sieci Web wyświetlany jest wyświetlany komunikat "Prostą usługę" u góry, a od razu poniżej "Utworzono usługę." W przeciwnym razie komunikat wyświetlany w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje implementację podstawowej usługi WCF, która umożliwia publikowanie metadanych dla usługi w kodzie.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Host samodzielny](../../../../docs/framework/wcf/samples/self-host.md)
- [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
