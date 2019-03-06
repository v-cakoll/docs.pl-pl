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
ms.openlocfilehash: c4da322bf779e084f12529d0da6949ef6ada5cf3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379656"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ef974-102">CreateIDispatchSTAForwarder, funkcja (niezarządzany wykaz interfejsów API WPF.)</span><span class="sxs-lookup"><span data-stu-id="ef974-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="ef974-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ef974-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="ef974-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania wątku i systemu windows.</span><span class="sxs-lookup"><span data-stu-id="ef974-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef974-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef974-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef974-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef974-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ef974-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="ef974-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="ef974-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="ef974-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="ef974-109">Wskaźnik do `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ef974-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="ef974-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="ef974-110">ppForwarder</span></span>  
 <span data-ttu-id="ef974-111">Wskaźnik na adres `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ef974-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef974-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef974-112">Requirements</span></span>  
 <span data-ttu-id="ef974-113">**Platformy:** Zobacz [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef974-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef974-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="ef974-114">**DLL:**</span></span>  
  
 <span data-ttu-id="ef974-115">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="ef974-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="ef974-116">W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="ef974-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="ef974-117">**Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef974-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef974-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef974-118">See also</span></span>
- [<span data-ttu-id="ef974-119">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="ef974-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
