---
title: Rozszerzanie systemu metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7ccef0c2b908a8f78249742decd6c46a862e541e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="5ead8-102">Rozszerzanie systemu metadanych</span><span class="sxs-lookup"><span data-stu-id="5ead8-102">Extending the Metadata System</span></span>
<span data-ttu-id="5ead8-103">Metadane systemu Windows Communication Foundation (WCF) to grupa klasy i interfejsy, które reprezentują metadane wymagane do wdrożenia aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5ead8-103">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="5ead8-104">Modyfikowanie lub rozszerzyć klasy lub wdrożenia i skonfigurować interfejsów, aby wyeksportować i zaimportować niestandardowy metadane, takie jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="5ead8-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ead8-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5ead8-105">In This Section</span></span>  
 [<span data-ttu-id="5ead8-106">Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF</span><span class="sxs-lookup"><span data-stu-id="5ead8-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="5ead8-107">Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs do osadzenia w dokumentach WSDL niestandardowych asercji zasad.</span><span class="sxs-lookup"><span data-stu-id="5ead8-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="5ead8-108">Importowanie niestandardowych metadanych dla rozszerzenia WCF</span><span class="sxs-lookup"><span data-stu-id="5ead8-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="5ead8-109">Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs do odczytu i odpowiadania na niestandardowych asercji zasad w dokumentach WSDL.</span><span class="sxs-lookup"><span data-stu-id="5ead8-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="5ead8-110">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="5ead8-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="5ead8-111">Opisuje sposób wymiany metadanych za pośrednictwem powiązania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="5ead8-111">Describes how to exchange metadata over custom bindings.</span></span>
