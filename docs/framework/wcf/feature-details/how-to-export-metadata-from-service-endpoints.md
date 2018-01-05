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
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="b5093-102">Instrukcje: Eksportowanie metadanych z punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="b5093-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="b5093-103">W tym temacie opisano sposób eksportowania metadanych z punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="b5093-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="b5093-104">Aby wyeksportować metadane z punktów końcowych usług</span><span class="sxs-lookup"><span data-stu-id="b5093-104">To export metadata from service endpoints</span></span>  
  
1.  <span data-ttu-id="b5093-105">Tworzenie nowego projektu programu Visual Studio konsoli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5093-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="b5093-106">Dodaj kod pokazano w poniższych krokach w wygenerowanym pliku Program.cs w metodzie main().</span><span class="sxs-lookup"><span data-stu-id="b5093-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2.  <span data-ttu-id="b5093-107">Utwórz <xref:System.ServiceModel.Description.WsdlExporter>.</span><span class="sxs-lookup"><span data-stu-id="b5093-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  <span data-ttu-id="b5093-108">Ustaw <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> jedną z wartości z właściwości <xref:System.ServiceModel.Description.PolicyVersion> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b5093-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="b5093-109">W tym przykładzie ustawiono wartość <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> odnosi się do wersji 1.5 usługi WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="b5093-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  <span data-ttu-id="b5093-110">Utwórz tablicę <xref:System.ServiceModel.Description.ServiceEndpoint> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b5093-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  <span data-ttu-id="b5093-111">Eksportowanie metadanych dla każdego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="b5093-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  <span data-ttu-id="b5093-112">Sprawdź, upewnij się, że nie wystąpiły żadne błędy podczas procesu eksportowania i pobieranie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b5093-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  <span data-ttu-id="b5093-113">Teraz możesz używać metadane, takie jak zapisze go w pliku przez wywołanie metody <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> metody.</span><span class="sxs-lookup"><span data-stu-id="b5093-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5093-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5093-114">Example</span></span>  
 <span data-ttu-id="b5093-115">Poniżej znajduje się pełna listy w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b5093-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5093-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b5093-116">Compiling the Code</span></span>  
 <span data-ttu-id="b5093-117">W przypadku kompilowania kodu System.ServiceModel.dll odwołanie do pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="b5093-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5093-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5093-118">See Also</span></span>  
 [<span data-ttu-id="b5093-119">Przegląd architektury metadanych</span><span class="sxs-lookup"><span data-stu-id="b5093-119">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="b5093-120">Używanie metadanych</span><span class="sxs-lookup"><span data-stu-id="b5093-120">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="b5093-121">Punkty końcowe: adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="b5093-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
