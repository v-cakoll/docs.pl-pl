---
title: Metoda ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: ba1cc8c91c53547c6ed4025ee67a69e253f3596d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783582"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="60ce0-102">Metoda ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="60ce0-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="60ce0-103">Zwraca ścieżkę modułu z adresu podstawowego modułu.</span><span class="sxs-lookup"><span data-stu-id="60ce0-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ce0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60ce0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60ce0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60ce0-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="60ce0-106">podczas Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="60ce0-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="60ce0-107">podczas Liczba znaków w buforze, która ma otrzymać ścieżkę modułu.</span><span class="sxs-lookup"><span data-stu-id="60ce0-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="60ce0-108">określoną Wskaźnik do liczby znaków zapisanych w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="60ce0-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="60ce0-109">określoną Ścieżka modułu.</span><span class="sxs-lookup"><span data-stu-id="60ce0-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60ce0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60ce0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60ce0-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="60ce0-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60ce0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60ce0-112">Requirements</span></span>  
 <span data-ttu-id="60ce0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60ce0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ce0-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60ce0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60ce0-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60ce0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60ce0-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60ce0-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ce0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60ce0-117">See also</span></span>

- [<span data-ttu-id="60ce0-118">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="60ce0-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="60ce0-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="60ce0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
