---
title: "Próba zapisu poza końcem pliku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="c0e43-102">Próba zapisu poza końcem pliku</span><span class="sxs-lookup"><span data-stu-id="c0e43-102">Input past end of file</span></span>
<span data-ttu-id="c0e43-103">Albo `Input` instrukcji jest odczytu z pliku, który jest pusty lub jeden w którym wszystkie dane są używane, lub użyto `EOF` funkcji przy użyciu pliku otwarte dostęp do danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="c0e43-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c0e43-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c0e43-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="c0e43-105">Użyj `EOF` funkcji bezpośrednio przed `Input` instrukcji, aby wykryć koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="c0e43-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2.  <span data-ttu-id="c0e43-106">Jeśli plik jest otwarty, aby uzyskać dostęp do danych binarnych, użyj `Seek` i `Loc`.</span><span class="sxs-lookup"><span data-stu-id="c0e43-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e43-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0e43-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
