---
title: 'Instrukcje: Importowanie metadanych do punktów końcowych usług'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597062"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Instrukcje: Importowanie metadanych do punktów końcowych usług
W tym temacie opisano sposób importowania metadanych do kolekcji punktów końcowych usługi i używania usługi zdefiniowanej w [wprowadzenie](../samples/getting-started-sample.md). W tym temacie pokazano, jak utworzyć aplikację kliencką, która importuje metadane z usługi, a następnie wywołuje `Add` metodę w usłudze.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Aby zaimportować metadane do punktów końcowych usługi  
  
1. Zadeklaruj <xref:System.ServiceModel.EndpointAddress> obiekt i zainicjuj go za pomocą Uniform Resource Identifier (URI) dla adresu wymiany metadanych (Mex) usługi.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. Utwórz <xref:System.ServiceModel.Description.MetadataExchangeClient> , przekazując w adresie MEX i Wywołaj <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> . Spowoduje to pobranie metadanych z usługi.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. Utwórz <xref:System.ServiceModel.Description.WsdlImporter> , przekazując do metadanych wcześniej pobrane i Wywołaj <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> . Spowoduje to wygenerowanie kolekcji <xref:System.ServiceModel.Description.ContractDescription> obiektów. Możesz również wywołać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> lub <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> , w zależności od potrzeb.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > Po zaimportowaniu metadanych nie będzie można utworzyć kanału klienta lub wyeksportować metadanych. Dzieje się tak, ponieważ w tym punkcie nie są dostępne żadne informacje o typie. Informacje o typie są wymagane do rzeczywistego współdziałania z usługą lub do eksportowania metadanych. Aby wygenerować informacje o typie, należy wygenerować kod, przedstawiony w krokach 4 i 5. Alternatywnie można użyć <xref:System.ServiceModel.Description.MetadataResolver> klasy pomocnika. Aby uzyskać więcej informacji, zobacz [How to: use klasy MetadataResolver do dynamicznego uzyskiwania metadanych powiązania](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4. Generuj informacje o typie dla każdego kontraktu.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. Teraz możesz użyć tych informacji. Poniższy przykład generuje kod źródłowy języka C#.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Metadane](metadata.md)
- [Wprowadzenie](../samples/getting-started-sample.md)
