---
title: 'Porady: znajdowanie podkatalogów z określonym wzorcem'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348774"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="1c64a-102">Porady: znajdowanie podkatalogów z określonym wzorcem w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c64a-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="1c64a-103">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> zwraca kolekcję ciągów reprezentujących nazwy ścieżek dla podkatalogów w katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c64a-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="1c64a-104">Aby określić konkretny wzorzec, można użyć parametru `wildCards`.</span><span class="sxs-lookup"><span data-stu-id="1c64a-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="1c64a-105">Jeśli chcesz uwzględnić zawartość podkatalogów w wyszukiwaniu, ustaw parametr `searchType` na `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="1c64a-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="1c64a-106">Po znalezieniu katalogów pasujących do określonego wzorca zwracana jest pusta kolekcja.</span><span class="sxs-lookup"><span data-stu-id="1c64a-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="1c64a-107">Aby znaleźć podkatalogi z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="1c64a-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="1c64a-108">Użyj metody `GetDirectories`, podając nazwę i ścieżkę do katalogu, który chcesz przeszukać.</span><span class="sxs-lookup"><span data-stu-id="1c64a-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="1c64a-109">Poniższy przykład zwraca wszystkie katalogi w strukturze katalogów, które zawierają wyraz "Logs" w nazwie i dodaje je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="1c64a-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="1c64a-110">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="1c64a-110">Robust Programming</span></span>

<span data-ttu-id="1c64a-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="1c64a-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="1c64a-112">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="1c64a-113">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="1c64a-114">Co najmniej jeden z określonych symboli wieloznacznych jest `Nothing`, pusty ciąg lub zawiera tylko spacje (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="1c64a-115">`directory` nie istnieje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="1c64a-116">`directory` wskazuje istniejący plik (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="1c64a-117">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="1c64a-118">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="1c64a-119">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="1c64a-120">Użytkownik nie ma wymaganych uprawnień (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="1c64a-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c64a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c64a-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="1c64a-122">Instrukcje: znajdowanie plików z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="1c64a-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
