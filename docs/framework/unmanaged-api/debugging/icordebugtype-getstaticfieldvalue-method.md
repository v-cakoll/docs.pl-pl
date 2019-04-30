---
title: ICorDebugType::GetStaticFieldValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c6b86c5ce3cc246af600d9b65d2fe12a0427f9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663846"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="c50e4-102">ICorDebugType::GetStaticFieldValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="c50e4-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="c50e4-103">Pobiera token w ramce stosu określony wskaźnik interfejsu do obiektu ICorDebugValue, który zawiera wartość pola statycznego odwołuje się określone pole.</span><span class="sxs-lookup"><span data-stu-id="c50e4-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c50e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c50e4-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c50e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c50e4-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="c50e4-106">[in] `mdFieldDef` Token, który określa pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="c50e4-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="c50e4-107">[in] Wskaźnik do ICorDebugFrame, który reprezentuje ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="c50e4-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c50e4-108">[out] Wskaźnik na adres `ICorDebugValue` zawierający wartość pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="c50e4-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c50e4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c50e4-109">Remarks</span></span>  
 <span data-ttu-id="c50e4-110">`GetStaticFieldValue` Metoda może być stosowana tylko wtedy, gdy typ jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, wskazane przez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c50e4-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="c50e4-111">Dla typu nieogólnego, operacja wykonana przez `GetStaticFieldValue` jest taka sama jak wywołanie [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass obiektu, który jest zwracany przez [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="c50e4-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="c50e4-112">Dla typów ogólnych wartość pola statyczne będą względem określonego podczas tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c50e4-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="c50e4-113">Ponadto jeśli pole statyczne prawdopodobnie może być określona względem wątku, kontekst lub domenę aplikacji, ramka stosu pomoże debugera określić poprawną wartość.</span><span class="sxs-lookup"><span data-stu-id="c50e4-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c50e4-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c50e4-114">Remarks</span></span>  
 <span data-ttu-id="c50e4-115">`GetStaticFieldValue` można używać tylko wtedy, gdy wywołanie `ICorDebugType::GetType` zwraca wartość ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="c50e4-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c50e4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c50e4-116">Requirements</span></span>  
 <span data-ttu-id="c50e4-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c50e4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c50e4-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c50e4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c50e4-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c50e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c50e4-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c50e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
