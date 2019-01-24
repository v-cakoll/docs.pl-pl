---
title: nonComVisibleBaseClass MDA
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a26863f2a1880cffba5eb3ea51573f45323be72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700861"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po `QueryInterface` klasy COM widoczny dla zarządzanych, która pochodzi od klasy podstawowej, która nie jest widoczne dla modelu COM, natywny lub kodowi niezarządzanemu na wywoływana otoka COM (CCW) zostanie nawiązane połączenie.  `QueryInterface` Wywołanie powoduje, że MDA aktywować tylko w przypadkach, w której żądania wywołań interfejsu klasy lub domyślna `IDispatch` COM widoczny dla klas zarządzanych.  MDA jest aktywowane gdy `QueryInterface` jest jawne interfejsu, który ma <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut zastosowane i jest jawnie implementowane przez klasy widoczne COM.  
  
## <a name="symptoms"></a>Symptomy  
 A `QueryInterface` wywołania z kodu macierzystego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.  HRESULT może wynikać ze środowiska uruchomieniowego nie można przydzielać `QueryInterface` wywołania, które mogą być przyczyną aktywacji to zdarzenie MDA.  
  
## <a name="cause"></a>Przyczyna  
 Środowisko wykonawcze nie może dopuścić `QueryInterface` wywołania do klasy interfejsu lub domyślne `IDispatch` interfejsu klasy widoczne COM, która pochodzi od klasy, które nie są widoczne dla modelu COM ze względu na potencjalne problemy z wersjonowaniem.  Na przykład, jeśli wszystkie publiczne elementy członkowskie zostały dodane do klasy bazowej, który nie jest widoczny dla modelu COM, istniejących klientów modelu COM za pomocą klasy pochodnej może potencjalnie uszkodzić ponieważ vtable klasy pochodnej, która zawiera składowe klasy podstawowej, może być zmienione przez takie Zmiana.  Jawne interfejsy widoczne dla modelu COM nie mają tego problemu, ponieważ nie zawierają elementów podstawowych interfejsów w vtable.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie ujawniaj interfejsu klasy. Definiowanie interfejsu jawnego i stosowanie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu do niego.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowy komunikat dla `QueryInterface` wywołać klasy widoczne COM `Derived` która jest pochodną klasy COM-niewidocznych `Base`.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
