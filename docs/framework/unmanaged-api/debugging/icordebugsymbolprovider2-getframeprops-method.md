---
title: 'ICorDebugSymbolProvider2:: GetFrameProps, Metoda'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: 39bdb93fcb48da6667d982ca2d511ee5e499ae32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133644"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="4c15c-102">ICorDebugSymbolProvider2:: GetFrameProps, Metoda</span><span class="sxs-lookup"><span data-stu-id="4c15c-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="4c15c-103">Zwraca metodę rozpoczynającą względny adres wirtualny metody i ramkę nadrzędną, w której znajduje się adres wirtualny względem kodu.</span><span class="sxs-lookup"><span data-stu-id="4c15c-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c15c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c15c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c15c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c15c-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="4c15c-106">podczas Względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="4c15c-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="4c15c-107">określoną Wskaźnik do początkowego adresu wirtualnego względnej metody.</span><span class="sxs-lookup"><span data-stu-id="4c15c-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="4c15c-108">określoną Wskaźnik do początkowego adresu wirtualnego ramki.</span><span class="sxs-lookup"><span data-stu-id="4c15c-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c15c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c15c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c15c-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4c15c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c15c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c15c-111">Requirements</span></span>  
 <span data-ttu-id="4c15c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c15c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c15c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c15c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c15c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4c15c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c15c-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c15c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c15c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c15c-116">See also</span></span>

- [<span data-ttu-id="4c15c-117">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c15c-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="4c15c-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4c15c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
