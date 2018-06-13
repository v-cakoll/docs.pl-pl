---
title: Wdrażanie projektu biblioteki WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: fb400a4d1ebba691222ad7fc9d2c09f1051591da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803026"
---
# <a name="deploying-a-wcf-library-project"></a>Wdrażanie projektu biblioteki WCF
W tym temacie opisano, jak można wdrożyć projektu biblioteki usługi Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Wdrażanie biblioteki usługi WCF  
 Biblioteki usługi WCF jest biblioteki dołączanej (dynamicznie DLL). W efekcie nie można wykonać samodzielnie. Musi zostać wdrożony w środowisku macierzystym. Aby uzyskać więcej informacji o tym procesie, zobacz [hostingu i korzystanie z usługi WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Podobnie jak inne usługi WCF można wdrożyć biblioteki usługi WCF. Jednak należy pamiętać, że [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje konfiguracji dla bibliotek DLL. <xref:System.Configuration> obsługuje jeden plik konfiguracji na domenie aplikacji. Projekt biblioteki usługi WCF eliminuje to ograniczenie przez zapewnienie podczas tworzenia pliku App.config dla biblioteki. Jednak po wdrożeniu nie jest rozpoznawana pliku App.config.  
  
 Masz Przenieś swój kod konfiguracji do pliku konfiguracyjnego rozpoznaje środowisku macierzystym. Dla hostingu samodzielnego, należy skopiować zawartość pliku App.config w pliku App.config hostingu pliku wykonywalnego. Jeśli używasz usług IIS do obsługi usługi, należy skopiować zawartość pliku App.config w pliku Web.config w katalogu wirtualnego.
