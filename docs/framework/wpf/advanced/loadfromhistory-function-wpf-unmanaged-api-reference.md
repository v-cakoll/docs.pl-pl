---
title: Funkcja LoadFromHistory (WPF niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 19674b45af84e1e6a6ca169f7b6654c6e3847416
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="4403e-102">Funkcja LoadFromHistory (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="4403e-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="4403e-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4403e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="4403e-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.</span><span class="sxs-lookup"><span data-stu-id="4403e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4403e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4403e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4403e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4403e-106">Parameters</span></span>  
 <span data-ttu-id="4403e-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="4403e-107">pHistoryStream</span></span>  
 <span data-ttu-id="4403e-108">Wskaźnik do strumienia informacji historii.</span><span class="sxs-lookup"><span data-stu-id="4403e-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="4403e-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="4403e-109">pBindCtx</span></span>  
 <span data-ttu-id="4403e-110">Wskaźnik do kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="4403e-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4403e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4403e-111">Requirements</span></span>  
 <span data-ttu-id="4403e-112">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4403e-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4403e-113">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="4403e-113">**DLL:**</span></span>  
  
 <span data-ttu-id="4403e-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="4403e-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="4403e-115">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="4403e-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="4403e-116">**.NET framework w wersji:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4403e-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4403e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4403e-117">See Also</span></span>  
 [<span data-ttu-id="4403e-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="4403e-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
