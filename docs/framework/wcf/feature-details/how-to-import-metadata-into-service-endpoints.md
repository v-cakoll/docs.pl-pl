---
title: 'Instrukcje: Importowanie metadanych do punktów końcowych usług'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 88b48b95a62c000d88b302589ebc489089e77602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-import-metadata-into-service-endpoints"></a>Instrukcje: Importowanie metadanych do punktów końcowych usług
W tym temacie wyjaśniono, jak zaimportować metadane do kolekcji punktów końcowych usługi i korzystać z usługi zdefiniowane w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym temacie przedstawiają sposób tworzenia aplikacji klienckiej, który importuje metadane z usługi, a następnie wywołania `Add` metody dla usługi.  
  
### <a name="to-import-metadata-into-service-endpoints"></a>Aby zaimportować metadane do punktów końcowych usług  
  
1.  Deklarowanie <xref:System.ServiceModel.EndpointAddress> i zainicjować go z identyfikatora URI (Uniform Resource) dla adresu programu exchange (MEX) metadanych usługi.  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  Utwórz <xref:System.ServiceModel.Description.MetadataExchangeClient>, przekazując adresu MEX. i wywołania <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>. To pobiera metadane z usługi.  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  Utwórz <xref:System.ServiceModel.Description.WsdlImporter>, przekazując metadanych wcześniej pobrane i wywołania <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>. Powoduje to kolekcja <xref:System.ServiceModel.Description.ContractDescription> obiektów. Można także wywołać <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> lub <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, zależnie od potrzeb.  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  Po zaimportowaniu metadanych, nie można utworzyć kanału klienta lub wyeksportować metadane. Jest to spowodowane typu informacje są niedostępne w tym momencie. Informacje o typie jest wymagany do faktycznie interakcji z usługą lub wyeksportować metadane. Aby wygenerować informacje o typie, należy wygenerować kod wyświetlany w kroku 4 i 5. Alternatywnie można użyć <xref:System.ServiceModel.Description.MetadataResolver> Klasa pomocy. Aby uzyskać więcej informacji, zobacz [porady: MetadataResolver używana do uzyskania powiązanie dynamicznie metadanych](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).  
  
4.  Generowanie informacji o typie dla każdej umowy.  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  Teraz można używać tych informacji. Poniższy przykład umożliwia wygenerowanie kodu źródłowego C#.  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
