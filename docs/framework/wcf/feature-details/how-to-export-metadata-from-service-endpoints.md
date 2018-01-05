---
title: "Instrukcje: Eksportowanie metadanych z punktów końcowych usług"
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
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b045ef55ac0b6d76bb06e711b4134d54b3d61f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Instrukcje: Eksportowanie metadanych z punktów końcowych usług
W tym temacie opisano sposób eksportowania metadanych z punktów końcowych usługi.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Aby wyeksportować metadane z punktów końcowych usług  
  
1.  Tworzenie nowego projektu programu Visual Studio konsoli aplikacji. Dodaj kod pokazano w poniższych krokach w wygenerowanym pliku Program.cs w metodzie main().  
  
2.  Utwórz <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Ustaw <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> jedną z wartości z właściwości <xref:System.ServiceModel.Description.PolicyVersion> wyliczenia. W tym przykładzie ustawiono wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> odnosi się do wersji 1.5 usługi WS-Policy.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  Utwórz tablicę <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  Eksportowanie metadanych dla każdego punktu końcowego usługi.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  Sprawdź, upewnij się, że nie wystąpiły żadne błędy podczas procesu eksportowania i pobieranie metadanych.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  Teraz możesz używać metadane, takie jak zapisze go w pliku przez wywołanie metody <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metody.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna listy w tym przykładzie kodu.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W przypadku kompilowania kodu System.ServiceModel.dll odwołanie do pliku Program.cs.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
