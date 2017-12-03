---
title: "Wdrażanie projektu biblioteki WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbddd99125e8615640ca39d091e92cdde87c9faf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-a-wcf-library-project"></a>Wdrażanie projektu biblioteki WCF
W tym temacie opisano sposób wdrażania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] projektu biblioteki usługi.  
  
## <a name="deploying-a-wcf-service-library"></a>Wdrażanie biblioteki usługi WCF  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi jest biblioteki dołączanej (dynamicznie DLL). W efekcie nie można wykonać samodzielnie. Musi zostać wdrożony w środowisku macierzystym. Aby uzyskać więcej informacji o tym procesie, zobacz [hostingu i korzystanie z usługi WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Biblioteka usług można wdrożyć jak każdy inny [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Jednak należy pamiętać, że [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje konfiguracji dla bibliotek DLL. <xref:System.Configuration>obsługuje jeden plik konfiguracji na domenie aplikacji. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projektu biblioteki usługi eliminuje to ograniczenie przez zapewnienie podczas tworzenia pliku App.config dla biblioteki. Jednak po wdrożeniu nie jest rozpoznawana pliku App.config.  
  
 Masz Przenieś swój kod konfiguracji do pliku konfiguracyjnego rozpoznaje środowisku macierzystym. Dla hostingu samodzielnego, należy skopiować zawartość pliku App.config w pliku App.config hostingu pliku wykonywalnego. Jeśli używasz usług IIS do obsługi usługi, należy skopiować zawartość pliku App.config w pliku Web.config w katalogu wirtualnego.
