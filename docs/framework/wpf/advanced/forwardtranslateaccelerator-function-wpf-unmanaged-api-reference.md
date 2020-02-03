---
title: Funkcja ForwardTranslateAccelerator — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747035"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="dcdac-102">ForwardTranslateAccelerator — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)</span><span class="sxs-lookup"><span data-stu-id="dcdac-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="dcdac-103">Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="dcdac-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="dcdac-104">Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="dcdac-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcdac-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcdac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcdac-106">Parameters</span></span>  
 <span data-ttu-id="dcdac-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="dcdac-107">pMsg</span></span>  
 <span data-ttu-id="dcdac-108">Wskaźnik do komunikatu.</span><span class="sxs-lookup"><span data-stu-id="dcdac-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="dcdac-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="dcdac-109">appUnhandled</span></span>  
 <span data-ttu-id="dcdac-110">`true`, gdy aplikacja uzyskała już szansę obsługi wiadomości wejściowej, ale jej nie została obsłużona; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="dcdac-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcdac-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcdac-111">Requirements</span></span>  
 <span data-ttu-id="dcdac-112">**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdac-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdac-113">**BIBLIOTECE**</span><span class="sxs-lookup"><span data-stu-id="dcdac-113">**DLL:**</span></span>  
  
 <span data-ttu-id="dcdac-114">W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="dcdac-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="dcdac-115">W .NET Framework 4 i nowszych: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="dcdac-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="dcdac-116">**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdac-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdac-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcdac-117">See also</span></span>

- [<span data-ttu-id="dcdac-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="dcdac-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
