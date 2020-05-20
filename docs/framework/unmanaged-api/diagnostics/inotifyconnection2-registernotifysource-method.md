---
title: INotifyConnection2::RegisterNotifySource — Metoda
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442075"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="a7f30-102">INotifyConnection2::RegisterNotifySource — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7f30-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="a7f30-103">Instaluje określone źródło powiadomień.</span><span class="sxs-lookup"><span data-stu-id="a7f30-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7f30-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7f30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7f30-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="a7f30-106">podczas Określa obiekt, który ma być używany jako źródło powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="a7f30-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="a7f30-107">określoną Odbiera obiekt, który ma być używany jako ujścia powiadomień.</span><span class="sxs-lookup"><span data-stu-id="a7f30-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7f30-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7f30-108">Return Value</span></span>  
 <span data-ttu-id="a7f30-109">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7f30-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f30-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7f30-110">Requirements</span></span>  
 <span data-ttu-id="a7f30-111">**Nagłówek:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="a7f30-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f30-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7f30-112">See also</span></span>

- [<span data-ttu-id="a7f30-113">INotifyConnection2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f30-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="a7f30-114">INotifySource2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f30-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="a7f30-115">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7f30-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="a7f30-116">UnregisterNotifySource, metoda</span><span class="sxs-lookup"><span data-stu-id="a7f30-116">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
