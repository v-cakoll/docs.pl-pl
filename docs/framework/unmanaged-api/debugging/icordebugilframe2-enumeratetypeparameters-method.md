---
title: ICorDebugILFrame2::EnumerateTypeParameters — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7454b551edc546fecbd9d091f7c821e0a07b16df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988549"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="57d17-102">ICorDebugILFrame2::EnumerateTypeParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="57d17-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="57d17-103">Pobiera obiekt zawierający icordebugtypeenum — <xref:System.Type> parametrów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="57d17-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57d17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57d17-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57d17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57d17-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="57d17-106">Wskaźnik na adres obiektu interfejsu icordebugtypeenum —, umożliwiający wyliczenie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="57d17-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="57d17-107">Lista parametrów typu zawiera parametrów typu klasy (jeśli istnieje) następuje z parametrami typu metody (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="57d17-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57d17-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57d17-108">Remarks</span></span>  
 <span data-ttu-id="57d17-109">Użyj [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) metodę pozwala ustalić, ile parametrów typu klasy i metody typu ta lista zawiera parametry.</span><span class="sxs-lookup"><span data-stu-id="57d17-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="57d17-110">Parametry typu nie są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="57d17-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57d17-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57d17-111">Requirements</span></span>  
 <span data-ttu-id="57d17-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57d17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57d17-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57d17-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57d17-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57d17-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57d17-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57d17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
