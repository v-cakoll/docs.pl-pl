---
title: pInvokeStackImbalance MDA
description: Zapoznaj się z PInvokeStackImbalance MDA, który może być aktywowany podczas naruszenia zasad dostępu lub uszkodzenia pamięci podczas tworzenia lub wykonywania wywołania platformy.
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
ms.openlocfilehash: 89afd3fce3f2a8bffe88d45991ceeb59fc5e5b76
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803667"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

`PInvokeStackImbalance`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko CLR wykryje, że głębokość stosu po wywołaniu wywołania platformy nie jest zgodna z oczekiwaną głębokością stosu, z uwzględnieniem konwencji wywoływania określonej w <xref:System.Runtime.InteropServices.DllImportAttribute> atrybucie i deklaracji parametrów w zarządzanym podpisie.

`PInvokeStackImbalance`Zdarzenie MDA jest implementowane tylko dla 32-bitowych platform x86.

> [!NOTE]
> `PInvokeStackImbalance`Zdarzenie MDA jest domyślnie wyłączone. W programie Visual Studio 2017 i nowszych wersjach, `PInvokeStackImbalance` zdarzenie MDA pojawia się na liście **asystentów debugowania zarządzanego** w oknie dialogowym **Ustawienia wyjątku** (które jest wyświetlane po wybraniu opcji **Debuguj**  >  **Windows**  >  **Ustawienia wyjątków**systemu Windows). Jednak zaznaczenie lub wyczyszczenie pola wyboru **Przerwij, gdy zostało zgłoszone** , nie powoduje włączenia ani wyłączenia MDA; kontroluje tylko, czy program Visual Studio zgłasza wyjątek podczas aktywowania MDA.

## <a name="symptoms"></a>Objawy

Aplikacja napotyka naruszenie zasad dostępu lub uszkodzenie pamięci podczas wykonywania lub po wywołaniu wywołania platformy.

## <a name="cause"></a>Przyczyna

Zarządzany podpis wywołania wywołania platformy może być niezgodny z niezarządzanym podpisem wywoływanej metody.  Niezgodność może być spowodowana przez zarządzaną sygnaturę, która nie deklaruje poprawnej liczby parametrów lub nie określa odpowiedniego rozmiaru parametrów.  Zdarzenie MDA można również uaktywnić, ponieważ Konwencja wywoływania, prawdopodobnie określona przez <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut, nie jest zgodna z niezarządzaną konwencją wywoływania.

## <a name="resolution"></a>Rozwiązanie

Przejrzyj sygnaturę wywołania i konwencję wywoływania zarządzanej platformy, aby potwierdzić, że jest zgodna z sygnaturą i konwencją wywoływania natywnego elementu docelowego.  Spróbuj jawnie określić konwencję wywoływania zarówno dla stron zarządzanych, jak i niezarządzanych. Istnieje również możliwość, chociaż nie jest to prawdopodobne, że niezarządzana funkcja nierównoważy stos z innego powodu, na przykład błąd w kompilatorze niezarządzanym.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

Wymusza, aby wszystkie wywołania wywoływane przez platformę przejmowanie niezoptymalizowanej ścieżki w środowisku CLR.

## <a name="output"></a>Dane wyjściowe

Komunikat MDA zawiera nazwę wywołania metody wywoływanej przez platformę, która powoduje Niezrównoważenie stosu. Przykładowy komunikat wywołującego wywołanie metody `SampleMethod` jest:

**Wywołanie funkcji PInvoke "SampleMethod" ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**

## <a name="configuration"></a>Konfigurowanie

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
