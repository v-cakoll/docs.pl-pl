---
title: Rozszerzanie warstwy kanału
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 76ca76d7973403c657b8f68bfde9619df36f220e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797137"
---
# <a name="extending-the-channel-layer"></a>Rozszerzanie warstwy kanału
Warstwa kanału jest odpowiedzialna za wymianę komunikatów między klientami i usługami. Rozszerzenia kanału mogą implementować nowe funkcje protokołu, takie jak zabezpieczenia lub funkcje transportu, takie jak implementacja nowego transportu sieciowego do przenoszenia komunikatów protokołu SOAP.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd modelu kanału](channel-model-overview.md)  
 Zawiera ogólny przegląd informacji o kanałach, funkcjach, które zapewnia i jak działają zarówno w usłudze, jak i w aplikacji klienckiej.  
  
 [Opracowywanie kanałów](developing-channels.md)  
 Szczegółowo opisano role, które są odtwarzane przez różne typy infrastruktury kanałów, jak działa aparat stanu i cykl życia stanu, jak obsługiwać wyjątki i błędy, jak zaimplementować obsługę metadanych oraz jak kanały pracują z koderami komunikatów.  
  
 [Niestandardowe kodery](custom-encoders.md)  
 Opisuje rolę, jaką odgrywa kodery wiadomości w kanałach i jak ją skompilować.  
  
 [Niestandardowe uaktualnienia strumienia](custom-stream-upgrades.md)  
 Opisuje proces uaktualniania strumieni dostarczonych przez transporty ukierunkowane na strumień.
