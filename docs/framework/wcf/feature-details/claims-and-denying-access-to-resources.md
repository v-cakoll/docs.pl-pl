---
title: Oświadczenia i odmawianie dostępu do zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 4f48c59090579f4b451f615bb792a4dcb73f6df5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079516"
---
# <a name="claims-and-denying-access-to-resources"></a>Oświadczenia i odmawianie dostępu do zasobów
Windows Communication Foundation (WCF) obsługuje mechanizm autoryzacji opartej na oświadczeniach. A także zezwalanie na dostęp do zasobów na podstawie obecności oświadczenia, systemy często zezwoli na dostęp do zasobów na podstawie obecności oświadczenia. Należy sprawdzić takich systemów <xref:System.IdentityModel.Policy.AuthorizationContext> oświadczeń, których wynikiem dostępu przed szuka oświadczenia, których wynikiem dostęp jest dozwolony.  
  
 Na przykład, system może zezwoli na dostęp do zasobu dla każdego, kto ma oświadczenie z typem elementu `Age`, po prawej stronie <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>i wartości zasobów `Under 21` tylko po tej tożsamości ma również oświadczenie typu `Name`, po prawej stronie <xref:System.IdentityModel.Claims.Rights.Identity%2A>, i wartości zasobów `Mallory`. Innymi słowy, system nie zezwala na dostęp do wszystkich użytkowników w obszarze 21 lat i nieograniczony dostęp, kiedy nazwa jest Mallory. Aby prawidłowo zaimplementować to semantyczne, ważne jest do wyszukania `Age` oświadczeń najpierw i ustalić, czy w obszarze 21 lat wieku. W przeciwnym razie, jeśli Mallory znajduje się w obszarze 21, następnie zasobu może otrzymać dostęp wyłącznie w oparciu o `Name` oświadczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
