---
title: Oświadczenia i odmawianie dostępu do zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: a53affe5e21b5ef532e7094eed032b44f5a5ea7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488614"
---
# <a name="claims-and-denying-access-to-resources"></a>Oświadczenia i odmawianie dostępu do zasobów
Windows Communication Foundation (WCF) obsługuje mechanizm autoryzacji opartej na oświadczeniach. A także zezwalanie na dostęp do zasobów na podstawie obecności oświadczenia, systemów często odmówić dostępu do zasobów na podstawie obecności oświadczenia. Należy zbadać takich systemów <xref:System.IdentityModel.Policy.AuthorizationContext> oświadczeń, które powodują powstanie dostępu przed wyszukiwanie oświadczeń, których wynikiem jest dozwolony dostęp do.  
  
 Na przykład system może być odmowa dostępu do zasobu dla każdego, kto ma oświadczenie o typie z `Age`, prawej strony <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i wartości zasobów `Under 21` tylko po jego tożsamość ma również oświadczenie typu `Name`, po prawej <xref:System.IdentityModel.Claims.Rights.Identity%2A>, i wartości zasobów `Mallory`. Innymi słowy, systemu nie zezwala na dostęp do każdego, kto jest 21 roku życia i nieograniczony dostęp, gdy nazwa Mallory. Aby prawidłowo zaimplementować to semantyczne, ważne jest, aby wyszukać `Age` oświadczeń najpierw oraz określają, czy w obszarze 21 lat ważności. W przeciwnym razie, jeśli Mallory znajduje się w obszarze 21, następnie zasobu może otrzymać dostęp wyłącznie w oparciu o `Name` oświadczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
