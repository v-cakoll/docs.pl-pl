---
title: Uzyskiwanie dostępu do zasobów komputera
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 9595abaa1daa2b4a4436577d58856183dcb4d9ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401787"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="3527f-102">Uzyskiwanie dostępu do zasobów komputera (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3527f-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="3527f-103">`My.Computer`Obiekt jest jednym z trzech centralnych obiektów w `My` , zapewniając dostęp do informacji i często używanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="3527f-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="3527f-104">`My.Computer`dostarcza metody, właściwości i zdarzenia w celu uzyskania dostępu do komputera, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="3527f-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="3527f-105">Jego obiekty obejmują:</span><span class="sxs-lookup"><span data-stu-id="3527f-105">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="3527f-106">Schowek ( <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy> )</span><span class="sxs-lookup"><span data-stu-id="3527f-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="3527f-107">Rejestr ( <xref:Microsoft.VisualBasic.MyServices.RegistryProxy> )</span><span class="sxs-lookup"><span data-stu-id="3527f-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3527f-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3527f-108">In this section</span></span>

[<span data-ttu-id="3527f-109">Odtwarzanie dźwięków</span><span class="sxs-lookup"><span data-stu-id="3527f-109">Playing Sounds</span></span>](playing-sounds.md)  
<span data-ttu-id="3527f-110">Wyświetla listę zadań skojarzonych z `My.Computer.Audio` , takich jak odtwarzanie dźwięku w tle.</span><span class="sxs-lookup"><span data-stu-id="3527f-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="3527f-111">Zapisywanie danych w schowku i odczytywanie ich z niego</span><span class="sxs-lookup"><span data-stu-id="3527f-111">Storing Data to and Reading from the Clipboard</span></span>](storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="3527f-112">Wyświetla listę zadań skojarzonych z `My.Computer.Clipboard` , takich jak odczytywanie danych z lub zapisywanie danych w Schowku.</span><span class="sxs-lookup"><span data-stu-id="3527f-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="3527f-113">Pobieranie informacji na temat komputera</span><span class="sxs-lookup"><span data-stu-id="3527f-113">Getting Information about the Computer</span></span>](getting-information-about-the-computer.md)  
<span data-ttu-id="3527f-114">Wyświetla listę zadań skojarzonych z `My.Computer.Info` , takich jak określanie pełnej nazwy lub adresów IP komputera.</span><span class="sxs-lookup"><span data-stu-id="3527f-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="3527f-115">Uzyskiwanie dostępu do klawiatury</span><span class="sxs-lookup"><span data-stu-id="3527f-115">Accessing the Keyboard</span></span>](accessing-the-keyboard.md)  
<span data-ttu-id="3527f-116">Wyświetla listę zadań skojarzonych z `My.Computer.Keyboard` , takich jak określenie, czy Caps Lock jest włączona.</span><span class="sxs-lookup"><span data-stu-id="3527f-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="3527f-117">Uzyskiwanie dostępu do myszy</span><span class="sxs-lookup"><span data-stu-id="3527f-117">Accessing the Mouse</span></span>](accessing-the-mouse.md)  
<span data-ttu-id="3527f-118">Wyświetla listę zadań skojarzonych z `My.Computer.Mouse` , takich jak określenie, czy mysz jest obecna.</span><span class="sxs-lookup"><span data-stu-id="3527f-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="3527f-119">Przeprowadzanie operacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="3527f-119">Performing Network Operations</span></span>](performing-network-operations.md)  
<span data-ttu-id="3527f-120">Wyświetla listę zadań skojarzonych z `My.Computer.Network` , takich jak przekazywanie lub pobieranie plików.</span><span class="sxs-lookup"><span data-stu-id="3527f-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="3527f-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="3527f-121">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)  
<span data-ttu-id="3527f-122">Wyświetla listę zadań skojarzonych z `My.Computer.Ports` , takich jak wyświetlanie dostępnych portów seryjnych lub wysyłanie ciągów do portów seryjnych.</span><span class="sxs-lookup"><span data-stu-id="3527f-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="3527f-123">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="3527f-123">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="3527f-124">Wyświetla listę zadań skojarzonych z `My.Computer.Registry` , takich jak odczytywanie danych z lub zapisywanie danych w kluczach rejestru.</span><span class="sxs-lookup"><span data-stu-id="3527f-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
