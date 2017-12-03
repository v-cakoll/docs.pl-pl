---
title: "Działania środowiska uruchomieniowego w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 022f12448d697ba179fb3705f18962e6b0c44239
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="runtime-activities-in-wf"></a>Działania środowiska uruchomieniowego w WF
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]zawiera kilka działań dostarczane przez system do uzyskiwania dostępu do funkcji środowiska uruchomieniowego przepływu pracy, takich jak trwałości i kończenie działania.  
  
|Działanie|Opis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|Wyraźnie zażąda, że przepływ pracy utrwalić stanu.|  
|<xref:System.Activities.Statements.TerminateWorkflow>|Kończy uruchomione wystąpienie przepływu pracy.|  
|<xref:System.Activities.Statements.NoPersistScope>|Działanie kontenera, który uniemożliwia utrwalanie działań podrzędnych.|
