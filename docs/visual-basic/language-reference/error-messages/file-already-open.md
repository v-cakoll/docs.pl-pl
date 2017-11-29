---
title: "Plik jest już otwarty"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="612e8-102">Plik jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="612e8-102">File already open</span></span>
<span data-ttu-id="612e8-103">Czasami pliku muszą zostać zamknięte przed inne `FileOpen` lub można wykonać innych operacji.</span><span class="sxs-lookup"><span data-stu-id="612e8-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="612e8-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="612e8-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="612e8-105">Tryb sekwencyjnych dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty</span><span class="sxs-lookup"><span data-stu-id="612e8-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="612e8-106">Oświadczenie odnosi się do otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="612e8-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="612e8-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="612e8-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="612e8-108">Zamknij plik przed wykonaniem instrukcji.</span><span class="sxs-lookup"><span data-stu-id="612e8-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612e8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="612e8-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
