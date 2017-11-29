---
title: "Przegląd klasy SoundPlayer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6df44df3582ed806d338e2d4565c5c11f69ce21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="soundplayer-class-overview"></a>Przegląd klasy SoundPlayer
<xref:System.Media.SoundPlayer> Klasa umożliwia łatwe dołączanie dźwięków w aplikacji.  
  
 <xref:System.Media.SoundPlayer> Klasy odtwarzanie dźwięku plików w formacie .wav, lub od zasobu z lokalizacji UNC lub HTTP. Ponadto <xref:System.Media.SoundPlayer> klasa umożliwia ładowanie lub odtwarzanie dźwięków asynchronicznie.  
  
 Można również użyć <xref:System.Media.SystemSounds> klasę, aby odtwarzać dźwięki systemu typowych, w tym sygnału dźwiękowego.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Typowe właściwości, metod i zdarzeń  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A>Właściwość|Ścieżka pliku lub adres sieci Web dźwięku. Dopuszczalne wartości może być ścieżką UNC lub HTTP.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A>Właściwość|Wyrażony w milisekundach czas oczekiwania programu ładowanie dźwięku przed nią zgłasza wyjątek. Wartość domyślna to 10 sekund.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A>Właściwość|Wartość logiczna wskazująca, czy dźwięk zakończeniu ładowania.|  
|<xref:System.Media.SoundPlayer.Load%2A>— Metoda|Ładuje dźwięk synchronicznie.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A>— Metoda|Rozpoczyna ładowanie dźwięku asynchronicznie. Po zakończeniu ładowania zgłasza <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> zdarzeń.|  
|<xref:System.Media.SoundPlayer.Play%2A>— Metoda|Odtwarza dźwięk określony w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w nowego wątku.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A>— Metoda|Odtwarza dźwięk określony w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w bieżącym wątku.|  
|<xref:System.Media.SoundPlayer.Stop%2A>— Metoda|Zatrzymuje wszystkie obecnie odtwarzanie dźwięku.|  
|<xref:System.Media.SoundPlayer.LoadCompleted>zdarzenia|Uruchamiany po nastąpiła obciążenia dźwięku.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
