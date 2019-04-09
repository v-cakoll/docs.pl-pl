---
title: przekazywanie międzyprocesowe (marshaling) MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c8e42e76a61eb0820c1af72c20d004161ad25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184473"
---
# <a name="marshaling-mda"></a>przekazywanie międzyprocesowe (marshaling) MDA
`marshaling` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko CLR konfiguruje organizowanie informacji dla parametru metody lub pola struktury. To zdarzenie MDA nie działa dla zestawów kompilowanego dokładnie na czas.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA Wyświetla typ parametru lub pola w kontekstach zarządzanych i niezarządzanych i struktury lub metody z typem.  Oto przykład danych wyjściowych dla pola:  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Konfiguracja  
 Konfiguracja MDA pozwala zgłaszane na podstawie związane pola lub nazwy metod organizowania informacji o filtrze.  Poniższy przykład pokazuje użycie `methodFilter`, `fieldFilter`, i `match` elementy, aby określić filtry.  Ustawienie `name` atrybutu, aby znak gwiazdki (*) będą zgodne wszystko.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
