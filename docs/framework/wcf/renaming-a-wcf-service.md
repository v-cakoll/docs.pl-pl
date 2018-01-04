---
title: "Zmienianie nazwy usługi WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2ab3d780f85131fc7adf24c5f420bd5fe643d9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="renaming-a-wcf-service"></a>Zmienianie nazwy usługi WCF
W tym temacie opisano, jak można zmienić nazwy [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi.  
  
## <a name="renaming-a-wcf-service"></a>Zmienianie nazwy usługi WCF  
 Wykonaj poniższe kroki, aby zmienić nazwę usługi w programie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] szablonu,  
  
-   Zmień nazwę klasy, która implementuje usługę.  
  
-   W pliku konfiguracji usługi Zmień nazwę usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie. Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   Czy usługa jest webhosted, używa plik *.svc. Otwórz plik svc i zmodyfikować nazwę usługi, jak wskazano w poniższym przykładzie. Ten krok nie jest konieczne własnym obsługiwanych aplikacji, ponieważ nie ma żadnego pliku svc.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Zmiana nazwy kontraktu usługi WCF  
  
-   Wykonaj poniższe kroki, aby zmienić nazwę kontraktu usługi  
  
-   Zmień nazwę kontraktu usługi.  
  
-   W pliku konfiguracji usługi należy zmienić nazwę kontraktu usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie. Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
