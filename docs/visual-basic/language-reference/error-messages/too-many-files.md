---
title: Za dużo plików
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 1d7fc769a0a2d0f8474c0a72a5600b84c8396201
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310060"
---
# <a name="too-many-files"></a><span data-ttu-id="4b3de-102">Za dużo plików</span><span class="sxs-lookup"><span data-stu-id="4b3de-102">Too many files</span></span>
<span data-ttu-id="4b3de-103">Im więcej plików zostały utworzone w katalogu głównym niż zezwala systemu operacyjnego lub więcej plików zostały otwarte niż liczba określona w **plików =** ustawienia w pliku CONFIG. SYS plik.</span><span class="sxs-lookup"><span data-stu-id="4b3de-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4b3de-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4b3de-104">To correct this error</span></span>  
  
1. <span data-ttu-id="4b3de-105">Jeśli program jest otwarcie, zamykanie lub zapisywanie plików w katalogu głównym, zmienić programu, korzystającą z podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="4b3de-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="4b3de-106">Zwiększ liczbę plików określonych w swojej **plików =** ustawienia w pliku CONFIG. SYS plik, a następnie ponownie uruchom komputer.</span><span class="sxs-lookup"><span data-stu-id="4b3de-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3de-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b3de-107">See also</span></span>

- [<span data-ttu-id="4b3de-108">Error — Typy</span><span class="sxs-lookup"><span data-stu-id="4b3de-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
