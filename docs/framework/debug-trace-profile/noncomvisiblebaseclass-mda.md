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
ms.openlocfilehash: b46d5c6ffbf12efbae113a95bbfccd5742ec9ec9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217304"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
Asystent debugowania zarządzanego `nonComVisibleBaseClass` (MDA) jest uaktywniany, gdy wywołanie `QueryInterface` odbywa się przy użyciu kodu natywnego lub niezarządzanego w przypadku niewidocznej otoki COM (CCW) klasy zarządzanej w modelu COM, która dziedziczy z klasy podstawowej, która nie jest widoczna dla modelu COM.  Wywołanie `QueryInterface` powoduje aktywację elementu MDA tylko w przypadkach, gdy wywołania żądają interfejsu klasy lub domyślnej `IDispatch` klasy zarządzanej widocznej dla modelu COM.  Zdarzenie MDA nie jest aktywowane, gdy `QueryInterface` dotyczy jawnego interfejsu, do którego zastosowano atrybut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> i jest on jawnie zaimplementowany przez klasę widoczną dla modelu COM.  
  
## <a name="symptoms"></a>Objawy  
 Wywołanie `QueryInterface` wykonane z kodu natywnego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.  WYNIK HRESULT może być spowodowany tym, że środowisko uruchomieniowe nie zezwoli na `QueryInterface` wywołań, które mogłyby spowodować aktywację tego elementu MDA.  
  
## <a name="cause"></a>Przyczyna  
 Środowisko wykonawcze nie może zezwalać na `QueryInterface` wywołań interfejsu klasy ani domyślnego interfejsu `IDispatch` klasy widocznej dla modelu COM, która dziedziczy z klasy, która nie jest widoczna dla modelu COM ze względu na potencjalne problemy z wersjami.  Na przykład, jeśli jakikolwiek publiczny element członkowski został dodany do klasy podstawowej, która nie jest widoczna dla modelu COM, istniejący klienci COM korzystający z klasy pochodnej mogą potencjalnie przerwać, ponieważ tablice metod pochodnych klasy pochodnej, która zawiera składowe klasy bazowej, zostałyby zmienione przez takie stąp.  Jawne interfejsy uwidocznione dla modelu COM nie mają tego problemu, ponieważ nie obejmują podstawowych elementów członkowskich interfejsów w tablicy bazowej.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie ujawniaj interfejsu klasy. Zdefiniuj jawny interfejs i Zastosuj do niego atrybut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej znajduje się przykładowy komunikat dla wywołania `QueryInterface` na klasie widocznej dla modelu COM `Derived`, który pochodzi z klasy niewidocznej dla modelu COM, `Base`.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
