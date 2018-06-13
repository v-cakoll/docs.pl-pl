---
title: Wywołania zabezpieczeń bez autoryzacji
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3554644a7f73894703cc26ad11e4f7b9d58cab60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472576"
---
# <a name="security-calls-not-authorized"></a>Wywołania zabezpieczeń bez autoryzacji
Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`. Wskazuje on, że przychodzący komunikat pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.
