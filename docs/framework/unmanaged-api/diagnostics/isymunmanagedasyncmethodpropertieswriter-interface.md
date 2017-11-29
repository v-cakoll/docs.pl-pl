---
title: "ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd84ea5ee00df3e59d4907cdf97bc36b7f06d993
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs
Można zdefiniować informacje dotyczące metody asynchronicznej opcjonalne dla każdego symbolu — metoda. Zawsze używaj metodą otwarty; oznacza to, że między wywołań [OpenMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) i [CloseMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs zawiera następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineAsyncStepInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Zdefiniuj grupę asynchronicznych operacji w bieżącej metodzie await.<br /><br /> Przesunięcie każdego yield odpowiada instrukcji return await, identyfikowanie potencjalnej wydajności. Każdy `breakpointMethod` / `breakpointOffset` pary identyfikuje, gdy operacja asynchroniczna wznowi; być może jest ona w innej metody.|  
|[DefineCatchHandlerILOffset — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Ustawia IL przesunięcie obsługi catch generowane przez kompilator, który opakowuje metody asynchronicznej.<br /><br /> Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on kodu innych użytkowników, mimo że może wystąpić w metody kodu użytkownika. W szczególności, jest on używany w odpowiedzi na **CatchHandlerFound** zdarzeniu wyjątku.|  
|[DefineKickoffMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Ustawia metodę początkową, który inicjuje operacji asynchronicznej.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
