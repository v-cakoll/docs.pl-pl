---
title: ForwardTranslateAccelerator, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 4bb7e665bb836dc5f95b14f39179f1d4b9f8173d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080257"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="a0e16-102">ForwardTranslateAccelerator, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="a0e16-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="a0e16-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a0e16-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="a0e16-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.</span><span class="sxs-lookup"><span data-stu-id="a0e16-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e16-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0e16-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0e16-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0e16-106">Parameters</span></span>  
 <span data-ttu-id="a0e16-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="a0e16-107">pMsg</span></span>  
 <span data-ttu-id="a0e16-108">Wskaźnik do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a0e16-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="a0e16-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="a0e16-109">appUnhandled</span></span>  
 <span data-ttu-id="a0e16-110">`true` gdy aplikacja został już podany Państwo, by obsłużyć komunikat wejściowy, ale nie został obsłużony w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a0e16-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e16-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0e16-111">Requirements</span></span>  
 <span data-ttu-id="a0e16-112">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e16-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e16-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="a0e16-113">**DLL:**</span></span>  
  
 <span data-ttu-id="a0e16-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="a0e16-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="a0e16-115">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="a0e16-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="a0e16-116">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e16-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e16-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0e16-117">See also</span></span>

- [<span data-ttu-id="a0e16-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="a0e16-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
