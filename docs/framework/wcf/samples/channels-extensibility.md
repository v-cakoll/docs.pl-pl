---
title: Rozszerzalność kanałów
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 9dbae26a548bdc8a8cfb05a3dd90db91475b55ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600636"
---
# <a name="channels-extensibility"></a>Rozszerzalność kanałów
Ta sekcja zawiera przykłady demonstrujące kanały niestandardowe.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Lokalny kanał](local-channel.md)  
 Pokazuje kanał lokalny, kanał transportu WCF używany do komunikacji w ramach tej samej domeny aplikacji.  
  
 [Niezawodny bezpieczny profil](reliable-secure-profile.md)  
 Pokazuje, jak tworzyć usługi WCF i niezawodne bezpieczne profile (RSP).  
  
 [Niestandardowy dyspozytor kanału](custom-channel-dispatcher.md)  
 Demonstruje sposób tworzenia stosu kanału w sposób niestandardowy przez implementację <xref:System.ServiceModel.ServiceHostBase> bezpośrednio i sposób tworzenia niestandardowego dyspozytora kanału w środowisku hosta sieci Web.  
  
 [Kanał dzielący na fragmenty](chunking-channel.md)  
 Pokazuje, jak ograniczyć ilość pamięci używanej do buforowania dużych komunikatów wysyłanych za pomocą programu WCF.
  
 [HttpCookieSession](httpcookiesession.md)  
 Pokazuje, jak utworzyć niestandardowy kanał protokołu, aby używać plików cookie protokołu HTTP do zarządzania sesją.  
  
 [Niestandardowy element przechwytujący komunikaty](custom-message-interceptor.md)  
 Demonstruje sposób implementacji elementu niestandardowego powiązania, który tworzy fabryki kanałów i odbiorników kanałów do przechwytywania wszystkich komunikatów przychodzących i wychodzących w określonym punkcie w stosie czasu wykonywania.
