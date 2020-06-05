---
title: Za dużo plików
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 38d39ad20f350137d714ae5d09db5d2204b83621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362803"
---
# <a name="too-many-files"></a><span data-ttu-id="c6b27-102">Za dużo plików</span><span class="sxs-lookup"><span data-stu-id="c6b27-102">Too many files</span></span>
<span data-ttu-id="c6b27-103">Więcej plików został utworzony w katalogu głównym niż zezwala na system operacyjny, lub więcej plików został otwarty niż liczba określona w ustawieniu **pliki =** w konfiguracji. Plik SYS.</span><span class="sxs-lookup"><span data-stu-id="c6b27-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6b27-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c6b27-104">To correct this error</span></span>  
  
1. <span data-ttu-id="c6b27-105">Jeśli program otwiera, zamyka lub zapisuje pliki w katalogu głównym, należy zmienić program tak, aby korzystał z podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="c6b27-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="c6b27-106">Zwiększ liczbę plików określoną w ustawieniu **pliki =** w konfiguracji. Plik SYS i uruchom ponownie komputer.</span><span class="sxs-lookup"><span data-stu-id="c6b27-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b27-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6b27-107">See also</span></span>

- [<span data-ttu-id="c6b27-108">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="c6b27-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
