---
title: 'Instrukcje: importowanie metadanych do punktów końcowych usług'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: dce65c31134c211c134cbae2b9bd8296f74b1627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930727"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Instrukcje: importowanie metadanych do punktów końcowych usług
W tym temacie opisano sposób importowania metadanych do kolekcji punktów końcowych usługi i używania usługi zdefiniowanej w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym temacie pokazano, jak utworzyć aplikację kliencką, która importuje metadane z usługi, a `Add` następnie wywołuje metodę w usłudze.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Aby zaimportować metadane do punktów końcowych usługi  
  
1. Zadeklaruj <xref:System.ServiceModel.EndpointAddress> obiekt i zainicjuj go za pomocą Uniform Resource Identifier (URI) dla adresu wymiany metadanych (Mex) usługi.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Utwórz, przekazując w adresie MEX i Wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. <xref:System.ServiceModel.Description.MetadataExchangeClient> Spowoduje to pobranie metadanych z usługi.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Utwórz, przekazując do metadanych wcześniej pobrane i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. <xref:System.ServiceModel.Description.WsdlImporter> Spowoduje to wygenerowanie kolekcji <xref:System.ServiceModel.Description.ContractDescription> obiektów. Możesz również wywołać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> lub <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, w zależności od potrzeb.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Po zaimportowaniu metadanych nie będzie można utworzyć kanału klienta lub wyeksportować metadanych. Dzieje się tak, ponieważ w tym punkcie nie są dostępne żadne informacje o typie. Informacje o typie są wymagane do rzeczywistego współdziałania z usługą lub do eksportowania metadanych. Aby wygenerować informacje o typie, należy wygenerować kod, przedstawiony w krokach 4 i 5. Alternatywnie można użyć <xref:System.ServiceModel.Description.MetadataResolver> klasy pomocnika. Aby uzyskać więcej informacji, zobacz [jak: Użyj klasy MetadataResolver, aby dynamicznie](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)uzyskać metadane powiązania.  
  
4. Generuj informacje o typie dla każdego kontraktu.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Teraz możesz użyć tych informacji. Poniższy przykład generuje C# kod źródłowy.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
