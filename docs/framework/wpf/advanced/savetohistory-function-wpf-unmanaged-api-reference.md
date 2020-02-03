---
title: Funkcja SaveToHistory — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731753"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f80da-102">SaveToHistory — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)</span><span class="sxs-lookup"><span data-stu-id="f80da-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f80da-103">Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f80da-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f80da-104">Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="f80da-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f80da-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f80da-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="f80da-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f80da-106">Parameters</span></span>  
 <span data-ttu-id="f80da-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="f80da-107">pHistoryStream</span></span>  
 <span data-ttu-id="f80da-108">Wskaźnik do strumienia historii.</span><span class="sxs-lookup"><span data-stu-id="f80da-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f80da-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f80da-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f80da-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f80da-110">Requirements</span></span>  
 <span data-ttu-id="f80da-111">**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f80da-111">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f80da-112">**BIBLIOTECE**</span><span class="sxs-lookup"><span data-stu-id="f80da-112">**DLL:**</span></span>  
  
 <span data-ttu-id="f80da-113">W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="f80da-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f80da-114">W .NET Framework 4 i nowszych: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="f80da-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f80da-115">**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f80da-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80da-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f80da-116">See also</span></span>

- [<span data-ttu-id="f80da-117">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="f80da-117">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
