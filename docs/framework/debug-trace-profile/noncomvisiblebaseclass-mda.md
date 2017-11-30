---
title: nonComVisibleBaseClass MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b43ad5c039be3ad1c4e57bad12304927a76fb6c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass` Zarządzany Asystent debugowania (MDA) została aktywowana po `QueryInterface` kod natywny lub niezarządzane w wywoływana otoka COM (CCW) wywołanie, widoczny dla modelu COM zarządzane klasy, która pochodzi z klasy podstawowej, która nie jest widoczne dla modelu COM.  `QueryInterface` MDA aktywować tylko w przypadkach, gdy wywołanie zażąda klasy interfejsu lub domyślnej powoduje, że wywołanie `IDispatch` widoczny dla modelu COM klasy zarządzane.  MDA nie jest aktywowany, gdy `QueryInterface` dotyczy jawnego interfejsu, który ma <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut stosowane i jest jawnie implementowana przez widoczny dla modelu COM klasy.  
  
## <a name="symptoms"></a>Symptomy  
 A `QueryInterface` wywołania z kodu macierzystego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.  HRESULT może wynikać ze środowiska uruchomieniowego, brak zezwolenia `QueryInterface` wywołania, które mogłyby spowodować aktywacji to zdarzenie MDA.  
  
## <a name="cause"></a>Przyczyna  
 Środowisko uruchomieniowe nie może dopuścić `QueryInterface` odwołuje się do klasy interfejsu lub domyślna `IDispatch` interfejsu widoczny dla modelu COM klasy, która pochodzi z klasy, która nie jest widoczny dla modelu COM ze względu na potencjalne problemy przechowywania wersji.  Na przykład, jeśli wszystkie publiczne elementy członkowskie zostały dodane do klasy podstawowej, która nie jest widoczny dla modelu COM, istniejących klientów modelu COM za pomocą klasy pochodnej może potencjalnie spowodować przerwanie ponieważ vtable klasy pochodnej, która zawiera elementów członkowskich klasy podstawowej, czy można zmienić takie Zmiana.  Jawne interfejsy ujawniony dla modelu COM nie mają ten problem, ponieważ nie zawierają podstawowe elementy członkowskie interfejsów w vtable.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie ujawniaj interfejsu klasy. Zdefiniuj jawnego interfejsu i zastosować <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do niej atrybut.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowy komunikat dla `QueryInterface` wywoływać dla klasy widoczne COM `Derived` który dziedziczy z klasy niewidoczne COM `Base`.  
  
```  
A QueryInterface call was made requesting the class interface of COM   
visible managed class 'Derived'. However since this class derives from   
non COM visible class 'Base', the QueryInterface call will fail. This   
is done to prevent the non COM visible base class from being   
constrained by the COM versioning rules.   
```  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
