---
title: Manipulowanie
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107890"
---
# <a name="tampering"></a>Manipulowanie
*Manipulowanie* polega na zmianę wiadomości lub dostarczania wiadomości i przy użyciu zmienionego komunikatu w celu innym niż co zostało przeznaczone.  
  
## <a name="do-not-disable-ws-addressing"></a>Nie można wyłączyć usługi WS-Addressing  
 Specyfikacja WS-Addressing zawiera nagłówki adresów dla każdej wiadomości, dzięki czemu adresat wiadomości sprawdzić nadawcy wiadomości. Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwość <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Gdy tryb zabezpieczeń jest ustawiony na komunikat i WS-Addressing jest wyłączona, osoba atakująca może wykonać żądania z klienta i wysyłać je do innej usługi, a druga usługa nie ma możliwości wykrywania, czy wiadomość pochodzi z oryginalnego klienta. W efekcie pierwszej usługi poudawać się klienta w przypadku drugiej usługi.  
  
 Aby temu zaradzić, nigdy nie ustawiono <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>i należy unikać użycia <xref:System.ServiceModel.Channels.MessageVersion>, takie jak statyczne <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> właściwość, która ustawia <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwość <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
