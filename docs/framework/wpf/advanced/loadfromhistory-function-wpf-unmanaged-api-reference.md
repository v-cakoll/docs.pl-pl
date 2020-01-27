---
title: Funkcja LoadFromHistory — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727928"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="61b1f-102">LoadFromHistory — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)</span><span class="sxs-lookup"><span data-stu-id="61b1f-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="61b1f-103">Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="61b1f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="61b1f-104">Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="61b1f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b1f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61b1f-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="61b1f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="61b1f-106">Parameters</span></span>  
 <span data-ttu-id="61b1f-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="61b1f-107">pHistoryStream</span></span>  
 <span data-ttu-id="61b1f-108">Wskaźnik do strumienia informacji o historii.</span><span class="sxs-lookup"><span data-stu-id="61b1f-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="61b1f-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="61b1f-109">pBindCtx</span></span>  
 <span data-ttu-id="61b1f-110">Wskaźnik do kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="61b1f-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61b1f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61b1f-111">Requirements</span></span>  
 <span data-ttu-id="61b1f-112">**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61b1f-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b1f-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="61b1f-113">**DLL:**</span></span>  
  
 <span data-ttu-id="61b1f-114">W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="61b1f-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="61b1f-115">W .NET Framework 4 i nowszych: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="61b1f-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="61b1f-116">**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61b1f-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b1f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61b1f-117">See also</span></span>

- [<span data-ttu-id="61b1f-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="61b1f-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
