---
title: "Błąd ładowania biblioteki DLL (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="ab9ba-102">Błąd ładowania biblioteki DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab9ba-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="ab9ba-103">Biblioteki dołączanej (dynamicznie DLL) jest określona w bibliotece `Lib` klauzuli `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="ab9ba-104">Możliwe przyczyny tego błędu to:</span><span class="sxs-lookup"><span data-stu-id="ab9ba-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="ab9ba-105">Plik nie jest wykonywalne biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="ab9ba-106">Plik nie jest biblioteką DLL systemu Windows firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="ab9ba-107">Plik DLL, który odwołuje się do innej bibliotece DLL, która nie występuje.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="ab9ba-108">Biblioteki DLL lub pliku nie jest określona w ścieżce katalogu.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab9ba-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ab9ba-109">To correct this error</span></span>  
  
-   <span data-ttu-id="ab9ba-110">Jeśli plik znajduje się plik tekst źródłowy i dlatego nie plik wykonywalny biblioteki DLL, musi być skompilowany i połączony z formularzem plik wykonywalny biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="ab9ba-111">Jeśli plik nie jest biblioteką DLL systemu Windows firmy Microsoft, należy uzyskać równoważne Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="ab9ba-112">Jeśli plik DLL, który odwołuje się do innej bibliotece DLL, która nie jest obecny, Uzyskaj przywoływanego biblioteki DLL i udostępni go.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="ab9ba-113">Jeśli plik DLL lub pliku nie jest określony przez ścieżkę katalogu, należy przenieść biblioteki DLL do katalogu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="ab9ba-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9ba-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab9ba-114">See Also</span></span>  
 [<span data-ttu-id="ab9ba-115">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ab9ba-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
