---
title: "ICorDebugILFrame2::EnumerateTypeParameters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9180ea68dde667ffe0dc8e15b98cb82efaa667ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="6d2a8-102">ICorDebugILFrame2::EnumerateTypeParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d2a8-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="6d2a8-103">Pobiera obiekt ICorDebugTypeEnum zawierający <xref:System.Type> parametrów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="6d2a8-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d2a8-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d2a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d2a8-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="6d2a8-106">Wskaźnik do adresu ICorDebugTypeEnum obiektu interfejs, umożliwiający wyliczenie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="6d2a8-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="6d2a8-107">Parametry typu zawierają parametrów typu klasy (jeśli istnieją) następuje parametr typu metody (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="6d2a8-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d2a8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d2a8-108">Remarks</span></span>  
 <span data-ttu-id="6d2a8-109">Użyj [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) metodę, aby określić, ile parametrów typu klasy i metody ta lista zawiera parametry typu.</span><span class="sxs-lookup"><span data-stu-id="6d2a8-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="6d2a8-110">Parametry typu nie są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="6d2a8-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2a8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d2a8-111">Requirements</span></span>  
 <span data-ttu-id="6d2a8-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2a8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d2a8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d2a8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d2a8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d2a8-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
