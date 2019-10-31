---
title: IAssemblyEnum::GetNextAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134433"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="ebd4a-102">IAssemblyEnum::GetNextAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebd4a-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="ebd4a-103">Pobiera wskaźnik do następnego [IAssemblyName](iassemblyname-interface.md) zawartego w tym obiekcie [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ebd4a-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebd4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebd4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebd4a-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="ebd4a-106">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ebd4a-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ebd4a-107">`pvReserved` musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="ebd4a-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ebd4a-108">określoną Zwrócony wskaźnik `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="ebd4a-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ebd4a-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ebd4a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ebd4a-110">`dwFlags` musi mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="ebd4a-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd4a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebd4a-111">Requirements</span></span>  
 <span data-ttu-id="ebd4a-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebd4a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd4a-113">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ebd4a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ebd4a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd4a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd4a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebd4a-115">See also</span></span>

- [<span data-ttu-id="ebd4a-116">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebd4a-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="ebd4a-117">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebd4a-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
