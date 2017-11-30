---
title: "Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu"
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
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c9ebfd6dd25bdeaa14df994c694dee699242ce8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Instrukcje: Publikowanie metadanych dla usługi przy użyciu kodu
Jest to jeden z dwóch tematy porad dotyczących Publikowanie metadanych dla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi. Istnieją dwa sposoby, aby określić, jak usługa powinna Publikowanie metadanych, przy użyciu pliku konfiguracji i kod. W tym temacie przedstawiono sposób Publikowanie metadanych dla usługi przy użyciu kodu.  
  
> [!CAUTION]
>  W tym temacie pokazano, jak publikować metadane w sposób niezabezpieczonych. Dowolny klient może pobrać metadanych usługi. Jeśli wymagana jest usługa Publikowanie metadanych w bezpieczny sposób. zobacz [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Publikowanie metadanych w pliku konfiguracji, zobacz [porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Publikowanie metadanych pozwala klientom na pobieranie metadanych za pomocą żądania GET usługi WS-Transfer lub żądania HTTP/GET przy użyciu `?wsdl` ciągu zapytania. Należy upewnić się, że kod działa można utworzyć podstawowej usługi WCF. Podstawowa usługa hostowania samoobsługowego jest dostarczana w poniższym kodzie.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Publikowanie metadanych w kodzie  
  
1.  W metodzie głównego aplikacji konsoli wystąpienia <xref:System.ServiceModel.ServiceHost> obiektu przez przekazywanie typu usługi i adres podstawowy.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  Tworzenie bloku try bezpośrednio pod kodu w kroku 1, to przechwytuje wszystkie wyjątki, które uzyskać zgłoszony, gdy usługa jest uruchomiona.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Sprawdź, czy host usługi zawiera już <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, jeśli nie, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości`true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Zawiera <xref:System.ServiceModel.Description.MetadataExporter> właściwości. <xref:System.ServiceModel.Description.MetadataExporter> Zawiera <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości. Ustaw wartość <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwości <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Można również ustawić właściwość <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Jeśli wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> eksportu metadanych generuje informacje o zasadach z metadanymi który "odpowiada 1.5 WS-Policy. Jeśli wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> eksportu metadanych generuje informacje o zasadach, które odpowiada 1.2 WS-Policy.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Dodaj <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie do kolekcji zachowań hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Dodaj punkt końcowy wymiany metadanych do hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Dodaj punkt końcowy aplikacji do usługi hosta.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Jeśli nie dodawaj żadnych punktów końcowych do usługi, środowisko uruchomieniowe dodaje domyślne punkty końcowe. W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawioną `true`, usługa ma Publikowanie metadanych włączone. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]domyślne punkty końcowe, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Otworzyć hosta usługi, a następnie zaczekaj na połączenia przychodzące. Gdy użytkownik naciśnie ENTER, zamknij hosta usługi.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Tworzenie i uruchamianie aplikacji konsoli.  
  
11. Przejdź do podstawowego adresu usługi (w tym przykładzie http://localhost:8001/MetadataSample) i sprawdź, czy Publikowanie metadanych jest włączona w programie Internet Explorer. Powinna zostać wyświetlona strona sieci Web wyświetlane, stwierdzający "Simple Service" u góry i natychmiast poniżej "Utworzono usługę." Jeśli nie, zostanie wyświetlony komunikat w górnej części strony wynikowy: "Publikowanie metadanych dla tej usługi jest obecnie wyłączona."  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia implementację podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która umożliwia publikowanie metadanych dla usługi w kodzie.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Host samodzielny](../../../../docs/framework/wcf/samples/self-host.md)  
 [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Przy użyciu metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
