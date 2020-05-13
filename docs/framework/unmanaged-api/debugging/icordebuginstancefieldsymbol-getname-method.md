---
title: 'ICorDebugInstanceFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 0f1b648f494a2f2676374cfd13db46b70f1f195c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209997"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="f344c-102">ICorDebugInstanceFieldSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="f344c-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="f344c-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f344c-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f344c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f344c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f344c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f344c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f344c-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="f344c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f344c-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="f344c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f344c-108">określoną Tablica znaków przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="f344c-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f344c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f344c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f344c-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f344c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f344c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f344c-111">Requirements</span></span>  
 <span data-ttu-id="f344c-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f344c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f344c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f344c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f344c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f344c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f344c-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f344c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f344c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f344c-116">See also</span></span>

- [<span data-ttu-id="f344c-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="f344c-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="f344c-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f344c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
