---
title: 'ICorDebugSymbolProvider2:: GetFrameProps, Metoda'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ad44c5a7b2d901967ae354f3c30218a8c7f2c2de
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379335"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="975a4-102">ICorDebugSymbolProvider2:: GetFrameProps, Metoda</span><span class="sxs-lookup"><span data-stu-id="975a4-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="975a4-103">Zwraca metodę rozpoczynającą względny adres wirtualny metody i ramkę nadrzędną, w której znajduje się adres wirtualny względem kodu.</span><span class="sxs-lookup"><span data-stu-id="975a4-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="975a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="975a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="975a4-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="975a4-106">podczas Względny adres wirtualny.</span><span class="sxs-lookup"><span data-stu-id="975a4-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="975a4-107">określoną Wskaźnik do początkowego adresu wirtualnego względnej metody.</span><span class="sxs-lookup"><span data-stu-id="975a4-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="975a4-108">określoną Wskaźnik do początkowego adresu wirtualnego ramki.</span><span class="sxs-lookup"><span data-stu-id="975a4-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="975a4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="975a4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="975a4-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="975a4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975a4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="975a4-111">Requirements</span></span>  
 <span data-ttu-id="975a4-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="975a4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="975a4-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="975a4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="975a4-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="975a4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="975a4-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="975a4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975a4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="975a4-116">See also</span></span>

- [<span data-ttu-id="975a4-117">ICorDebugSymbolProvider2, interfejs</span><span class="sxs-lookup"><span data-stu-id="975a4-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="975a4-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="975a4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
