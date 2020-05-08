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
ms.openlocfilehash: d4a254853256e1a1440f5588418b94e39eabcc9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894111"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="b5038-102">ICorDebugClass::GetStaticFieldValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5038-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="b5038-103">Pobiera wartość określonego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="b5038-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5038-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5038-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5038-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5038-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="b5038-106">podczas Token pola `Def` , który odwołuje się do pola, które ma zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="b5038-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="b5038-107">podczas Wskaźnik do obiektu ICorDebugFrame, który reprezentuje ramkę, która ma zostać użyta do rozróżnienia między elementem statycznym, kontekstowym lub domeną aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5038-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="b5038-108">Jeśli pole statyczne jest powiązane z wątkiem, kontekstem lub domeną aplikacji, ramka będzie określać odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="b5038-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b5038-109">określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="b5038-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5038-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5038-110">Remarks</span></span>  
 <span data-ttu-id="b5038-111">W przypadku typów sparametryzowanych wartość pola statycznego jest określana względem konkretnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b5038-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="b5038-112">W związku z tym, jeśli Konstruktor klasy przyjmuje parametry <xref:System.Type>typu, należy wywołać [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) zamiast `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="b5038-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5038-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5038-113">Requirements</span></span>  
 <span data-ttu-id="b5038-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5038-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5038-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b5038-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5038-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b5038-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5038-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5038-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
