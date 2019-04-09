---
title: Przegląd klasy SoundPlayer
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195010"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="eafe9-102">Przegląd klasy SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="eafe9-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="eafe9-103"><xref:System.Media.SoundPlayer> Klasy umożliwia łatwe uwzględnianie dźwięki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eafe9-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="eafe9-104"><xref:System.Media.SoundPlayer> Klasy można odtworzyć pliki dźwiękowe w formacie .wav lub od zasobu z lokalizacji UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="eafe9-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="eafe9-105">Ponadto <xref:System.Media.SoundPlayer> klasy można załadować lub odtwarzanie dźwięków asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="eafe9-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="eafe9-106">Można również użyć <xref:System.Media.SystemSounds> klasy, aby odtwarzać dźwięki systemu typowych, w tym sygnał dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="eafe9-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="eafe9-107">Często używanych właściwości, metody i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="eafe9-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="eafe9-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="eafe9-108">Name</span></span>|<span data-ttu-id="eafe9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eafe9-109">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Media.SoundPlayer.SoundLocation%2A> <span data-ttu-id="eafe9-110">property</span><span class="sxs-lookup"><span data-stu-id="eafe9-110">property</span></span>|<span data-ttu-id="eafe9-111">Ścieżka pliku lub adres internetowy dźwięku.</span><span class="sxs-lookup"><span data-stu-id="eafe9-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="eafe9-112">Dopuszczalne wartości mogą być ścieżka UNC lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="eafe9-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadTimeout%2A> <span data-ttu-id="eafe9-113">property</span><span class="sxs-lookup"><span data-stu-id="eafe9-113">property</span></span>|<span data-ttu-id="eafe9-114">Liczba milisekund oczekiwania program załadować dźwięk przed nią zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="eafe9-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="eafe9-115">Wartość domyślna to 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="eafe9-115">The default is 10 seconds.</span></span>|  
|<xref:System.Media.SoundPlayer.IsLoadCompleted%2A> <span data-ttu-id="eafe9-116">property</span><span class="sxs-lookup"><span data-stu-id="eafe9-116">property</span></span>|<span data-ttu-id="eafe9-117">Wartość logiczna wskazująca, czy dźwięk zakończy ładowanie.</span><span class="sxs-lookup"><span data-stu-id="eafe9-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<xref:System.Media.SoundPlayer.Load%2A> <span data-ttu-id="eafe9-118">— metoda</span><span class="sxs-lookup"><span data-stu-id="eafe9-118">method</span></span>|<span data-ttu-id="eafe9-119">Ładuje dźwięk synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="eafe9-119">Loads a sound synchronously.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadAsync%2A> <span data-ttu-id="eafe9-120">— metoda</span><span class="sxs-lookup"><span data-stu-id="eafe9-120">method</span></span>|<span data-ttu-id="eafe9-121">Rozpoczyna się ładowanie dźwięku asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="eafe9-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="eafe9-122">Po zakończeniu ładowania zgłasza <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="eafe9-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<xref:System.Media.SoundPlayer.Play%2A> <span data-ttu-id="eafe9-123">— metoda</span><span class="sxs-lookup"><span data-stu-id="eafe9-123">method</span></span>|<span data-ttu-id="eafe9-124">Odtwarza dźwięk, określone w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości nowego wątku.</span><span class="sxs-lookup"><span data-stu-id="eafe9-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<xref:System.Media.SoundPlayer.PlaySync%2A> <span data-ttu-id="eafe9-125">— metoda</span><span class="sxs-lookup"><span data-stu-id="eafe9-125">method</span></span>|<span data-ttu-id="eafe9-126">Odtwarza dźwięk, określone w <xref:System.Media.SoundPlayer.SoundLocation%2A> lub <xref:System.Media.SoundPlayer.Stream%2A> właściwości w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="eafe9-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<xref:System.Media.SoundPlayer.Stop%2A> <span data-ttu-id="eafe9-127">— metoda</span><span class="sxs-lookup"><span data-stu-id="eafe9-127">method</span></span>|<span data-ttu-id="eafe9-128">Zatrzymuje wszystkie obecnie odtwarzanie dźwięku.</span><span class="sxs-lookup"><span data-stu-id="eafe9-128">Stops any sound currently playing.</span></span>|  
|<xref:System.Media.SoundPlayer.LoadCompleted> <span data-ttu-id="eafe9-129">zdarzenie</span><span class="sxs-lookup"><span data-stu-id="eafe9-129">event</span></span>|<span data-ttu-id="eafe9-130">Podniesiony po tym jak obciążenie dźwięku zostanie podjęta.</span><span class="sxs-lookup"><span data-stu-id="eafe9-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eafe9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eafe9-131">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
