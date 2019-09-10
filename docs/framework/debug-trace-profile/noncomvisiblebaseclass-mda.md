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
ms.openlocfilehash: a52460bbbf2b5f65f5c15d2cd06be7d3917f68bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854054"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
Asystent debugowania `QueryInterface` zarządzanego (MDA) jest uaktywniany, gdy wywołanie jest wykonywane przez kod natywny lub niezarządzany w przypadku niezarządzanej otoki COM (CCW) klasy zarządzanej com, która dziedziczy z klasy podstawowej, która nie jest widoczna dla modelu com. `nonComVisibleBaseClass`  Wywołanie powoduje aktywację elementu MDA tylko w przypadkach, gdy wywołania żądają interfejsu klasy lub domyślnej `IDispatch` klasy zarządzanej przez com. `QueryInterface`  Zdarzenie MDA nie jest uaktywniane, `QueryInterface` gdy jest przeznaczony dla jawnego interfejsu, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> który ma atrybut zastosowany i jest jawnie zaimplementowany przez klasę widoczną dla modelu com.  
  
## <a name="symptoms"></a>Symptomy  
 Wykonano `QueryInterface` wywołanie z kodu natywnego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.  Wynik HRESULT może być spowodowany tym, że środowisko uruchomieniowe nie zezwoli `QueryInterface` na wywołania, które mogłyby spowodować aktywację tego elementu MDA.  
  
## <a name="cause"></a>Przyczyna  
 Środowisko uruchomieniowe nie `QueryInterface` może zezwolić na wywołania interfejsu klasy lub `IDispatch` domyślnego interfejsu klasy widocznej dla modelu COM, która dziedziczy z klasy, która nie jest widoczna dla modelu COM ze względu na potencjalne problemy z wersjami.  Na przykład, jeśli jakikolwiek publiczny element członkowski został dodany do klasy podstawowej, która nie jest widoczna dla modelu COM, istniejący klienci COM korzystający z klasy pochodnej mogą potencjalnie przerwać, ponieważ tablice metod pochodnych klasy pochodnej, która zawiera składowe klasy bazowej, zostałyby zmienione przez takie stąp.  Jawne interfejsy uwidocznione dla modelu COM nie mają tego problemu, ponieważ nie obejmują podstawowych elementów członkowskich interfejsów w tablicy bazowej.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie ujawniaj interfejsu klasy. Zdefiniuj jawny interfejs i Zastosuj <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do niego atrybut.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej znajduje się przykładowy komunikat dla `QueryInterface` wywołania klasy `Derived` widocznej dla modelu COM, która dziedziczy z klasy `Base`niewidocznej dla modelu com.  
  
```output
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
