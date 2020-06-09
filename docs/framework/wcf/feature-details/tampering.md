---
title: Manipulowanie
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600714"
---
# <a name="tampering"></a>Manipulowanie
*Manipulowanie* to czynność polegająca na zmianie wiadomości lub dostarczeniu wiadomości, a także przy użyciu zmienionego komunikatu do celów innych niż to, do czego została zaprojektowana.  
  
## <a name="do-not-disable-ws-addressing"></a>Nie należy wyłączać usługi WS-Addressing  
 Specyfikacja WS-Addressing zawiera nagłówki adresów dla każdego komunikatu, umożliwiając odbiorcom komunikatu zweryfikowanie nadawcy wiadomości. Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> Właściwość na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
 Gdy tryb zabezpieczeń jest ustawiony na komunikat, a Usługa WS-Addressing jest wyłączona, osoba atakująca może wykonać żądanie od klienta i wysłać ją do innej usługi, a druga usługa nie ma możliwości wykrycia, że wiadomość pochodzi od oryginalnego klienta. W efekcie pierwsza usługa może poudawać, że jest klientem podczas rozmowy z drugą usługą.  
  
 Aby rozwiązać ten problem, nigdy nie ustawiaj <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> i Unikaj używania <xref:System.ServiceModel.Channels.MessageVersion> , takich jak właściwość statyczna <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> , która ustawia <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> Właściwość na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
## <a name="see-also"></a>Zobacz też

- [Zagadnienia dotyczące zabezpieczeń](security-considerations-in-wcf.md)
- [Ujawnianie informacji](information-disclosure.md)
- [Podniesienie uprawnień](elevation-of-privilege.md)
- [Odmowa usługi](denial-of-service.md)
- [Nieobsługiwane scenariusze](unsupported-scenarios.md)
- [Ataki oparte na metodzie powtórzeń](replay-attacks.md)
