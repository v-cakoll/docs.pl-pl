---
title: Wdrażanie projektu biblioteki WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 1ba26a7e68fe262dc5f4f569647af1ebb94e03a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785128"
---
# <a name="deploying-a-wcf-library-project"></a>Wdrażanie projektu biblioteki WCF
W tym temacie opisano, jak wdrożyć projekt biblioteki usługi Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Wdrażanie biblioteki usługi WCF  
 Biblioteki usługi WCF jest biblioteki dołączanej (dynamicznie DLL). W efekcie nie można wykonać na swoich własnych. Musi zostać wdrożone w środowisku hostingu. Aby uzyskać więcej informacji na temat tego procesu, zobacz [hostingu i korzystanie z usługi WCF](https://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Podobnie jak inne usługi WCF można wdrożyć biblioteki usługi WCF. Jednak należy pamiętać, że [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje konfiguracji dla bibliotek DLL. <xref:System.Configuration> obsługuje jeden plik konfiguracji na domeny aplikacji. Projekt biblioteki usługi WCF eliminuje to ograniczenie, dostarczając plik App.config dla biblioteki podczas programowania. Jednak po wdrożeniu nie jest rozpoznawany w pliku App.config.  
  
 Masz Przenieś swój kod konfiguracji do pliku konfiguracyjnego rozpoznawane przez środowisku macierzystym. Dla hostingu samodzielnego, należy skopiować zawartość pliku App.config do pliku App.config hostingu pliku wykonywalnego. Jeśli używasz usług IIS do hostowania usługi, należy skopiować zawartość pliku App.config do pliku Web.config w katalogu wirtualnego.
