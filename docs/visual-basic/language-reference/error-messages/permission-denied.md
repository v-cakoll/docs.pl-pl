---
title: "Odmowa uprawnień (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5d7965ebd42cb3e56d66966d035be9ba3d3957c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="1f67c-102">Odmowa uprawnień (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f67c-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="1f67c-103">Nastąpiła próba zapisu na dysku przed zapisem lub uzyskać dostępu do zablokowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="1f67c-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1f67c-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1f67c-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="1f67c-105">Aby otworzyć plik zabezpieczony przed zapisem, zmienić atrybutu zabezpieczenie przed zapisem pliku.</span><span class="sxs-lookup"><span data-stu-id="1f67c-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="1f67c-106">Upewnij się, że inny proces nie został zablokowany w pliku i poczekaj, aby otworzyć plik, dopóki zwolnieniem innego procesu.</span><span class="sxs-lookup"><span data-stu-id="1f67c-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="1f67c-107">Dostępu do rejestru, sprawdź, czy uprawnienia użytkownika i zawierać tego rodzaju dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="1f67c-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f67c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f67c-108">See Also</span></span>  
 [<span data-ttu-id="1f67c-109">Error — typy</span><span class="sxs-lookup"><span data-stu-id="1f67c-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
