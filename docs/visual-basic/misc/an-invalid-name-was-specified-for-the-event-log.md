---
title: "Określono nieprawidłową nazwę dziennika zdarzeń"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fc5a2e93541063a129efaa0ce08fc19a98372126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="b613e-102">Określono nieprawidłową nazwę dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b613e-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="b613e-103">Określono nieprawidłową nazwę dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b613e-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="b613e-104">Zazwyczaj jest to wynik nieprawidłowych znaków w nazwa, Nazwa pustego pliku lub nazwę pliku, który jest zbyt długi.</span><span class="sxs-lookup"><span data-stu-id="b613e-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b613e-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b613e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b613e-106">Jeśli określona nazwa jest więcej niż osiem znaków, upewnij się, że nie występuje konflikt z nazwami innych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b613e-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="b613e-107">Tylko pierwszych osiem znaków są oceniane podczas ustalania, czy nazwa jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="b613e-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="b613e-108">Jeśli podając ścieżkę, upewnij się, że jest poprawnie przeanalizować.</span><span class="sxs-lookup"><span data-stu-id="b613e-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="b613e-109">Sprawdź, czy nie są nieprawidłowe znaki w nazwie.</span><span class="sxs-lookup"><span data-stu-id="b613e-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="b613e-110">Znaki, których nie można użyć w nazwie pliku to `<`, `>`, `:`, `"`, `/`, `\`, i `|`.</span><span class="sxs-lookup"><span data-stu-id="b613e-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b613e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b613e-111">See Also</span></span>  
 [<span data-ttu-id="b613e-112">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="b613e-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="b613e-113">Porady: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="b613e-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="b613e-114">Porady: tworzenie i usuwanie dzienników zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b613e-114">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
