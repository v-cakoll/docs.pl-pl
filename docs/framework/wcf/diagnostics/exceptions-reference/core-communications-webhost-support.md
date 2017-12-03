---
title: "Podstawowe wiadomości: Obsługa hosta sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 707b97c49d6a6f5262719e91f8cb38fe7da53601
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-webhost-support"></a>Podstawowe wiadomości: Obsługa hosta sieci Web
W tym temacie wymieniono wszystkie wyjątki generowane przez obsługa hosta sieci Web.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|Hosting_CompatibilityServiceNotHosted|Ta usługa wymaga zgodności z platformą ASP.NET. Musi on również obsługiwane w usługach IIS. Albo hosta usługi w programie IIS ze zgodnością ASP.NET włączone w pliku Web.config lub ustaw właściwość AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode na wartość inną niż Required.|  
|Hosting_ListenerNotFoundForActivationInRecycling|Kanał nie jest aktywnie nasłuchujących pod określonym adresem. Jeśli odtwarzanie aplikacji usługi jest zamknięty.|  
|Hosting_NonHTTPInCompatibilityMode|Tylko protokoły, które są obsługiwane w obszarze zgodności z platformą ASP.NET są protokoły HTTP i HTTPS. Usuń wskazany punkt końcowy lub wyłącz zgodności z platformą ASP.NET dla aplikacji.|  
|Hosting_ProcessNotExecutingUnderHostedContext|Określony processcannot hostingu można wywołać w bieżącym środowisku macierzystym. Ten interfejs API wymaga, aby aplikacja wywołująca była obsługiwana w usługach IIS lub usługa aktywacji procesów systemu Windows.|  
|Hosting_ServiceCompatibilityRequire|Nie można aktywować usługi, ponieważ wymaga ona zgodności z platformą ASP.NET. Zgodność platformy ASP.NET nie jest włączona dla tej aplikacji. Włącz zgodności z platformą ASP.NET w pliku Web.config albo ustaw AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.|
