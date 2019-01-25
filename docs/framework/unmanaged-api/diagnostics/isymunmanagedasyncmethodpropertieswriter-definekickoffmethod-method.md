---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38b4564aeb3c8ed4674e755e5691bb0a9d417bca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624197"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="8ccc4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ccc4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="8ccc4-103">Ustawia metodę początkową, która inicjuje operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ccc4-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ccc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ccc4-105">Parameters</span></span>  
  
|<span data-ttu-id="8ccc4-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="8ccc4-106">Parameter</span></span>|<span data-ttu-id="8ccc4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8ccc4-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="8ccc4-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ccc4-108">Return Value</span></span>  
 <span data-ttu-id="8ccc4-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="8ccc4-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccc4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ccc4-110">Requirements</span></span>  
 <span data-ttu-id="8ccc4-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ccc4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccc4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ccc4-112">See also</span></span>
- [<span data-ttu-id="8ccc4-113">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ccc4-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
