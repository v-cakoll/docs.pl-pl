---
title: ICorDebugType2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 0e480db953131d7771e493a8f367154a7d17dada
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396630"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="087f7-102">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="087f7-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="087f7-103">Rozszerza interfejs ICorDebugType w celu pobrania identyfikatora typu podstawowego lub złożonego (zdefiniowanego przez użytkownika).</span><span class="sxs-lookup"><span data-stu-id="087f7-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="087f7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="087f7-104">Methods</span></span>  
  
|<span data-ttu-id="087f7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="087f7-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="087f7-106">GetTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="087f7-106">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="087f7-107">Pobiera [COR_TYPEID](cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="087f7-107">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="087f7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="087f7-108">Remarks</span></span>  
 <span data-ttu-id="087f7-109">Ten interfejs jest logicznym rozszerzeniem interfejsu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="087f7-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="087f7-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="087f7-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="087f7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="087f7-111">Example</span></span>  
 <span data-ttu-id="087f7-112">Poniższy fragment kodu ilustruje użycie metody [ICorDebugType2:: GetTypeId](icordebugtype2-gettypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="087f7-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="087f7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="087f7-113">Requirements</span></span>  
 <span data-ttu-id="087f7-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="087f7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="087f7-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="087f7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="087f7-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="087f7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="087f7-117">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="087f7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087f7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="087f7-118">See also</span></span>

- [<span data-ttu-id="087f7-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="087f7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
