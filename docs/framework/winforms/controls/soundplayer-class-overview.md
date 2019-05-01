---
title: Przegląd klasy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972006"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="32868-102">Przegląd klasy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="32868-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="32868-103"><xref:System.Media.SoundPlayer> Klasy umożliwia łatwe uwzględnianie dźwięki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32868-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="32868-104"><xref:System.Media.SoundPlayer> Klasy można odtworzyć pliki dźwiękowe w formacie .wav lub od zasobu z lokalizacji UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="32868-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="32868-105">Ponadto <xref:System.Media.SoundPlayer> klasy można załadować lub odtwarzanie dźwięków asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="32868-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="32868-106">Można również użyć <xref:System.Media.SystemSounds> klasy, aby odtwarzać dźwięki systemu typowych, w tym sygnał dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="32868-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="32868-107">Często używanych właściwości, metody i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="32868-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="32868-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="32868-108">Name</span></span>|<span data-ttu-id="32868-109">Opis</span><span class="sxs-lookup"><span data-stu-id="32868-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="32868-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="32868-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="32868-111">Ścieżka pliku lub adres internetowy dźwięku.</span><span class="sxs-lookup"><span data-stu-id="32868-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="32868-112">Dopuszczalne wartości mogą być ścieżka UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="32868-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="32868-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="32868-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="32868-114">Liczba milisekund oczekiwania program załadować dźwięk przed nią zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="32868-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="32868-115">Wartość domyślna to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="32868-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="32868-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> Właściwość</span><span class="sxs-lookup"><span data-stu-id="32868-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="32868-117">Wartość logiczna wskazująca, czy dźwięk zakończy ładowanie.</span><span class="sxs-lookup"><span data-stu-id="32868-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="32868-118"><xref:System.Media.SoundPlayer.Load%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32868-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="32868-119">Ładuje dźwięk synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="32868-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="32868-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32868-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="32868-121">Rozpoczyna się ładowanie dźwięku asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="32868-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="32868-122">Po zakończeniu ładowania zgłasza <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32868-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="32868-123"><xref:System.Media.SoundPlayer.Play%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32868-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="32868-124">Odtwarza dźwięk, określone w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="32868-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="32868-125"><xref:System.Media.SoundPlayer.PlaySync%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32868-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="32868-126">Odtwarza dźwięk, określone w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="32868-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="32868-127"><xref:System.Media.SoundPlayer.Stop%2A> — Metoda</span><span class="sxs-lookup"><span data-stu-id="32868-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="32868-128">Zatrzymuje wszystkie obecnie odtwarzanie dźwięku.</span><span class="sxs-lookup"><span data-stu-id="32868-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="32868-129"><xref:System.Media.SoundPlayer.LoadCompleted> Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="32868-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="32868-130">Podniesiony po tym jak obciążenie dźwięku zostanie podjęta.</span><span class="sxs-lookup"><span data-stu-id="32868-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32868-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32868-131">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
