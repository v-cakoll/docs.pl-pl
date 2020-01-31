---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 118f52db63464b4c9355ba9ee7f330b996c5bf71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792247"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="c1bc0-102">Metoda ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="c1bc0-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="c1bc0-103">Zawiera informacje dotyczące funkcji wyeksportowanych przez środowisko uruchomieniowe, które ułatwiają przechodzenie przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1bc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1bc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1bc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1bc0-105">Parameters</span></span>  
 <span data-ttu-id="c1bc0-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="c1bc0-106">pszExportName</span></span>  
 <span data-ttu-id="c1bc0-107">podczas Nazwa funkcji eksportu środowiska uruchomieniowego, która została zapisywana w tabeli eksportu PE.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="c1bc0-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="c1bc0-108">invokeKind</span></span>  
 <span data-ttu-id="c1bc0-109">określoną Wskaźnik do elementu członkowskiego wyliczenia [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) , który opisuje sposób, w jaki wyeksportowana funkcja wywoła kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="c1bc0-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="c1bc0-110">invokePurpose</span></span>  
 <span data-ttu-id="c1bc0-111">określoną Wskaźnik do elementu członkowskiego wyliczenia [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) , który opisuje, dlaczego wyeksportowana funkcja wywoła kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1bc0-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="c1bc0-112">Return Value</span></span>  
 <span data-ttu-id="c1bc0-113">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="c1bc0-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c1bc0-114">Return value</span></span>|<span data-ttu-id="c1bc0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c1bc0-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="c1bc0-116">Wywołanie metody zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="c1bc0-117">`pInvokeKind` lub `pInvokePurpose` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="c1bc0-118">Inne błędne wartości `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="c1bc0-119">Zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1bc0-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1bc0-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1bc0-121">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c1bc0-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1bc0-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1bc0-122">Requirements</span></span>  
 <span data-ttu-id="c1bc0-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1bc0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1bc0-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c1bc0-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1bc0-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c1bc0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1bc0-126">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1bc0-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1bc0-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1bc0-127">See also</span></span>

- [<span data-ttu-id="c1bc0-128">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1bc0-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="c1bc0-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c1bc0-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
