---
title: ForwardTranslateAccelerator, funkcja — odwołanie do niezarządzanego interfejsu API WPF WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186629"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="1f349-102">ForwardTranslateAccelerator, funkcja (odwołanie do interfejsu API niezarządzanego WPF)</span><span class="sxs-lookup"><span data-stu-id="1f349-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="1f349-103">Ten interfejs API obsługuje infrastrukturę Programu Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio z kodu.</span><span class="sxs-lookup"><span data-stu-id="1f349-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="1f349-104">Używane przez Windows Presentation Foundation (WPF) infrastruktury do zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="1f349-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f349-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f349-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f349-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f349-106">Parameters</span></span>  
 <span data-ttu-id="1f349-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="1f349-107">pMsg</span></span>  
 <span data-ttu-id="1f349-108">Wskaźnik do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1f349-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="1f349-109">appNieręczny</span><span class="sxs-lookup"><span data-stu-id="1f349-109">appUnhandled</span></span>  
 <span data-ttu-id="1f349-110">`true`gdy aplikacja ma już szansę obsłużyć komunikat wejściowy, ale nie obsługuje go; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="1f349-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f349-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f349-111">Requirements</span></span>  
 <span data-ttu-id="1f349-112">**Platformy:** Zobacz [.NET Framework Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f349-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f349-113">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="1f349-113">**DLL:**</span></span>  
  
 <span data-ttu-id="1f349-114">W pliku .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="1f349-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="1f349-115">W pliku .NET Framework 4 i nowszym: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="1f349-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="1f349-116">**Wersja programu .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f349-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f349-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f349-117">See also</span></span>

- [<span data-ttu-id="1f349-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="1f349-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
