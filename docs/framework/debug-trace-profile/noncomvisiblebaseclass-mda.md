---
title: nonComVisibleBaseClass MDA
description: Zobacz Asystent debugowania zarządzanego nonComVisibleBaseClass (MDA), który jest wywoływany w wywołaniach QueryInterface z kodu natywnego z niepowodzeniem z COR_E_INVALIDOPERATION.
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: 9f32b2c57f50fcd900b1fd78f4f8df1ec656a6db
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803926"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
`nonComVisibleBaseClass`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy `QueryInterface` wywołanie jest wykonywane przez kod natywny lub niezarządzany w przypadku niezarządzanej otoki COM (CCW) klasy zarządzanej com, która dziedziczy z klasy podstawowej, która nie jest widoczna dla modelu com.  `QueryInterface`Wywołanie powoduje aktywację elementu MDA tylko w przypadkach, gdy wywołania żądają interfejsu klasy lub domyślnej `IDispatch` klasy zarządzanej przez com.  Zdarzenie MDA nie jest uaktywniane, gdy `QueryInterface` jest przeznaczony dla jawnego interfejsu, który ma <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut zastosowany i jest jawnie zaimplementowany przez klasę widoczną dla modelu com.  
  
## <a name="symptoms"></a>Objawy  
 `QueryInterface`Wykonano wywołanie z kodu natywnego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.  WYNIK HRESULT może być spowodowany tym, że środowisko uruchomieniowe nie zezwoli na `QueryInterface` wywołania, które mogłyby spowodować aktywację tego elementu MDA.  
  
## <a name="cause"></a>Przyczyna  
 Środowisko uruchomieniowe nie może zezwolić na `QueryInterface` wywołania interfejsu klasy lub domyślnego `IDispatch` interfejsu klasy widocznej dla modelu COM, która dziedziczy z klasy, która nie jest widoczna dla modelu COM ze względu na potencjalne problemy z wersjami.  Na przykład, jeśli jakikolwiek publiczny element członkowski został dodany do klasy podstawowej, która nie jest widoczna dla modelu COM, istniejący klienci COM korzystający z klasy pochodnej mogą potencjalnie przerwać, ponieważ tablice metod pochodnych klasy pochodnej, która zawiera składowe klasy bazowej, zostałyby zmienione przez taką zmianę.  Jawne interfejsy uwidocznione dla modelu COM nie mają tego problemu, ponieważ nie obejmują podstawowych elementów członkowskich interfejsów w tablicy bazowej.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie ujawniaj interfejsu klasy. Zdefiniuj jawny interfejs i Zastosuj <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do niego atrybut.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej znajduje się przykładowy komunikat dla `QueryInterface` wywołania klasy widocznej dla modelu COM `Derived` , która dziedziczy z klasy niewidocznej dla modelu COM `Base` .  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
