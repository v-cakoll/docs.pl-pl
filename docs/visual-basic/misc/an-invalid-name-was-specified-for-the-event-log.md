---
title: Określono nieprawidłową nazwę dziennika zdarzeń
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940676"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="b400b-102">Określono nieprawidłową nazwę dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b400b-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="b400b-103">Nieprawidłowa nazwa została określona dla dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b400b-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="b400b-104">Zazwyczaj jest to wynik nieprawidłowe znaki w nazwę, nazwę pustego pliku lub nazwę pliku, który jest za długi.</span><span class="sxs-lookup"><span data-stu-id="b400b-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b400b-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b400b-105">To correct this error</span></span>  
  
- <span data-ttu-id="b400b-106">Jeśli określona nazwa jest więcej niż 8 znaków, upewnij się, że nie występuje konflikt z nazwami innych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b400b-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="b400b-107">Pierwsze osiem znaków są oceniane podczas ustalania, czy nazwa jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="b400b-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="b400b-108">Jeśli dostarczenie ścieżki, upewnij się, że jest analizowany poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b400b-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="b400b-109">Sprawdź, czy istnieją nie nieprawidłowe znaki w nazwie.</span><span class="sxs-lookup"><span data-stu-id="b400b-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="b400b-110">Znaki, których nie można używać w nazwie pliku obejmują `<`, `>`, `:`, `"`, `/`, `\`, i `|`.</span><span class="sxs-lookup"><span data-stu-id="b400b-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b400b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b400b-111">See also</span></span>

- [<span data-ttu-id="b400b-112">Instrukcje: Analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="b400b-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="b400b-113">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="b400b-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
