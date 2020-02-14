---
title: contextSwitchDeadlock MDA
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
ms.openlocfilehash: e3fc4a2cb35cdcc713ba0ef362071083af08a27b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217556"
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock MDA

Asystent debugowania zarządzanego `contextSwitchDeadlock` (MDA) jest uaktywniany w przypadku wykrycia zakleszczenia podczas próby przejścia kontekstu COM.

## <a name="symptoms"></a>Objawy

Najbardziej typowym objawem jest to, że wywołanie niezarządzanego składnika COM z kodu zarządzanego nie zwraca.  Innym objawem jest wzrost wykorzystania pamięci z upływem czasu.

## <a name="cause"></a>Przyczyna

Najbardziej prawdopodobną przyczyną jest to, że wątek jednowątkowego apartamentu (STA) nie pompuje komunikatów. Wątek STA jest czekał bez pompowania komunikatów lub wykonuje długotrwałe operacje i nie zezwala na pompę kolejki komunikatów.

Zwiększenie użycia pamięci w czasie jest spowodowane przez wątek finalizatora próbujący wywołać `Release` na niezarządzanym składniku COM i ten składnik nie zwraca.  Zapobiega to odzyskiwaniu innych obiektów przez finalizatora.

Domyślnie model wątkowości głównego wątku Visual Basic aplikacji konsolowych to STA. To zdarzenie MDA jest uaktywniane, jeśli wątek STA używa współdziałania COM bezpośrednio lub pośrednio za pośrednictwem środowiska uruchomieniowego języka wspólnego lub formantu innej firmy.  Aby uniknąć aktywowania tego MDA w Visual Basic aplikacji konsolowej, należy zastosować atrybut <xref:System.MTAThreadAttribute> do metody Main lub zmodyfikować aplikację na komunikaty pompy.

W przypadku spełnienia wszystkich następujących warunków zdarzenie MDA może być nieaktywne.

- Aplikacja tworzy składniki COM z wątków STA bezpośrednio lub pośrednio za pośrednictwem bibliotek.

- Aplikacja została zatrzymana w debugerze, a użytkownik może kontynuować działanie aplikacji lub wykonać operację kroku.

- Debugowanie niezarządzane nie jest włączone.

Aby określić, czy MDA jest aktualnie aktywowany, wyłącz wszystkie punkty przerwania, uruchom ponownie aplikację i zezwól na jej uruchomienie bez zatrzymywania. Jeśli zdarzenie MDA nie zostanie aktywowane, prawdopodobnie początkowa aktywacja miała wartość false. W takim przypadku należy wyłączyć MDA, aby uniknąć interwencji z sesją debugowania.

> [!NOTE]
> To zdarzenie MDA jest w domyślnym zestawie dla programu Visual Studio. Aby uzyskać informacje na temat sposobu wyłączania usługi MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).

## <a name="resolution"></a>Rozwiązanie

Przestrzegaj reguł COM dotyczących pompowania komunikatów STA.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące kontekstów COM.

## <a name="output"></a>Dane wyjściowe

Komunikat opisujący bieżący kontekst i kontekst docelowy.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
