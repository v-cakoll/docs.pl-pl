---
title: "Za dużo plików"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 506f0735956267d51b575cd26b628605e9db38cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-files"></a><span data-ttu-id="93de6-102">Za dużo plików</span><span class="sxs-lookup"><span data-stu-id="93de6-102">Too many files</span></span>
<span data-ttu-id="93de6-103">Utworzono większej liczby plików w katalogu głównym niż zezwala systemu operacyjnego albo otwarte pliki więcej niż liczba określona w **pliki =** ustawienia w pliku CONFIG. Plik SYS.</span><span class="sxs-lookup"><span data-stu-id="93de6-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93de6-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="93de6-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="93de6-105">Jeśli program jest otwieranie, zamykanie lub zapisywanie plików w katalogu głównym, należy zmienić programu korzystającą z podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="93de6-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2.  <span data-ttu-id="93de6-106">Zwiększ liczbę plików określonych w Twojej **pliki =** ustawienia w pliku CONFIG. SYS pliku i uruchom ponownie komputer.</span><span class="sxs-lookup"><span data-stu-id="93de6-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93de6-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93de6-107">See Also</span></span>  
 [<span data-ttu-id="93de6-108">Error — typy</span><span class="sxs-lookup"><span data-stu-id="93de6-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
