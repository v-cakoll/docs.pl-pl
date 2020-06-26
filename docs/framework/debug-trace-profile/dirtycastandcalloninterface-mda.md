---
title: dirtyCastAndCallOnInterface MDA
description: Zapoznaj się z asystentem debugowania zarządzanego dirtyCastAndCallOnInterface, który jest wywoływany, gdy wczesne wywołania tablic wirtualnych są wykonywane na interfejsach klas z późnym wiązaniem.
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
ms.openlocfilehash: 2ed5589909915a261a22c48490e469ae52659c8c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416073"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
`dirtyCastAndCallOnInterface`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy podejmowana jest próba wywołania wczesnego za pośrednictwem tablicy tablicowej interfejsu klasy, który został oznaczony jako późny.  
  
## <a name="symptoms"></a>Objawy  
 Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwane zachowanie podczas umieszczania na wczesnym połączeniu wywołania przy użyciu modelu COM do środowiska CLR.  
  
## <a name="cause"></a>Przyczyna  
 Kod próbuje nawiązać połączenie z wczesnym wiązaniem przez tablicę czasową za pośrednictwem interfejsu klasy, który jest tylko z późnym wiązaniem. Należy zauważyć, że domyślnie interfejsy klasy są identyfikowane jako późne wiązanie. Mogą być również identyfikowane jako późne powiązania z <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem o <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> wartości ( `[ClassInterface(ClassInterfaceType.AutoDispatch)]` ).  
  
## <a name="resolution"></a>Rozwiązanie  
 Zalecanym rozwiązaniem jest zdefiniowanie jawnego interfejsu do użycia przez model COM i zadzwonienie klientów modelu COM za pomocą tego interfejsu zamiast za pomocą automatycznie wygenerowanego interfejsu klasy. Alternatywnie wywołanie z modelu COM może być przekształcone w wywołanie z późnym wiązaniem za pośrednictwem `IDispatch` .  
  
 Na koniec istnieje możliwość zidentyfikowania klasy jako <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> ( `[ClassInterface(ClassInterfaceType.AutoDual)]` ) w celu umożliwienia umieszczenia wywołań wczesnego wiązania z modelu COM, jednak użycie <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zdecydowanie odradzane ze względu na ograniczenia wersji opisane w temacie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> .  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące wczesnych wywołań w interfejsach z późnym wiązaniem.  
  
## <a name="output"></a>Dane wyjściowe  
 Nazwa metody lub nazwy pola, do którego uzyskuje się wczesne powiązanie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
