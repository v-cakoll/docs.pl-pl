---
title: Funkcja CreateIDispatchSTAForwarder — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738032"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="fc265-102">CreateIDispatchSTAForwarder — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)</span><span class="sxs-lookup"><span data-stu-id="fc265-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="fc265-103">Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fc265-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="fc265-104">Używany przez infrastrukturę Windows Presentation Foundation (WPF) dla wątków i zarządzania systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="fc265-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc265-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc265-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc265-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc265-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fc265-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="fc265-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="fc265-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="fc265-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="fc265-109">Wskaźnik do interfejsu `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="fc265-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="fc265-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="fc265-110">ppForwarder</span></span>  
 <span data-ttu-id="fc265-111">Wskaźnik do adresu interfejsu `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="fc265-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc265-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc265-112">Requirements</span></span>  
 <span data-ttu-id="fc265-113">**Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc265-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc265-114">**BIBLIOTECE**</span><span class="sxs-lookup"><span data-stu-id="fc265-114">**DLL:**</span></span>  
  
 <span data-ttu-id="fc265-115">W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="fc265-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="fc265-116">W .NET Framework 4 i nowszych: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="fc265-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="fc265-117">**Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc265-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc265-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc265-118">See also</span></span>

- [<span data-ttu-id="fc265-119">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="fc265-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
