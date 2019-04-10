---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226615"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="04d0d-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="04d0d-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="04d0d-103">Ustawia metodę początkową, która inicjuje operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="04d0d-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04d0d-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04d0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04d0d-105">Parameters</span></span>  
  
|<span data-ttu-id="04d0d-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="04d0d-106">Parameter</span></span>|<span data-ttu-id="04d0d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="04d0d-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="04d0d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04d0d-108">Return Value</span></span>  
 <span data-ttu-id="04d0d-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="04d0d-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d0d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04d0d-110">Requirements</span></span>  
 <span data-ttu-id="04d0d-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="04d0d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d0d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04d0d-112">See also</span></span>

- [<span data-ttu-id="04d0d-113">ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="04d0d-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
