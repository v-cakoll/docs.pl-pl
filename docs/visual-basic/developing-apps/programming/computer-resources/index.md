---
title: Uzyskiwanie dostępu do zasobów komputera (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 5eb240b23d255987e96c58fefc7007c8030c6502
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524405"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="0bacc-102">Uzyskiwanie dostępu do zasobów komputera (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bacc-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="0bacc-103">Obiekt `My.Computer` jest jednym z trzech centralnych obiektów w `My`, zapewniając dostęp do informacji i często używanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0bacc-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="0bacc-104">`My.Computer` udostępnia metody, właściwości i zdarzenia w celu uzyskania dostępu do komputera, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="0bacc-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="0bacc-105">Jego obiekty obejmują:</span><span class="sxs-lookup"><span data-stu-id="0bacc-105">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="0bacc-106">Schowek (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="0bacc-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="0bacc-107">Rejestr (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="0bacc-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0bacc-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0bacc-108">In this section</span></span>

[<span data-ttu-id="0bacc-109">Odtwarzanie dźwięków</span><span class="sxs-lookup"><span data-stu-id="0bacc-109">Playing Sounds</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md)  
<span data-ttu-id="0bacc-110">Wyświetla listę zadań skojarzonych z `My.Computer.Audio`, takich jak odtwarzanie dźwięku w tle.</span><span class="sxs-lookup"><span data-stu-id="0bacc-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="0bacc-111">Zapisywanie danych w schowku i odczytywanie ich z niego</span><span class="sxs-lookup"><span data-stu-id="0bacc-111">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="0bacc-112">Wyświetla listę zadań skojarzonych z `My.Computer.Clipboard`, takich jak odczytywanie danych z lub zapisywanie danych w Schowku.</span><span class="sxs-lookup"><span data-stu-id="0bacc-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="0bacc-113">Pobieranie informacji na temat komputera</span><span class="sxs-lookup"><span data-stu-id="0bacc-113">Getting Information about the Computer</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md)  
<span data-ttu-id="0bacc-114">Wyświetla listę zadań skojarzonych z `My.Computer.Info`, takich jak określanie pełnych nazw lub adresów IP komputera.</span><span class="sxs-lookup"><span data-stu-id="0bacc-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="0bacc-115">Uzyskiwanie dostępu do klawiatury</span><span class="sxs-lookup"><span data-stu-id="0bacc-115">Accessing the Keyboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
<span data-ttu-id="0bacc-116">Wyświetla listę zadań skojarzonych z `My.Computer.Keyboard`, takich jak określenie, czy Caps Lock jest włączona.</span><span class="sxs-lookup"><span data-stu-id="0bacc-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="0bacc-117">Uzyskiwanie dostępu do myszy</span><span class="sxs-lookup"><span data-stu-id="0bacc-117">Accessing the Mouse</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md)  
<span data-ttu-id="0bacc-118">Wyświetla listę zadań skojarzonych z `My.Computer.Mouse`, takich jak określenie, czy mysz jest obecna.</span><span class="sxs-lookup"><span data-stu-id="0bacc-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="0bacc-119">Przeprowadzanie operacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="0bacc-119">Performing Network Operations</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md)  
<span data-ttu-id="0bacc-120">Wyświetla listę zadań skojarzonych z `My.Computer.Network`, takich jak przekazywanie lub pobieranie plików.</span><span class="sxs-lookup"><span data-stu-id="0bacc-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="0bacc-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="0bacc-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)  
<span data-ttu-id="0bacc-122">Wyświetla listę zadań skojarzonych z `My.Computer.Ports`, takich jak wyświetlanie dostępnych portów seryjnych lub wysyłanie ciągów do portów seryjnych.</span><span class="sxs-lookup"><span data-stu-id="0bacc-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="0bacc-123">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="0bacc-123">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="0bacc-124">Wyświetla listę zadań skojarzonych z `My.Computer.Registry`, takich jak odczytywanie danych z lub zapisywanie danych w kluczach rejestru.</span><span class="sxs-lookup"><span data-stu-id="0bacc-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
