---
title: dirtyCastAndCallOnInterface MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a28820479ca15ad72475ae9a7754bbbf99ce5c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108592"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
`dirtyCastAndCallOnInterface` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy próba zostanie podjęta na interfejs klasy, która została oznaczona z późnym wiązaniem tylko wywołanie wczesnym wiązaniem przy użyciu wartości vtable.  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwane zachowanie podczas umieszczania wywołania z wczesnym wiązaniem za pośrednictwem modelu COM do środowiska CLR.  
  
## <a name="cause"></a>Przyczyna  
 Kod próbuje wywołania wczesnym wiązaniem vtable za pośrednictwem interfejsu klasy, która jest tylko z późnym wiązaniem. Należy pamiętać, że przez domyślną klasę interfejsy są identyfikowane jako trwa z późnym wiązaniem tylko. Można również zidentyfikować jako z późnym wiązaniem przy użyciu <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> wartość (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Rozwiązanie  
 Zalecane rozwiązanie jest zdefiniowanie interfejsu jawnego do użycia przez model COM i mieć wywołania klientów modelu COM za pośrednictwem tego interfejsu, zamiast za pośrednictwem interfejsu automatycznie wygenerowana klasa. Alternatywnie wywołania z modelu COM mogą zostać przekształcone do wywołania późnego wiązania za pośrednictwem `IDispatch`.  
  
 Na koniec jest możliwe zidentyfikować klasę jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) umożliwia wywołania z wczesnym wiązaniem do umieszczenia z modelu COM; jednak za pomocą <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zdecydowanie odradzane ze względu na ograniczenia wersji opisanego w <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o wywołaniach wczesnym wiązaniem dla interfejsów z późnym wiązaniem.  
  
## <a name="output"></a>Dane wyjściowe  
 Nazwa metody lub nazwę pola, którego uzyskiwany jest dostęp wczesnym wiązaniem.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
