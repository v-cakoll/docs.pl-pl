---
title: Rozszerzanie systemu metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: d3ce7e1a228e6303be1009c7b72f4e889b40c536
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795722"
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="2c093-102">Rozszerzanie systemu metadanych</span><span class="sxs-lookup"><span data-stu-id="2c093-102">Extending the Metadata System</span></span>
<span data-ttu-id="2c093-103">System metadanych programu Windows Communication Foundation (WCF) to grupa klas i interfejsów, które reprezentują metadane wymagane do implementowania aplikacji opartych na usługach.</span><span class="sxs-lookup"><span data-stu-id="2c093-103">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="2c093-104">Modyfikuj lub rozszerzaj klasy albo Implementuj i Konfiguruj interfejsy do eksportowania i importowania niestandardowych metadanych, takich jak rozszerzenia Web Services Description Language (WSDL) lub niestandardowe potwierdzenia WS-PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="2c093-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c093-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2c093-105">In This Section</span></span>  
 [<span data-ttu-id="2c093-106">Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF</span><span class="sxs-lookup"><span data-stu-id="2c093-106">Exporting Custom Metadata for a WCF Extension</span></span>](exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="2c093-107">Opisuje sposób wdrażania i używania <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu do osadzania niestandardowych potwierdzeń zasad w dokumentach WSDL.</span><span class="sxs-lookup"><span data-stu-id="2c093-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="2c093-108">Importowanie niestandardowych metadanych dla rozszerzenia WCF</span><span class="sxs-lookup"><span data-stu-id="2c093-108">Importing Custom Metadata for a WCF Extension</span></span>](importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="2c093-109">Opisuje sposób wdrażania i używania <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu w celu odczytu i reagowania na niestandardowe potwierdzenia zasad w dokumentach WSDL.</span><span class="sxs-lookup"><span data-stu-id="2c093-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="2c093-110">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="2c093-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="2c093-111">Opisuje sposób wymiany metadanych za pośrednictwem powiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2c093-111">Describes how to exchange metadata over custom bindings.</span></span>
