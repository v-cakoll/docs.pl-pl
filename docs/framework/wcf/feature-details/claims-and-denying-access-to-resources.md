---
title: "Oświadczenia i odmawianie dostępu do zasobów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 156856ddd1a4c3b1d8f77a8a61f7e0336f993839
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-denying-access-to-resources"></a>Oświadczenia i odmawianie dostępu do zasobów
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]obsługuje mechanizm autoryzacji opartej na oświadczeniach. A także zezwalanie na dostęp do zasobów na podstawie obecności oświadczenia, systemów często odmówić dostępu do zasobów na podstawie obecności oświadczenia. Należy zbadać takich systemów <xref:System.IdentityModel.Policy.AuthorizationContext> oświadczeń, które powodują powstanie dostępu przed wyszukiwanie oświadczeń, których wynikiem jest dozwolony dostęp do.  
  
 Na przykład system może być odmowa dostępu do zasobu dla każdego, kto ma oświadczenie o typie z `Age`, prawej strony <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i wartości zasobów `Under 21` tylko po jego tożsamość ma również oświadczenie typu `Name`, po prawej <xref:System.IdentityModel.Claims.Rights.Identity%2A>, i wartości zasobów `Mallory`. Innymi słowy, systemu nie zezwala na dostęp do każdego, kto jest 21 roku życia i nieograniczony dostęp, gdy nazwa Mallory. Aby prawidłowo zaimplementować to semantyczne, ważne jest, aby wyszukać `Age` oświadczeń najpierw oraz określają, czy w obszarze 21 lat ważności. W przeciwnym razie, jeśli Mallory znajduje się w obszarze 21, następnie zasobu może otrzymać dostęp wyłącznie w oparciu o `Name` oświadczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
