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
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791273"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="03379-102">ICorDebugType::GetStaticFieldValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="03379-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="03379-103">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który zawiera wartość pola statycznego, do którego odwołuje się określony token pola w określonej ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="03379-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03379-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03379-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03379-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03379-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="03379-106">podczas Token `mdFieldDef`, który określa pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="03379-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="03379-107">podczas Wskaźnik do elementu ICorDebugFrame, który reprezentuje ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="03379-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="03379-108">określoną Wskaźnik do adresu `ICorDebugValue`, który zawiera wartość pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="03379-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03379-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03379-109">Remarks</span></span>  
 <span data-ttu-id="03379-110">Metody `GetStaticFieldValue` można używać tylko wtedy, gdy typ jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, jak wskazano w metodzie [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="03379-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="03379-111">W przypadku typów innych niż ogólne Operacja wykonywana przez `GetStaticFieldValue` jest taka sama jak wywołanie [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) w obiekcie ICorDebugClass, który jest zwracany przez [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="03379-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="03379-112">W przypadku typów ogólnych wartość pola statycznego będzie określana względem konkretnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="03379-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="03379-113">Ponadto, jeśli pole statyczne może być powiązane z wątkiem, kontekstem lub domeną aplikacji, Ramka stosu pomoże debugerowi określić odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="03379-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03379-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03379-114">Remarks</span></span>  
 <span data-ttu-id="03379-115">`GetStaticFieldValue` można używać tylko wtedy, gdy wywołanie `ICorDebugType::GetType` zwraca wartość ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="03379-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03379-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03379-116">Requirements</span></span>  
 <span data-ttu-id="03379-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03379-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03379-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03379-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03379-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="03379-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03379-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03379-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
