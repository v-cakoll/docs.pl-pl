---
title: 'Instrukcje: eksportowanie metadanych z punktów końcowych usług'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: bd6543e1e22b7a2cb0b870fe2fdb34011f0d2a4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162792"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Instrukcje: eksportowanie metadanych z punktów końcowych usług
W tym temacie opisano sposób eksportowania metadanych z punktów końcowych usługi.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Eksportowanie metadanych z punktów końcowych usług  
  
1.  Tworzenie nowego projektu programu Visual Studio konsoli aplikacji. Dodaj kod przedstawiony w poniższych krokach w wygenerowanym pliku Program.cs wewnątrz metody main().  
  
2.  Utwórz <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Ustaw <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> właściwość na jedną z wartości z <xref:System.ServiceModel.Description.PolicyVersion> wyliczenia. W tym przykładzie ustawia wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> odnosi się do wersji 1.5 usługi WS-Policy.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  Utwórz tablicę <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  Eksportowanie metadanych dla każdego punktu końcowego usługi.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  Sprawdź, upewnij się, że nie wystąpiły żadne błędy podczas procesu eksportowania do pobierania metadanych.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  Teraz możesz używać metadane, takie jak zapisać do pliku, wywołując <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metody.  
  
## <a name="example"></a>Przykład  
 Oto pełny kod dla tego przykładu.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Podczas kompilowania System.ServiceModel.dll odwołanie do pliku Program.cs.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Punkty końcowe: adresy, wiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
