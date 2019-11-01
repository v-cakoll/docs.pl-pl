---
title: 'Nie można zapisać do pliku wyjściowego „<filename>”: <error>'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 087735722fcd4dd789e25aacf6eeefffb490dac5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198190"
---
# <a name="unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="60115-102">Nie można zapisać do pliku wyjściowego "\<filename >": błąd \<</span><span class="sxs-lookup"><span data-stu-id="60115-102">Unable to write to output file '\<filename>': \<error></span></span>
<span data-ttu-id="60115-103">Wystąpił problem podczas tworzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="60115-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="60115-104">Nie można otworzyć pliku wyjściowego do zapisu.</span><span class="sxs-lookup"><span data-stu-id="60115-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="60115-105">Plik (lub folder zawierający plik) może być otwarty do wyłącznego użytku przez inny proces lub może mieć ustawiony atrybut tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="60115-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="60115-106">Typowe sytuacje, w których plik jest otwierany wyłącznie:</span><span class="sxs-lookup"><span data-stu-id="60115-106">Common situations where a file is opened exclusively are:</span></span>  
  
- <span data-ttu-id="60115-107">Aplikacja jest już uruchomiona i używa jej plików.</span><span class="sxs-lookup"><span data-stu-id="60115-107">The application is already running and using its files.</span></span> <span data-ttu-id="60115-108">Aby rozwiązać ten problem, upewnij się, że aplikacja nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="60115-108">To solve this problem, make sure that the application is not running.</span></span>  
  
- <span data-ttu-id="60115-109">Inna aplikacja otworzyła plik.</span><span class="sxs-lookup"><span data-stu-id="60115-109">Another application has opened the file.</span></span> <span data-ttu-id="60115-110">Aby rozwiązać ten problem, upewnij się, że żadne inne aplikacje nie uzyskują dostępu do plików.</span><span class="sxs-lookup"><span data-stu-id="60115-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="60115-111">Nie zawsze jest oczywiste, która aplikacja uzyskuje dostęp do Twoich plików; w takim przypadku ponowne uruchomienie komputera może być Najprostszym sposobem na zakończenie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60115-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="60115-112">Jeśli nawet jeden z plików wyjściowych projektu jest oznaczony jako tylko do odczytu, zostanie zgłoszony ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="60115-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="60115-113">**Identyfikator błędu:** BC31019</span><span class="sxs-lookup"><span data-stu-id="60115-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60115-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="60115-114">To correct this error</span></span>  
  
1. <span data-ttu-id="60115-115">Skompiluj ponownie program, aby zobaczyć, czy błąd jest powtarzany.</span><span class="sxs-lookup"><span data-stu-id="60115-115">Compile the program again to see if the error recurs.</span></span>  
  
2. <span data-ttu-id="60115-116">Jeśli błąd będzie nadal występował, Zapisz swoją pracę i ponownie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60115-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3. <span data-ttu-id="60115-117">Jeśli błąd będzie się powtarzać, uruchom ponownie komputer.</span><span class="sxs-lookup"><span data-stu-id="60115-117">If the error continues, restart the computer.</span></span>  
  
4. <span data-ttu-id="60115-118">Jeśli błąd się powtarza, zainstaluj ponownie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="60115-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5. <span data-ttu-id="60115-119">Jeśli błąd będzie się powtarzać po ponownej instalacji, powiadom firmę Microsoft o pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="60115-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="60115-120">Aby sprawdzić atrybuty plików w Eksploratorze plików</span><span class="sxs-lookup"><span data-stu-id="60115-120">To check file attributes in File Explorer</span></span>  
  
1. <span data-ttu-id="60115-121">Otwórz folder, który Cię interesuje.</span><span class="sxs-lookup"><span data-stu-id="60115-121">Open the folder you are interested in.</span></span>  
  
2. <span data-ttu-id="60115-122">Kliknij ikonę **widoki** i wybierz pozycję **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="60115-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3. <span data-ttu-id="60115-123">Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybierz z listy rozwijanej **atrybuty** .</span><span class="sxs-lookup"><span data-stu-id="60115-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="60115-124">Aby zmienić atrybuty pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="60115-124">To change the attributes of a file or folder</span></span>  
  
1. <span data-ttu-id="60115-125">W **Eksploratorze plików**kliknij prawym przyciskiem myszy plik lub folder, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="60115-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2. <span data-ttu-id="60115-126">W sekcji **atrybuty** karty **Ogólne** wyczyść pole **tylko do odczytu** .</span><span class="sxs-lookup"><span data-stu-id="60115-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3. <span data-ttu-id="60115-127">Naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="60115-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60115-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60115-128">See also</span></span>

- [<span data-ttu-id="60115-129">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="60115-129">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
