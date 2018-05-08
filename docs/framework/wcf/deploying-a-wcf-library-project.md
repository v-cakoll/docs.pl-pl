---
title: Wdrażanie projektu biblioteki WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 08a1d794aeeea1a41cd1eb3abf298f3f4a0f6d15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-a-wcf-library-project"></a>Wdrażanie projektu biblioteki WCF
W tym temacie opisano, jak można wdrożyć projektu biblioteki usługi Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Wdrażanie biblioteki usługi WCF  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi jest biblioteki dołączanej (dynamicznie DLL). W efekcie nie można wykonać samodzielnie. Musi zostać wdrożony w środowisku macierzystym. Aby uzyskać więcej informacji o tym procesie, zobacz [hostingu i korzystanie z usługi WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Biblioteka usług można wdrożyć jak każdy inny [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Jednak należy pamiętać, że [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje konfiguracji dla bibliotek DLL. <xref:System.Configuration> obsługuje jeden plik konfiguracji na domenie aplikacji. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projektu biblioteki usługi eliminuje to ograniczenie przez zapewnienie podczas tworzenia pliku App.config dla biblioteki. Jednak po wdrożeniu nie jest rozpoznawana pliku App.config.  
  
 Masz Przenieś swój kod konfiguracji do pliku konfiguracyjnego rozpoznaje środowisku macierzystym. Dla hostingu samodzielnego, należy skopiować zawartość pliku App.config w pliku App.config hostingu pliku wykonywalnego. Jeśli używasz usług IIS do obsługi usługi, należy skopiować zawartość pliku App.config w pliku Web.config w katalogu wirtualnego.
