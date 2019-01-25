---
title: Przegląd klasy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 041e7d0170bc98797278e209fd86cff0f82db9fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690695"
---
# <a name="soundplayer-class-overview"></a>Przegląd klasy SoundPlayer
<xref:System.Media.SoundPlayer> Klasy umożliwia łatwe uwzględnianie dźwięki w aplikacji.  
  
 <xref:System.Media.SoundPlayer> Klasy można odtworzyć pliki dźwiękowe w formacie .wav lub od zasobu z lokalizacji UNC lub HTTP. Ponadto <xref:System.Media.SoundPlayer> klasy można załadować lub odtwarzanie dźwięków asynchronicznie.  
  
 Można również użyć <xref:System.Media.SystemSounds> klasy, aby odtwarzać dźwięki systemu typowych, w tym sygnał dźwiękowy.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Często używanych właściwości, metody i zdarzenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> Właściwość|Ścieżka pliku lub adres internetowy dźwięku. Dopuszczalne wartości mogą być ścieżka UNC lub HTTP.|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> Właściwość|Liczba milisekund oczekiwania program załadować dźwięk przed nią zgłasza wyjątek. Wartość domyślna to 10 sekund.|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Właściwość|Wartość logiczna wskazująca, czy dźwięk zakończy ładowanie.|  
|<xref:System.Media.SoundPlayer.Load%2A> — Metoda|Ładuje dźwięk synchronicznie.|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> — Metoda|Rozpoczyna się ładowanie dźwięku asynchronicznie. Po zakończeniu ładowania zgłasza <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> zdarzeń.|  
|<xref:System.Media.SoundPlayer.Play%2A> — Metoda|Odtwarza dźwięk, określone w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości nowego wątku.|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> — Metoda|Odtwarza dźwięk, określone w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w bieżącym wątku.|  
|<xref:System.Media.SoundPlayer.Stop%2A> — Metoda|Zatrzymuje wszystkie obecnie odtwarzanie dźwięku.|  
|<xref:System.Media.SoundPlayer.LoadCompleted> Zdarzenia|Podniesiony po tym jak obciążenie dźwięku zostanie podjęta.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
