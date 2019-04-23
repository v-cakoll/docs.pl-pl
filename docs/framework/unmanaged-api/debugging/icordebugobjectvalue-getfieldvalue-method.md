---
title: ICorDebugObjectValue::GetFieldValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8778edf9ac6e32d5dab3a53a6d9cc643a8df13b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107916"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="24296-102">ICorDebugObjectValue::GetFieldValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="24296-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="24296-103">Pobiera wartość określonego pola określonej klasie dla tej wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="24296-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24296-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24296-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24296-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24296-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="24296-106">[in] Wskaźnik do obiektu "ICorDebugClass", który reprezentuje klasę, dla którego należy pobrać wartości pola.</span><span class="sxs-lookup"><span data-stu-id="24296-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="24296-107">[in] `mdFieldDef` Token, który odwołuje się do metadanych opisujących pola.</span><span class="sxs-lookup"><span data-stu-id="24296-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="24296-108">[out] Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość określonego pola.</span><span class="sxs-lookup"><span data-stu-id="24296-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24296-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24296-109">Remarks</span></span>  
 <span data-ttu-id="24296-110">Klasa określona w `pClass` parametru musi być w hierarchii klasy wartości obiektu, a pole musi być polem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="24296-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="24296-111">`GetFieldValue` Metoda zakończy się powodzeniem dla ogólnych obiektów i klas ogólnych.</span><span class="sxs-lookup"><span data-stu-id="24296-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="24296-112">Na przykład jeśli MyDictionary\<V > dziedziczy ze słownika\<ciągu V >, i wartość obiektu jest typu MyDictionary\<int32 >, przekazując `ICorDebugClass` obiekt słownika\<K, V > będzie pomyślnie pobrać polem słownika\<ciąg, int32 >.</span><span class="sxs-lookup"><span data-stu-id="24296-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24296-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24296-113">Requirements</span></span>  
 <span data-ttu-id="24296-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24296-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24296-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24296-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24296-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24296-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24296-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24296-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24296-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24296-118">See also</span></span>
