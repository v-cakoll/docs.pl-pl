---
title: "Format schowka nie jest prawidłowy"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="38c08-102">Format schowka nie jest prawidłowy</span><span class="sxs-lookup"><span data-stu-id="38c08-102">Clipboard format is not valid</span></span>
<span data-ttu-id="38c08-103">Określony format Schowka jest niezgodna z wykonywanej metody.</span><span class="sxs-lookup"><span data-stu-id="38c08-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="38c08-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="38c08-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="38c08-105">Korzystanie ze Schowka `GetText` lub `SetText` metody przy użyciu formatu Schowka innych niż `vbCFText` lub `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="38c08-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="38c08-106">Korzystanie ze Schowka `GetData` lub `SetData` metody przy użyciu formatu Schowka innych niż `vbCFBitmap`, `vbCFDIB`, lub `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="38c08-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="38c08-107">Przy użyciu `DataObject``GetData` metody lub `SetData` metody przy użyciu formatu Schowka w zakresie zarezerwowane przez Microsoft Windows dla zarejestrowanego formatów (& HC000 - & HFFFF), podczas tego formatu Schowka nie został zarejestrowany w usłudze Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="38c08-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38c08-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="38c08-108">To correct this error</span></span>  
  
-   <span data-ttu-id="38c08-109">Usuń nieprawidłowy format i określ prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="38c08-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c08-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38c08-110">See Also</span></span>  
 [<span data-ttu-id="38c08-111">Schowek: Dodawanie innych formatów</span><span class="sxs-lookup"><span data-stu-id="38c08-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
