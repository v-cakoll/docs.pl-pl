---
title: 'Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
author: BrucePerlerMS
ms.openlocfilehash: 2d2f114d45675ece23f818d4d56bcc40684f9dbf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194084"
---
# <a name="endpoint-security-calls-not-authorized"></a>Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji
Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`. Wskazuje on, przychodząca wiadomość pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.
