---
title: Wywołania zabezpieczeń bez autoryzacji
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 492886a8e0083e8993b68ad710229113faf79e8d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198405"
---
# <a name="security-calls-not-authorized"></a>Wywołania zabezpieczeń bez autoryzacji
Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.  
  
## <a name="description"></a>Opis  
 Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`. Wskazuje on, przychodząca wiadomość pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.
