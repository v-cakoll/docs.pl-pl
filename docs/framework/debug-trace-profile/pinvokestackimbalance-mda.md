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
ms.openlocfilehash: c789e8cb409bd4c59c91d6b646efe428afe7c86d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217240"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

Asystent debugowania zarządzanego `PInvokeStackImbalance` (MDA) jest uaktywniany, gdy środowisko CLR wykryje, że głębokość stosu po wywołaniu wywołania platformy jest niezgodna z oczekiwaną głębokością stosu, w przypadku konwencji wywoływania określonej w atrybucie <xref:System.Runtime.InteropServices.DllImportAttribute> i deklaracji parametrów w zarządzanym podpisie.

`PInvokeStackImbalance` MDA jest implementowana tylko dla 32-bitowych platform x86.

> [!NOTE]
> `PInvokeStackImbalance` MDA jest domyślnie wyłączona. W programie Visual Studio 2017 i nowszych wersjach `PInvokeStackImbalance` MDA pojawia się na liście **asystentów debugowania zarządzanego** w oknie dialogowym **Ustawienia wyjątku** (wyświetlanym po wybraniu opcji **Debuguj** > **Windows** > **Ustawienia wyjątku**). Jednak zaznaczenie lub wyczyszczenie pola wyboru **Przerwij, gdy zostało zgłoszone** , nie powoduje włączenia ani wyłączenia MDA; kontroluje tylko, czy program Visual Studio zgłasza wyjątek podczas aktywowania MDA.

## <a name="symptoms"></a>Objawy

Aplikacja napotyka naruszenie zasad dostępu lub uszkodzenie pamięci podczas wykonywania lub po wywołaniu wywołania platformy.

## <a name="cause"></a>Przyczyna

Zarządzany podpis wywołania wywołania platformy może być niezgodny z niezarządzanym podpisem wywoływanej metody.  Niezgodność może być spowodowana przez zarządzaną sygnaturę, która nie deklaruje poprawnej liczby parametrów lub nie określa odpowiedniego rozmiaru parametrów.  Zdarzenie MDA można również uaktywnić, ponieważ Konwencja wywoływania, prawdopodobnie określona przez atrybut <xref:System.Runtime.InteropServices.DllImportAttribute>, nie jest zgodna z niezarządzaną konwencją wywoływania.

## <a name="resolution"></a>Rozwiązanie

Przejrzyj sygnaturę wywołania i konwencję wywoływania zarządzanej platformy, aby potwierdzić, że jest zgodna z sygnaturą i konwencją wywoływania natywnego elementu docelowego.  Spróbuj jawnie określić konwencję wywoływania zarówno dla stron zarządzanych, jak i niezarządzanych. Istnieje również możliwość, chociaż nie jest to prawdopodobne, że niezarządzana funkcja nierównoważy stos z innego powodu, na przykład błąd w kompilatorze niezarządzanym.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

Wymusza, aby wszystkie wywołania wywoływane przez platformę przejmowanie niezoptymalizowanej ścieżki w środowisku CLR.

## <a name="output"></a>Dane wyjściowe

Komunikat MDA zawiera nazwę wywołania metody wywoływanej przez platformę, która powoduje Niezrównoważenie stosu. Przykładowy komunikat o wywołaniu wywołania platformy dla metody `SampleMethod` to:

**Wywołanie funkcji PInvoke "SampleMethod" ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
