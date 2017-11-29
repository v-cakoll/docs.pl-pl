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
# <a name="soundplayer-class-overview"></a><span data-ttu-id="dbbdb-102">Przegląd klasy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="dbbdb-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="dbbdb-103"><xref:System.Media.SoundPlayer> Klasa umożliwia łatwe dołączanie dźwięków w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="dbbdb-104"><xref:System.Media.SoundPlayer> Klasy odtwarzanie dźwięku plików w formacie .wav, lub od zasobu z lokalizacji UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="dbbdb-105">Ponadto <xref:System.Media.SoundPlayer> klasa umożliwia ładowanie lub odtwarzanie dźwięków asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="dbbdb-106">Można również użyć <xref:System.Media.SystemSounds> klasę, aby odtwarzać dźwięki systemu typowych, w tym sygnału dźwiękowego.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="dbbdb-107">Typowe właściwości, metod i zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dbbdb-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="dbbdb-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="dbbdb-108">Name</span></span>|<span data-ttu-id="dbbdb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dbbdb-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="dbbdb-110"><xref:System.Media.SoundPlayer.SoundLocation%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="dbbdb-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="dbbdb-111">Ścieżka pliku lub adres sieci Web dźwięku.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="dbbdb-112">Dopuszczalne wartości może być ścieżką UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="dbbdb-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="dbbdb-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="dbbdb-114">Wyrażony w milisekundach czas oczekiwania programu ładowanie dźwięku przed nią zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="dbbdb-115">Wartość domyślna to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="dbbdb-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="dbbdb-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="dbbdb-117">Wartość logiczna wskazująca, czy dźwięk zakończeniu ładowania.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="dbbdb-118"><xref:System.Media.SoundPlayer.Load%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="dbbdb-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="dbbdb-119">Ładuje dźwięk synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="dbbdb-120"><xref:System.Media.SoundPlayer.LoadAsync%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="dbbdb-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="dbbdb-121">Rozpoczyna ładowanie dźwięku asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="dbbdb-122">Po zakończeniu ładowania zgłasza <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="dbbdb-123"><xref:System.Media.SoundPlayer.Play%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="dbbdb-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="dbbdb-124">Odtwarza dźwięk określony w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="dbbdb-125"><xref:System.Media.SoundPlayer.PlaySync%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="dbbdb-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="dbbdb-126">Odtwarza dźwięk określony w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="dbbdb-127"><xref:System.Media.SoundPlayer.Stop%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="dbbdb-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="dbbdb-128">Zatrzymuje wszystkie obecnie odtwarzanie dźwięku.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="dbbdb-129"><xref:System.Media.SoundPlayer.LoadCompleted>zdarzenia</span><span class="sxs-lookup"><span data-stu-id="dbbdb-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="dbbdb-130">Uruchamiany po nastąpiła obciążenia dźwięku.</span><span class="sxs-lookup"><span data-stu-id="dbbdb-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbbdb-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbbdb-131">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
