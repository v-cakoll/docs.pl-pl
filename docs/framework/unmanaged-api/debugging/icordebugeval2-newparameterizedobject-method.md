---
title: ICorDebugEval2::NewParameterizedObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: f6ede42ac90f65f934e285f879bcef62d13b65cb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976099"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="1f228-102">ICorDebugEval2::NewParameterizedObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f228-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="1f228-103">Tworzy wystąpienie nowego obiektu typu sparametryzowanego i wywołuje metodę konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f228-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f228-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f228-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f228-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f228-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="1f228-106">podczas Wskaźnik do obiektu ICorDebugFunction, który reprezentuje konstruktora obiektu do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1f228-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="1f228-107">podczas Liczba przezakończonych argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="1f228-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="1f228-108">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje argument typu dla obiektu, który jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="1f228-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="1f228-109">podczas Liczba argumentów przeniesiona do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1f228-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="1f228-110">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który reprezentuje wartość argumentu, który jest przesyłany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1f228-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f228-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f228-111">Remarks</span></span>  
 <span data-ttu-id="1f228-112">Konstruktor obiektu może przyjmować <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="1f228-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f228-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f228-113">Requirements</span></span>  
 <span data-ttu-id="1f228-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f228-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f228-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1f228-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f228-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1f228-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f228-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f228-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
