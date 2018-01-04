---
title: "Funkcja SaveToHistory (WPF niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: SaveToHistory
api_location: PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af5294aad43b28bc590dd84466e133553f0ee47b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="734c6-102">Funkcja SaveToHistory (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="734c6-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="734c6-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="734c6-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="734c6-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.</span><span class="sxs-lookup"><span data-stu-id="734c6-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="734c6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="734c6-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="734c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="734c6-106">Parameters</span></span>  
 <span data-ttu-id="734c6-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="734c6-107">pHistoryStream</span></span>  
 <span data-ttu-id="734c6-108">Wskaźnik do strumienia historii.</span><span class="sxs-lookup"><span data-stu-id="734c6-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="734c6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="734c6-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="734c6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="734c6-110">Requirements</span></span>  
 <span data-ttu-id="734c6-111">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="734c6-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="734c6-112">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="734c6-112">**DLL:**</span></span>  
  
 <span data-ttu-id="734c6-113">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="734c6-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="734c6-114">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="734c6-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="734c6-115">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="734c6-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734c6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="734c6-116">See Also</span></span>  
 [<span data-ttu-id="734c6-117">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="734c6-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
