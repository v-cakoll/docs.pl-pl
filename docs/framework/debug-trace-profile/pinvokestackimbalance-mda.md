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
ms.openlocfilehash: 9ecdfd708217f260b0c02383159fab88948029c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874214"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

`PInvokeStackImbalance` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy CLR wykryje, że głębokość stosu po wywołaniu wywołania platformy jest niezgodna Głębokość stosu oczekiwanego, podane konwencja wywołania określona w <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu i Deklaracja parametrów w zarządzanego podpisu.

`PInvokeStackImbalance` MDA jest zaimplementowanych tylko dla x86 32-bitowych platform.

> [!NOTE]
> `PInvokeStackImbalance` MDA jest domyślnie wyłączona. W programie Visual Studio 2017 `PInvokeStackImbalance` MDA pojawia się w **asystentów zarządzanego debugowania** listy w **ustawienia wyjątków** okno dialogowe (który jest wyświetlany po wybraniu **debugowania**  >  **Windows** > **ustawienia wyjątków**). Jednakże, zaznaczając lub usuwając **Przerwij gdy zgłoszony** pole wyboru jest w stanie włączać lub wyłączać MDA; tylko kontroluje, czy program Visual Studio zgłasza wyjątek, gdy zdarzenie MDA jest aktywowane.

## <a name="symptoms"></a>Symptomy

Aplikacja napotyka naruszenie zasad dostępu lub uszkodzenie podczas wprowadzania lub po platformie wywołania wywołania pamięci.

## <a name="cause"></a>Przyczyna

Zarządzanego podpisu platformy wywołania wywołania mogą być niezgodne z niezarządzanego podpisu metody wywoływane.  Taka niezgodność może być spowodowany zarządzanego podpisu nie deklarując poprawną liczbę parametrów lub brak określenia odpowiedniego rozmiaru dla parametrów.  MDA mogą także aktywować, ponieważ konwencji wywoływania, prawdopodobnie określony przez <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu, jest niezgodny z konwencji wywoływania niezarządzanego.

## <a name="resolution"></a>Rozwiązanie

Przegląd zarządzanej platformie wywołać podpisu i konwencji wywoływania, aby upewnić się, że jest on zgodny podpis i konwencji wywoływania natywnego obiektu docelowego.  Spróbuj jawnie określić konwencję wywołania po obu stronach zarządzanych i niezarządzanych. Jest również możliwe, ale nie jako prawdopodobne, że niezarządzanej funkcji niezrównoważone stosu innego powodu, takie jak usterki w kompilatorze niezarządzanych.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

Wymusza platformy wszystkie wywołania do podjęcia nonoptimized ścieżki w CLR.

## <a name="output"></a>Dane wyjściowe

Komunikat MDA zapewnia nazwę platformy wywołania metody, która powoduje nierównowaga stosu wywołania. Przykładowy komunikat platformy wywołania wywołanie metody `SampleMethod` jest:

**Wywołanie funkcji PInvoke "SampleMethod" ma niezrównoważone stosu. Jest to prawdopodobnie, ponieważ zarządzanego podpisu PInvoke jest niezgodna z niezarządzanego podpisu docelowego. Sprawdź, czy Konwencja wywoływania i parametry podpisu funkcji PInvoke odpowiadają niezarządzanego podpisu docelowego.**

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
