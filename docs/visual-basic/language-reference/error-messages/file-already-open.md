---
title: Plik jest już otwarty
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 75a08b411a4afd7ea8e11953f1d465b082faa712
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="file-already-open"></a><span data-ttu-id="65f42-102">Plik jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="65f42-102">File already open</span></span>
<span data-ttu-id="65f42-103">Czasami pliku muszą zostać zamknięte przed inne `FileOpen` lub można wykonać innych operacji.</span><span class="sxs-lookup"><span data-stu-id="65f42-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="65f42-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="65f42-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="65f42-105">Tryb sekwencyjnych dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="65f42-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="65f42-106">Oświadczenie odnosi się do otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="65f42-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65f42-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="65f42-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="65f42-108">Zamknij plik przed wykonaniem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="65f42-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f42-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65f42-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
