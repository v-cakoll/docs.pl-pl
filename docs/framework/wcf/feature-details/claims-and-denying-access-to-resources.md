---
title: Oświadczenia i odmawianie dostępu do zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: e5ecb71b7e0596b1732207b50e1b6087528bba3f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587043"
---
# <a name="claims-and-denying-access-to-resources"></a>Oświadczenia i odmawianie dostępu do zasobów
Windows Communication Foundation (WCF) obsługuje mechanizm autoryzacji oparty na oświadczeniach. Jak również umożliwienie dostępu do zasobów na podstawie obecności oświadczeń, systemy często odmawiają dostępu do zasobów na podstawie obecności oświadczeń. Takie systemy powinny sprawdzać <xref:System.IdentityModel.Policy.AuthorizationContext> oświadczenia, które powodują odmowę dostępu przed wyszukiwaniem oświadczeń, w wyniku których jest dozwolony dostęp.  
  
 Na przykład system może odmówić dostępu do zasobu wszystkim osobom, które mają wierzytelność z typem, z `Age` prawej strony <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> , i wartością zasobu tylko wtedy, `Under 21` gdy ta tożsamość ma również typ `Name` , po prawej stronie <xref:System.IdentityModel.Claims.Rights.Identity%2A> i wartość zasobu `Mallory` . W inny sposób system odmówi dostępu wszystkim osobom, które są w wieku poniżej 21 lat i udzielą dostępu, gdy nazwa jest Mallory. Aby poprawnie zaimplementować tę semantykę, ważne jest, aby najpierw wyszukać zgłoszenie `Age` i określić, czy wiek jest w wieku poniżej 21 lat. W przeciwnym razie, jeśli Mallory ma wartość 21, do zasobu można udzielić dostępu wyłącznie na podstawie tego `Name` żądania.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md)
- [Oświadczenia i tokeny](claims-and-tokens.md)
