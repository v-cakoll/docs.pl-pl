---
title: ICorDebugValue2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: d036ddf353aa3a622ade05e1e2daa7f170d28f63
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396775"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="c258e-102">ICorDebugValue2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c258e-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="c258e-103">Rozszerza interfejs "ICorDebugValue", aby zapewnić obsługę obiektów "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="c258e-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c258e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c258e-104">Methods</span></span>  
  
|<span data-ttu-id="c258e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c258e-105">Method</span></span>|<span data-ttu-id="c258e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c258e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c258e-107">GetExactType, metoda</span><span class="sxs-lookup"><span data-stu-id="c258e-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="c258e-108">Pobiera wskaźnik interfejsu do `ICorDebugType` obiektu, który reprezentuje <xref:System.Type> tę wartość.</span><span class="sxs-lookup"><span data-stu-id="c258e-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c258e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c258e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c258e-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="c258e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c258e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c258e-111">Requirements</span></span>  
 <span data-ttu-id="c258e-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c258e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c258e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c258e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c258e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c258e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c258e-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c258e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c258e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c258e-116">See also</span></span>

- [<span data-ttu-id="c258e-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c258e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="c258e-118">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c258e-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
