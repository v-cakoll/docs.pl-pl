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
ms.locfileid: "33488959"
---
# <a name="extending-the-metadata-system"></a>Rozszerzanie systemu metadanych
Metadane systemu Windows Communication Foundation (WCF) to grupa klasy i interfejsy, które reprezentują metadane wymagane do wdrożenia aplikacji usługi. Modyfikowanie lub rozszerzyć klasy lub wdrożenia i skonfigurować interfejsów, aby wyeksportować i zaimportować niestandardowy metadane, takie jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Eksportowanie niestandardowych metadanych na potrzeby rozszerzenia programu WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interfejs do osadzenia w dokumentach WSDL niestandardowych asercji zasad.  
  
 [Importowanie niestandardowych metadanych dla rozszerzenia WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 Opisuje sposób zaimplementowania i użycia <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs do odczytu i odpowiadania na niestandardowych asercji zasad w dokumentach WSDL.  
  
 [Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Opisuje sposób wymiany metadanych za pośrednictwem powiązania niestandardowego.
