---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a476d92486d7f2523dfbcc8b25e9c11e26c55f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425618"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="4d37b-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d37b-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="4d37b-103">Ustawia metodę początkową, który inicjuje operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="4d37b-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d37b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d37b-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d37b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d37b-105">Parameters</span></span>  
  
|<span data-ttu-id="4d37b-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="4d37b-106">Parameter</span></span>|<span data-ttu-id="4d37b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4d37b-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="4d37b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d37b-108">Return Value</span></span>  
 <span data-ttu-id="4d37b-109">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4d37b-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d37b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d37b-110">Requirements</span></span>  
 <span data-ttu-id="4d37b-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d37b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d37b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d37b-112">See Also</span></span>  
 [<span data-ttu-id="4d37b-113">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d37b-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
