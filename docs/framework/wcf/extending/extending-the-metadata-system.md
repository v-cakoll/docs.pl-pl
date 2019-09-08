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
# <a name="extending-the-metadata-system"></a>Rozszerzanie systemu metadanych
System metadanych programu Windows Communication Foundation (WCF) to grupa klas i interfejsów, które reprezentują metadane wymagane do implementowania aplikacji opartych na usługach. Modyfikuj lub rozszerzaj klasy albo Implementuj i Konfiguruj interfejsy do eksportowania i importowania niestandardowych metadanych, takich jak rozszerzenia Web Services Description Language (WSDL) lub niestandardowe potwierdzenia WS-PolicyAttachments.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF](exporting-custom-metadata-for-a-wcf-extension.md)  
 Opisuje sposób wdrażania i używania <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejsu do osadzania niestandardowych potwierdzeń zasad w dokumentach WSDL.  
  
 [Importowanie niestandardowych metadanych dla rozszerzenia WCF](importing-custom-metadata-for-a-wcf-extension.md)  
 Opisuje sposób wdrażania i używania <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu w celu odczytu i reagowania na niestandardowe potwierdzenia zasad w dokumentach WSDL.  
  
 [Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Opisuje sposób wymiany metadanych za pośrednictwem powiązań niestandardowych.
