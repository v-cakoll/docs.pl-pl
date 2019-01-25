---
title: Określono nieprawidłową nazwę dziennika zdarzeń
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 242c5394011fd018a03f81b9b56bcfd7015682dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604404"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="b3018-102">Określono nieprawidłową nazwę dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b3018-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="b3018-103">Nieprawidłowa nazwa została określona dla dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3018-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="b3018-104">Zazwyczaj jest to wynik nieprawidłowe znaki w nazwę, nazwę pustego pliku lub nazwę pliku, który jest za długi.</span><span class="sxs-lookup"><span data-stu-id="b3018-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3018-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b3018-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b3018-106">Jeśli określona nazwa jest więcej niż 8 znaków, upewnij się, że nie występuje konflikt z nazwami innych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3018-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="b3018-107">Pierwsze osiem znaków są oceniane podczas ustalania, czy nazwa jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="b3018-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="b3018-108">Jeśli dostarczenie ścieżki, upewnij się, że jest analizowany poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b3018-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="b3018-109">Sprawdź, czy istnieją nie nieprawidłowe znaki w nazwie.</span><span class="sxs-lookup"><span data-stu-id="b3018-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="b3018-110">Znaki, których nie można używać w nazwie pliku obejmują `<`, `>`, `:`, `"`, `/`, `\`, i `|`.</span><span class="sxs-lookup"><span data-stu-id="b3018-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3018-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3018-111">See also</span></span>
- [<span data-ttu-id="b3018-112">Instrukcje: Analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="b3018-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="b3018-113">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="b3018-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)

