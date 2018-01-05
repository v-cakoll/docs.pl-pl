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
ms.workload: dotnet
ms.openlocfilehash: 3dc355fbe0d8262cb24779b99375d6075f758bbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="03a4e-102">Przegląd klasy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="03a4e-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="03a4e-103"><xref:System.Media.SoundPlayer> Klasa umożliwia łatwe dołączanie dźwięków w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03a4e-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="03a4e-104"><xref:System.Media.SoundPlayer> Klasy odtwarzanie dźwięku plików w formacie .wav, lub od zasobu z lokalizacji UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="03a4e-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="03a4e-105">Ponadto <xref:System.Media.SoundPlayer> klasa umożliwia ładowanie lub odtwarzanie dźwięków asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="03a4e-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="03a4e-106">Można również użyć <xref:System.Media.SystemSounds> klasę, aby odtwarzać dźwięki systemu typowych, w tym sygnału dźwiękowego.</span><span class="sxs-lookup"><span data-stu-id="03a4e-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="03a4e-107">Typowe właściwości, metod i zdarzeń</span><span class="sxs-lookup"><span data-stu-id="03a4e-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="03a4e-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="03a4e-108">Name</span></span>|<span data-ttu-id="03a4e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="03a4e-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="03a4e-110"><xref:System.Media.SoundPlayer.SoundLocation%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="03a4e-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="03a4e-111">Ścieżka pliku lub adres sieci Web dźwięku.</span><span class="sxs-lookup"><span data-stu-id="03a4e-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="03a4e-112">Dopuszczalne wartości może być ścieżką UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="03a4e-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="03a4e-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="03a4e-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="03a4e-114">Wyrażony w milisekundach czas oczekiwania programu ładowanie dźwięku przed nią zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="03a4e-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="03a4e-115">Wartość domyślna to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="03a4e-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="03a4e-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="03a4e-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="03a4e-117">Wartość logiczna wskazująca, czy dźwięk zakończeniu ładowania.</span><span class="sxs-lookup"><span data-stu-id="03a4e-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="03a4e-118"><xref:System.Media.SoundPlayer.Load%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="03a4e-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="03a4e-119">Ładuje dźwięk synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="03a4e-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="03a4e-120"><xref:System.Media.SoundPlayer.LoadAsync%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="03a4e-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="03a4e-121">Rozpoczyna ładowanie dźwięku asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="03a4e-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="03a4e-122">Po zakończeniu ładowania zgłasza <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="03a4e-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="03a4e-123"><xref:System.Media.SoundPlayer.Play%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="03a4e-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="03a4e-124">Odtwarza dźwięk określony w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="03a4e-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="03a4e-125"><xref:System.Media.SoundPlayer.PlaySync%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="03a4e-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="03a4e-126">Odtwarza dźwięk określony w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="03a4e-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="03a4e-127"><xref:System.Media.SoundPlayer.Stop%2A>— Metoda</span><span class="sxs-lookup"><span data-stu-id="03a4e-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="03a4e-128">Zatrzymuje wszystkie obecnie odtwarzanie dźwięku.</span><span class="sxs-lookup"><span data-stu-id="03a4e-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="03a4e-129"><xref:System.Media.SoundPlayer.LoadCompleted>zdarzenia</span><span class="sxs-lookup"><span data-stu-id="03a4e-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="03a4e-130">Uruchamiany po nastąpiła obciążenia dźwięku.</span><span class="sxs-lookup"><span data-stu-id="03a4e-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03a4e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03a4e-131">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>
