---
title: Zagadnienia dotyczące zabezpieczeń w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: ed0f018e0151e68afeb9a4747bf8a260faa184b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601039"
---
# <a name="security-considerations-in-wcf"></a>Zagadnienia dotyczące zabezpieczeń w programie WCF
W tematach w tej sekcji przedstawiono różne elementy związane z zabezpieczeniami, które należy wziąć pod uwagę podczas projektowania aplikacji Windows Communication Foundation (WCF).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Ujawnianie informacji](information-disclosure.md)  
 W tym artykule omówiono różne sposoby, w których informacje mogą być ujawnione lub zaatakowane oraz jak można je złagodzić.  
  
 [Podniesienie uprawnień](elevation-of-privilege.md)  
 W tym artykule omówiono skutki udzielenia uprawnień autoryzacji osoby atakującej poza tymi, które zostały początkowo przyznane i jak można je złagodzić.  
  
 [Odmowa usługi](denial-of-service.md)  
 W tym artykule omówiono, co się dzieje, gdy system nie może prawidłowo przetwarzać komunikatów i jak można je ograniczyć.  
  
 [Manipulowanie](tampering.md)  
 W tym artykule omówiono zmiany komunikatów lub dostarczania komunikatów oraz sposób ich ograniczania.  
  
 [Ataki oparte na metodzie powtórzeń](replay-attacks.md)  
 W tym artykule omówiono, co się dzieje, gdy osoba atakująca skopiuje strumień komunikatów między dwiema stronami i odtwarza strumień do jednej lub kilku stron, a także jak to zrobić.  
  
 [Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji](security-considerations-for-secure-sessions.md)  
 W tym artykule omówiono następujące elementy, które mają wpływ na zabezpieczenia podczas implementowania bezpiecznych sesji.  
  
 [Nieobsługiwane scenariusze](unsupported-scenarios.md)  
 Wyświetla listę różnych scenariuszy, które nie obsługują określonego aspektu zabezpieczeń i należy je unikać lub rozważać.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>Zobacz też

- [Bezpieczeństwo](security.md)
