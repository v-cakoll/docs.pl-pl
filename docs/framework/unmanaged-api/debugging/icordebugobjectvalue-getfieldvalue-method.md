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
ms.openlocfilehash: 002c6cccb3ddf29b831ba5e14baa5e51f1b82433
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095878"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="cab3c-102">ICorDebugObjectValue::GetFieldValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="cab3c-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="cab3c-103">Pobiera wartość określonego pola określonej klasy dla tej wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="cab3c-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cab3c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cab3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cab3c-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="cab3c-106">podczas Wskaźnik do obiektu "ICorDebugClass", który reprezentuje klasę, dla której ma zostać pobrana wartość pola.</span><span class="sxs-lookup"><span data-stu-id="cab3c-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="cab3c-107">podczas Token `mdFieldDef`, który odwołuje się do metadanych opisujących pole.</span><span class="sxs-lookup"><span data-stu-id="cab3c-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="cab3c-108">określoną Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość określonego pola.</span><span class="sxs-lookup"><span data-stu-id="cab3c-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cab3c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cab3c-109">Remarks</span></span>  
 <span data-ttu-id="cab3c-110">Klasa określona w parametrze `pClass` musi znajdować się w hierarchii klasy wartości obiektu, a pole musi być polem tej klasy.</span><span class="sxs-lookup"><span data-stu-id="cab3c-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="cab3c-111">Metoda `GetFieldValue` nadal powiedzie się dla obiektów ogólnych i klas ogólnych.</span><span class="sxs-lookup"><span data-stu-id="cab3c-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="cab3c-112">Na przykład, jeśli program webdictionary\<V > dziedziczy ze słownika\<String, V >, a wartość obiektu to typu webdictionary\<Int32 >, przekazanie obiektu `ICorDebugClass` dla słownika\<K, >\<słownika, ciąg Int32 >.</span><span class="sxs-lookup"><span data-stu-id="cab3c-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cab3c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cab3c-113">Requirements</span></span>  
 <span data-ttu-id="cab3c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cab3c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cab3c-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cab3c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cab3c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cab3c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cab3c-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab3c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab3c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cab3c-118">See also</span></span>
