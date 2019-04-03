---
title: 'Nie można zapisać do pliku wyjściowego „<filename>”: <error>'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 61ba4dbc668f7b236b0631f797feb4e81068e517
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827201"
---
# <a name="unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="9035a-102">Nie można zapisać do pliku wyjściowego "\<nazwa pliku >": \<błąd ></span><span class="sxs-lookup"><span data-stu-id="9035a-102">Unable to write to output file '\<filename>': \<error></span></span>
<span data-ttu-id="9035a-103">Wystąpił problem podczas tworzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="9035a-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="9035a-104">Nie można otworzyć pliku wyjściowego do zapisu.</span><span class="sxs-lookup"><span data-stu-id="9035a-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="9035a-105">Plik (lub folder zawierający plik) może być otwarty do wyłącznego użytku przez inny proces lub może być jej ustawiony atrybut tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9035a-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="9035a-106">Typowe sytuacje, gdy plik jest otwarty w trybie wyłączności są następujące:</span><span class="sxs-lookup"><span data-stu-id="9035a-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="9035a-107">Aplikacja jest już uruchomiona i korzystania z jego plików.</span><span class="sxs-lookup"><span data-stu-id="9035a-107">The application is already running and using its files.</span></span> <span data-ttu-id="9035a-108">Aby rozwiązać ten problem, upewnij się, że aplikacja nie jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="9035a-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="9035a-109">Plik został otwarty w innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9035a-109">Another application has opened the file.</span></span> <span data-ttu-id="9035a-110">Aby rozwiązać ten problem, upewnij się, że żadna inna aplikacja uzyskuje dostęp do plików.</span><span class="sxs-lookup"><span data-stu-id="9035a-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="9035a-111">Nie zawsze jest oczywiste która aplikacja uzyskuje dostęp do plików. w takim przypadku ponowne uruchomienie komputera może być Najprostszym sposobem, aby zakończyć tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="9035a-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="9035a-112">Jeśli jeszcze jeden z plików wyjściowych projektu jest oznaczony jako tylko do odczytu, ten wyjątek zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="9035a-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="9035a-113">**Identyfikator błędu:** BC31019</span><span class="sxs-lookup"><span data-stu-id="9035a-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9035a-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9035a-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="9035a-115">Skompiluj program ponownie, aby zobaczyć, jeśli błąd będzie się powtarzać.</span><span class="sxs-lookup"><span data-stu-id="9035a-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="9035a-116">Jeśli błąd będzie się powtarzał, Zapisz swoją pracę i uruchom ponownie program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9035a-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="9035a-117">Jeśli błąd będzie się powtarzać, uruchom ponownie komputer.</span><span class="sxs-lookup"><span data-stu-id="9035a-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="9035a-118">Jeśli ten błąd wystąpi, zainstaluj ponownie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9035a-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="9035a-119">Jeśli ten błąd będzie występował po ponownej instalacji, powiadom pomoc techniczna firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9035a-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="9035a-120">Aby sprawdzić atrybutów plików w Eksploratorze plików</span><span class="sxs-lookup"><span data-stu-id="9035a-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="9035a-121">Otwórz folder, który Cię interesuje.</span><span class="sxs-lookup"><span data-stu-id="9035a-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="9035a-122">Kliknij przycisk **widoków** ikonę i wybierz polecenie **szczegóły**.</span><span class="sxs-lookup"><span data-stu-id="9035a-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="9035a-123">Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybierz **atrybuty** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="9035a-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="9035a-124">Do zmiany atrybutów pliku lub folderu</span><span class="sxs-lookup"><span data-stu-id="9035a-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="9035a-125">W **Eksploratora plików**, kliknij prawym przyciskiem myszy plik lub folder i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9035a-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="9035a-126">W **atrybuty** części **ogólne** kartę, usuń zaznaczenie **tylko do odczytu** pole.</span><span class="sxs-lookup"><span data-stu-id="9035a-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="9035a-127">Naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="9035a-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9035a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9035a-128">See also</span></span>

- [<span data-ttu-id="9035a-129">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="9035a-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
