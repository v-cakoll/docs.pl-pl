---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9938db3f4a3d054fde52139c166fb6a2e2a402df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388059"
---
# <a name="pinvokestackimbalance-mda"></a>pInvokeStackImbalance MDA
`pInvokeStackImbalance` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko CLR wykryje, że głębokość stosu po wywołaniu wywołanie platformy nie odpowiada Głębokość stosu oczekiwanego, podane Konwencja wywoływania określona w <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu, jak również Deklaracja parametrów w zarządzanego podpisu.  
  
> [!NOTE]
>  `pInvokeStackImbalance` MDA zaimplementowano tylko w przypadku x86 32-bitowych platform.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 3.5 `pInvokeStackImbalance` MDA jest domyślnie wyłączona. Podczas korzystania z programu Visual Studio 2005, .NET Framework w wersji 3.5 `pInvokeStackImbalance` MDA pojawią się w **Asystenci zarządzanego debugowania** na liście **wyjątki** okno dialogowe (który jest wyświetlany, gdy Możesz kliknąć przycisk **wyjątki** na **debugowania** menu). Jednak zaznaczenie lub wyczyszczenie **wyrzuconych** pole wyboru dla `pInvokeStackImbalance` nie Włączanie lub wyłączanie MDA; tylko określa, czy program Visual Studio zgłasza wyjątek, po aktywowaniu MDA.  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacja napotka naruszenie zasad dostępu lub wywołania wywołania podczas wprowadzania lub po platformę uszkodzenie pamięci.  
  
## <a name="cause"></a>Przyczyna  
 Wywołanie invoke zarządzanego podpisu platformy może nie pasują do niezarządzanego podpisu metody wywoływane.  Ta niezgodność może być spowodowane zarządzanego podpisu nie deklarowanie poprawną liczbę parametrów lub nie określając odpowiedni rozmiar parametrów.  MDA mogą także aktywować, ponieważ Konwencja wywoływania prawdopodobnie określony przez <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu, jest niezgodny z niezarządzana konwencja wywołania.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przejrzyj zarządzana platforma wywołania podpisu i Konwencja wywoływania potwierdzić, że jest on zgodny podpisu i Konwencja wywoływania natywnego obiektu docelowego.  Spróbuj jawnie określić konwencję wywołania po obu stronach zarządzane i niezarządzane. Istnieje również możliwość, mimo że nie jako prawdopodobne, że niezarządzanej funkcji równowagą stosu innego powodu, takich jak usterki w kompilatorze niezarządzane.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Wymusza wywołanie platformy wszystkich wywołań korzysta ze ścieżki nonoptimized w środowisku CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat MDA nadaje nazwę platformy wywołania metody, która powoduje nierównowaga stosu wywołania.  Wywołanie metody invoke przykładowy komunikat platformy `SampleMethod` jest:  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
