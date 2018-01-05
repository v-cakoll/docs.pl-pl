---
title: Rozszerzanie systemu metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aca7a7aba7ef4a40100e9858561d197916b71544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-metadata-system"></a>Rozszerzanie systemu metadanych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] System metadanych to grupa klasy i interfejsy, które reprezentują metadane wymagane do wdrożenia aplikacji usługi. Modyfikowanie lub rozszerzyć klasy lub wdrożenia i skonfigurować interfejsów, aby wyeksportować i zaimportować niestandardowy metadane, takie jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs do osadzenia w dokumentach WSDL niestandardowych asercji zasad.  
  
 [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs do odczytu i odpowiadania na niestandardowych asercji zasad w dokumentach WSDL.  
  
 [Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Opisuje sposób wymiany metadanych za pośrednictwem powiązania niestandardowego.
