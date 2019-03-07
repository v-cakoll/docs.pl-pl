---
title: ICorDebugClass::GetStaticFieldValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471631"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="ea712-102">ICorDebugClass::GetStaticFieldValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea712-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="ea712-103">Pobiera wartość określonego pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="ea712-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea712-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea712-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea712-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea712-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="ea712-106">[in] Pole `Def` token, który odwołuje się do pola, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="ea712-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="ea712-107">[in] Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, która ma być używany, aby rozróżniać wśród wątku, kontekstu lub statystyce domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea712-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="ea712-108">Jeśli pola statycznego jest określana względem wątku, kontekst lub domenę aplikacji, ramki określi poprawnej wartości.</span><span class="sxs-lookup"><span data-stu-id="ea712-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ea712-109">[out] Wskaźnik na adres obiektu ICorDebugValue, która reprezentuje wartość pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="ea712-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea712-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea712-110">Remarks</span></span>  
 <span data-ttu-id="ea712-111">Dla typów sparametryzowanych wartość pola statycznego jest względem określonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ea712-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="ea712-112">W związku z tym jeśli Konstruktor klasy ma parametry typu <xref:System.Type>, wywołaj [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) zamiast `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="ea712-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea712-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea712-113">Requirements</span></span>  
 <span data-ttu-id="ea712-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea712-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea712-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea712-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea712-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea712-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea712-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea712-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
