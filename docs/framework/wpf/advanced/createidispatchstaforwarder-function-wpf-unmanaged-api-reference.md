---
title: CreateIDispatchSTAForwarder, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 215f6ff727b814e7e7d7c708c29a8c5221f5797f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575989"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b1f9b-102">CreateIDispatchSTAForwarder, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="b1f9b-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b1f9b-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b1f9b-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b1f9b-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania wątku i systemu windows.</span><span class="sxs-lookup"><span data-stu-id="b1f9b-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f9b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1f9b-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1f9b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1f9b-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b1f9b-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="b1f9b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b1f9b-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="b1f9b-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="b1f9b-109">Wskaźnik do `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b1f9b-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="b1f9b-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="b1f9b-110">ppForwarder</span></span>  
 <span data-ttu-id="b1f9b-111">Wskaźnik na adres `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b1f9b-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1f9b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1f9b-112">Requirements</span></span>  
 <span data-ttu-id="b1f9b-113">**Platformy:** Zobacz [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1f9b-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f9b-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="b1f9b-114">**DLL:**</span></span>  
  
 <span data-ttu-id="b1f9b-115">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b1f9b-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b1f9b-116">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b1f9b-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b1f9b-117">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f9b-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f9b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1f9b-118">See also</span></span>
- [<span data-ttu-id="b1f9b-119">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="b1f9b-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
