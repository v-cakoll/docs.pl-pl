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
ms.openlocfilehash: 9020fed83b1c57cae3cc492872a279afb0195983
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205174"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="afb48-102">ICorDebugILFrame2::EnumerateTypeParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="afb48-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="afb48-103">Pobiera obiekt ICorDebugTypeEnum, który zawiera <xref:System.Type> Parametry w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="afb48-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afb48-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afb48-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="afb48-106">Wskaźnik do adresu obiektu interfejsu ICorDebugTypeEnum, który umożliwia Wyliczenie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="afb48-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="afb48-107">Lista parametrów typu zawiera parametry typu klasy (jeśli istnieją), a następnie parametry typu metody (jeśli istnieją).</span><span class="sxs-lookup"><span data-stu-id="afb48-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afb48-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afb48-108">Remarks</span></span>  
 <span data-ttu-id="afb48-109">Użyj metody [IMetaDataImport2:: EnumGenericParams —](../metadata/imetadataimport2-enumgenericparams-method.md) , aby określić, ile parametrów typu klasy i parametrów typu metody ta lista zawiera.</span><span class="sxs-lookup"><span data-stu-id="afb48-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="afb48-110">Parametry typu nie są zawsze dostępne.</span><span class="sxs-lookup"><span data-stu-id="afb48-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb48-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afb48-111">Requirements</span></span>  
 <span data-ttu-id="afb48-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb48-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb48-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="afb48-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afb48-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="afb48-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afb48-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb48-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
