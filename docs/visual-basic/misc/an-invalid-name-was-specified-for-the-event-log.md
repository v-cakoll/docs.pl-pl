---
title: Określono nieprawidłową nazwę dziennika zdarzeń
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412926"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="54dd6-102">Określono nieprawidłową nazwę dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="54dd6-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="54dd6-103">Określono nieprawidłową nazwę dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54dd6-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="54dd6-104">Zwykle jest to wynik nieprawidłowych znaków w nazwie, pustej nazwie pliku lub nazwy pliku, która jest zbyt długa.</span><span class="sxs-lookup"><span data-stu-id="54dd6-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54dd6-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="54dd6-105">To correct this error</span></span>  
  
- <span data-ttu-id="54dd6-106">Jeśli określona nazwa jest dłuższa niż osiem znaków, upewnij się, że nie występują konflikty z nazwami innych dzienników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54dd6-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="54dd6-107">Podczas ustalania, czy nazwa jest unikatowa, oceniane są tylko pierwsze osiem znaków.</span><span class="sxs-lookup"><span data-stu-id="54dd6-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="54dd6-108">W przypadku podawania ścieżki upewnij się, że została ona prawidłowo przeanalizowana.</span><span class="sxs-lookup"><span data-stu-id="54dd6-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="54dd6-109">Sprawdź, czy nazwa nie zawiera nieprawidłowych znaków.</span><span class="sxs-lookup"><span data-stu-id="54dd6-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="54dd6-110">Znaki, których nie można użyć w nazwie pliku, obejmują,,,,, `<` `>` `:` `"` `/` `\` i `|` .</span><span class="sxs-lookup"><span data-stu-id="54dd6-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54dd6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54dd6-111">See also</span></span>

- [<span data-ttu-id="54dd6-112">Instrukcje: Analizowanie ścieżek plików</span><span class="sxs-lookup"><span data-stu-id="54dd6-112">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="54dd6-113">Instrukcje: Zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="54dd6-113">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
