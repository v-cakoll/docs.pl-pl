---
title: Format schowka nie jest prawidłowy
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 0a5d06b381df3af8de1d092b600239c9acfce39a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735782"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="88935-102">Format schowka nie jest prawidłowy</span><span class="sxs-lookup"><span data-stu-id="88935-102">Clipboard format is not valid</span></span>
<span data-ttu-id="88935-103">Określony format Schowka jest niezgodna z wykonywanej metody.</span><span class="sxs-lookup"><span data-stu-id="88935-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="88935-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="88935-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="88935-105">Korzystanie ze Schowka `GetText` lub `SetText` metody z formatu Schowka w innych niż `vbCFText` lub `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="88935-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="88935-106">Korzystanie ze Schowka `GetData` lub `SetData` metody z formatu Schowka w innych niż `vbCFBitmap`, `vbCFDIB`, lub `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="88935-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="88935-107">Za pomocą `GetData` lub `SetData` metody `DataObject` za pomocą formatu Schowka w zakresie zarezerwowane przez program Microsoft Windows dla zarejestrowanego formatów (& HC000 - & HFFFF), gdy ten format schowka nie został zarejestrowany za pomocą programu Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="88935-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88935-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="88935-108">To correct this error</span></span>  
  
-   <span data-ttu-id="88935-109">Usuń nieprawidłowy format i określ prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="88935-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88935-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88935-110">See also</span></span>
- [<span data-ttu-id="88935-111">Schowek: Dodawanie innych formatów</span><span class="sxs-lookup"><span data-stu-id="88935-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
