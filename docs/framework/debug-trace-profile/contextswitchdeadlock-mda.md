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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43404ba24f6308d8da17b03df9997e893799c8d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875007"
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock MDA

`contextSwitchDeadlock` Zarządzanego Asystenta debugowania (MDA) jest aktywowana po wykryciu zakleszczenie podczas próby przejścia kontekstu COM.

## <a name="symptoms"></a>Symptomy

Najbardziej typowym symptomem jest wywołanie składnika COM niezarządzane z kodu zarządzanego nie zwraca.  Kolejnym objawem może być to wykorzystania pamięci zwiększa się wraz z upływem czasu.

## <a name="cause"></a>Przyczyna

Najbardziej prawdopodobna przyczyna to, że wątek jednowątkowego apartamentu (STA) nie jest przekazywanie komunikatów. Wątku STA. jest albo oczekiwania bez przekazywania komunikatów operacji długotrwałej lub nie zezwala na kolejki komunikatów, która pompy.

Użycie pamięci zwiększa się wraz z upływem czasu jest spowodowany przez wątek finalizatora, próba wywołania `Release` niezarządzanych com i ten składnik nie powraca.  To uniemożliwia to finalizatorowi odzyskiwaniu innych obiektów.

Domyślnie modelu wątkowości dla głównego wątku aplikacji konsoli języka Visual Basic jest komórce jednowątkowej To zdarzenie MDA jest aktywowane, jeśli w wątku STA. używa współdziałania COM bezpośrednio lub pośrednio za pośrednictwem środowiska uruchomieniowego języka wspólnego lub kontroli innych firm.  Aby uniknąć aktywowanie to zdarzenie MDA w aplikację konsolową w języku Visual Basic, należy zastosować <xref:System.MTAThreadAttribute> atrybutu do głównej metody lub zmodyfikować aplikację tak, by przekazywać komunikaty.

Możliwe jest, to zdarzenie MDA błędnie zostanie uaktywniony, gdy są spełnione wszystkie następujące warunki:

- Aplikacja tworzy składników COM z wątków STA bezpośrednio lub pośrednio za pośrednictwem biblioteki.

- Aplikacja została zatrzymana w debugerze, a użytkownik nadal aplikacji lub wykonana operacja kroku.

- Debugowanie niezarządzane nie jest włączona.

Aby określić, jeśli zdarzenie MDA jest aktywowane błędnie, wyłącz wszystkie punkty przerwania, uruchom ponownie aplikację i zezwolenia na jego uruchomienie bez zatrzymywania. Jeśli zdarzenie MDA nie został aktywowany, prawdopodobnie początkowej aktywacji została wartość false. W takim przypadku należy wyłączyć MDA, aby uniknąć zakłócenia w sesji debugowania.

> [!NOTE]
> To zdarzenie MDA jest domyślnym zestawem dla programu Visual Studio. Aby uzyskać informacje na temat wyłączania mda, zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).

## <a name="resolution"></a>Rozwiązanie

Postępuj zgodnie z COM reguły dotyczące przekazywanie komunikatów STA.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o kontekstach COM.

## <a name="output"></a>Dane wyjściowe

Komunikat opisujący bieżący kontekst i kontekst docelowego.

## <a name="configuration"></a>Konfiguracja

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
