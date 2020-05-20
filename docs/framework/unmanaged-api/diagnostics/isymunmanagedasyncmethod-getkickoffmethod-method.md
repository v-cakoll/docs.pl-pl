---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 879b9eac7cb6df06ffe4f994b505ea9cb2396d7f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441841"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="0ecce-102">ISymUnmanagedAsyncMethod::GetKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ecce-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="0ecce-103">Zobacz [DefineKickoffMethod —](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ecce-103">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ecce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ecce-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ecce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ecce-105">Parameters</span></span>  
  
|<span data-ttu-id="0ecce-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="0ecce-106">Parameter</span></span>|<span data-ttu-id="0ecce-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0ecce-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="0ecce-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0ecce-108">Return Value</span></span>  
 <span data-ttu-id="0ecce-109">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0ecce-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ecce-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ecce-110">Requirements</span></span>  
 <span data-ttu-id="0ecce-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0ecce-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecce-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ecce-112">See also</span></span>

- [<span data-ttu-id="0ecce-113">ISymUnmanagedAsyncMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ecce-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
