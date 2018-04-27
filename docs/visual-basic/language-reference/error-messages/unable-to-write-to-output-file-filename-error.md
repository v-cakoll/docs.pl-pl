---
title: 'Nie można zapisać do pliku wyjściowego &#39; &lt;filename&gt;&#39;: &lt;błąd&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a183f81a73c3c8034d9ba7366be8b36d425263da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="86fac-102">Nie można zapisać do pliku wyjściowego &#39; &lt;filename&gt;&#39;: &lt;błąd&gt;</span><span class="sxs-lookup"><span data-stu-id="86fac-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="86fac-103">Wystąpił problem podczas tworzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="86fac-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="86fac-104">Nie można otworzyć pliku wyjściowego do zapisu.</span><span class="sxs-lookup"><span data-stu-id="86fac-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="86fac-105">Plik (lub folderu zawierającego plik) może być otwarty w trybie wyłączności przez inny proces lub może mieć jego ustawiony atrybut tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="86fac-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="86fac-106">Typowe sytuacje, gdy plik jest otwarty w trybie wyłączności są:</span><span class="sxs-lookup"><span data-stu-id="86fac-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="86fac-107">Aplikacja jest już uruchomiona i korzystania z jego plików.</span><span class="sxs-lookup"><span data-stu-id="86fac-107">The application is already running and using its files.</span></span> <span data-ttu-id="86fac-108">Aby rozwiązać ten problem, upewnij się, że aplikacja nie jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="86fac-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="86fac-109">Plik został otwarty w innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86fac-109">Another application has opened the file.</span></span> <span data-ttu-id="86fac-110">Aby rozwiązać ten problem, upewnij się, że żadna inna aplikacja uzyskuje dostęp do plików.</span><span class="sxs-lookup"><span data-stu-id="86fac-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="86fac-111">Nie jest zawsze oczywiste, która aplikacja uzyskuje dostęp do plików. w takim przypadku ponowne uruchomienie komputera może być Najprostszym sposobem, aby zakończyć tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="86fac-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="86fac-112">Jeśli nawet jednego z plików wyjściowych projektu jest oznaczona jako tylko do odczytu, to zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="86fac-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="86fac-113">**Identyfikator błędu:** BC31019</span><span class="sxs-lookup"><span data-stu-id="86fac-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86fac-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="86fac-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="86fac-115">Skompiluj program, aby zobaczyć, jeśli ten błąd wystąpi ponownie.</span><span class="sxs-lookup"><span data-stu-id="86fac-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="86fac-116">Jeśli błąd będzie się powtarzał, Zapisz swoją pracę i ponownie uruchom [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="86fac-116">If the error continues, save your work and restart [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
3.  <span data-ttu-id="86fac-117">Jeśli błąd będzie nadal występował, uruchom ponownie komputer.</span><span class="sxs-lookup"><span data-stu-id="86fac-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="86fac-118">Jeśli błąd będzie się powtarzał, zainstaluj ponownie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86fac-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="86fac-119">Jeśli błąd będzie nadal występować po ponownej instalacji, powiadamia pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86fac-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="86fac-120">Aby sprawdzić atrybutów plików w Eksploratorze plików</span><span class="sxs-lookup"><span data-stu-id="86fac-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="86fac-121">Otwórz folder, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="86fac-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="86fac-122">Kliknij przycisk **widoków** ikonę i wybierz polecenie **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="86fac-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="86fac-123">Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybierz pozycję **atrybuty** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="86fac-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="86fac-124">Do zmiany atrybutów pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="86fac-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="86fac-125">W **Eksploratora plików**, kliknij prawym przyciskiem myszy plik lub folder i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="86fac-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="86fac-126">W **atrybuty** sekcji **ogólne** kartę, wyczyść **tylko do odczytu** pole.</span><span class="sxs-lookup"><span data-stu-id="86fac-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="86fac-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="86fac-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86fac-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86fac-128">See Also</span></span>  
 [<span data-ttu-id="86fac-129">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="86fac-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
