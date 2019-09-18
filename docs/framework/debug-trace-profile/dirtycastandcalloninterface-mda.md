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
ms.openlocfilehash: 6ac43f6b92198fec03e722b6cf5e12b86df6f4b8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052869"
---
# <a name="dirtycastandcalloninterface-mda"></a>dirtyCastAndCallOnInterface MDA
Asystent `dirtyCastAndCallOnInterface` debugowania zarządzanego (MDA) jest uaktywniany, gdy podejmowana jest próba wywołania wczesnego za pośrednictwem tablicy tablicowej interfejsu klasy, który został oznaczony jako późny.  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacja zgłasza naruszenie zasad dostępu lub ma nieoczekiwane zachowanie podczas umieszczania na wczesnym połączeniu wywołania przy użyciu modelu COM do środowiska CLR.  
  
## <a name="cause"></a>Przyczyna  
 Kod próbuje nawiązać połączenie z wczesnym wiązaniem przez tablicę czasową za pośrednictwem interfejsu klasy, który jest tylko z późnym wiązaniem. Należy zauważyć, że domyślnie interfejsy klasy są identyfikowane jako późne wiązanie. Mogą być również identyfikowane jako późne powiązania z <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> o wartości (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).  
  
## <a name="resolution"></a>Rozwiązanie  
 Zalecanym rozwiązaniem jest zdefiniowanie jawnego interfejsu do użycia przez model COM i zadzwonienie klientów modelu COM za pomocą tego interfejsu zamiast za pomocą automatycznie wygenerowanego interfejsu klasy. Alternatywnie wywołanie z modelu COM może być przekształcone w wywołanie z późnym wiązaniem za pośrednictwem `IDispatch`.  
  
 Na koniec istnieje <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> możliwość zidentyfikowania klasy jako (`[ClassInterface(ClassInterfaceType.AutoDual)]`) w celu umożliwienia umieszczenia wywołań wczesnego wiązania z modelu COM, jednak użycie <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> jest zdecydowanie odradzane ze względu na ograniczenia wersji opisane w <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>temacie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
