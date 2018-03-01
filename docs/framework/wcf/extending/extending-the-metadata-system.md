---
title: Rozszerzanie systemu metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aca7a7aba7ef4a40100e9858561d197916b71544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="4652f-102">Rozszerzanie systemu metadanych</span><span class="sxs-lookup"><span data-stu-id="4652f-102">Extending the Metadata System</span></span>
<span data-ttu-id="4652f-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] System metadanych to grupa klasy i interfejsy, które reprezentują metadane wymagane do wdrożenia aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4652f-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="4652f-104">Modyfikowanie lub rozszerzyć klasy lub wdrożenia i skonfigurować interfejsów, aby wyeksportować i zaimportować niestandardowy metadane, takie jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="4652f-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4652f-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4652f-105">In This Section</span></span>  
 [<span data-ttu-id="4652f-106">Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF</span><span class="sxs-lookup"><span data-stu-id="4652f-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="4652f-107">Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs do osadzenia w dokumentach WSDL niestandardowych asercji zasad.</span><span class="sxs-lookup"><span data-stu-id="4652f-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="4652f-108">Importowanie niestandardowych metadanych dla rozszerzenia WCF</span><span class="sxs-lookup"><span data-stu-id="4652f-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="4652f-109">Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs do odczytu i odpowiadania na niestandardowych asercji zasad w dokumentach WSDL.</span><span class="sxs-lookup"><span data-stu-id="4652f-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="4652f-110">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="4652f-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="4652f-111">Opisuje sposób wymiany metadanych za pośrednictwem powiązania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="4652f-111">Describes how to exchange metadata over custom bindings.</span></span>
