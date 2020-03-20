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
ms.openlocfilehash: 4c16432df201d19b65c91206ec529d07605e979a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181788"
---
# <a name="noncomvisiblebaseclass-mda"></a>nonComVisibleBaseClass MDA
Zarządzany `nonComVisibleBaseClass` asystent debugowania (MDA) jest `QueryInterface` aktywowany, gdy wywołanie jest nawiązywane przez kod macierzysty lub niezarządzany na otoce (CCW) wywoływanej przez COM klasy zarządzanej, która wywodzi się z klasy podstawowej, która nie jest widoczna dla modelu COM.  Wywołanie `QueryInterface` powoduje, że MDA, aby aktywować tylko `IDispatch` w przypadkach, gdy wywołania żąda interfejsu klasy lub domyślnie klasy zarządzanej widoczne com.  MDA nie jest aktywowany, gdy `QueryInterface` jest dla <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> jawnego interfejsu, który ma atrybut stosowane i jest jawnie implementowane przez klasę widoczne COM.  
  
## <a name="symptoms"></a>Objawy  
 Wywołanie `QueryInterface` wykonane z kodu macierzystego, który kończy się niepowodzeniem z COR_E_INVALIDOPERATION HRESULT.  HRESULT może być ze względu na czas `QueryInterface` wykonywania nie zezwalając na wywołania, które mogłyby spowodować aktywację tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Środowisko wykonawcze `QueryInterface` nie może zezwolić `IDispatch` na wywołania interfejsu klasy lub domyślnego interfejsu klasy widocznej w trybie COM, która pochodzi z klasy, która nie jest widoczna dla środowiska COM z powodu potencjalnych problemów z przechowywaniem wersji.  Na przykład jeśli wszystkie elementy publiczne zostały dodane do klasy podstawowej, która nie jest widoczna dla com, istniejących klientów COM przy użyciu klasy pochodnej może potencjalnie przerwać, ponieważ vtable klasy pochodnej, która zawiera elementy członkowskie klasy podstawowej, zostaną zmienione przez takie a Zmienić.  Jawne interfejsy narażone na COM nie mają tego problemu, ponieważ nie zawierają podstawowych elementów członkowskich interfejsów w vtable.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie należy udostępniać interfejsu klasy. Zdefiniuj jawny interfejs i zastosuj do niego <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 To MDA nie ma wpływu na CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładową `QueryInterface` wiadomość dla wywołania `Derived` klasy widocznej w trybie COM, `Base`która wywodzi się z klasy niewidocznej dla com.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
