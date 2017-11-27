---
title: "Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 59922fad717ea464d8e023c25c8e17a3c17f1846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-calls-not-authorized"></a>Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji
Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`. Wskazuje on, że przychodzący komunikat pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.
