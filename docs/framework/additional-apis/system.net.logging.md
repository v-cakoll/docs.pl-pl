---
title: Klasa rejestrowania (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990390"
---
# <a name="logging-class"></a>Logging, klasa

Zapewnia funkcję rejestrowania śledzenia.

```csharp
internal class Logging
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="associate-method"></a>Skojarz metodę

Rejestruje informacje, które są ze sobą skojarzone dwa obiekty.

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `objA` <xref:System.Object>

  Obiekt, z którym ma zostać skojarzone `objB` .

- `objB` <xref:System.Object>

  Obiekt, z którym ma zostać skojarzone `objA` .

## <a name="entertracesource-object-string-string-method"></a>Enter (TraceSource, Object, String, String) — Metoda

Rejestruje wejście do metody.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.Object>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest wprowadzana.

- `param` <xref:System.String>

  Parametry, które zostały przesłane do metody.

## <a name="entertracesource-object-string-object-method"></a>Enter (TraceSource, Object, String, Object) — Metoda

Rejestruje wejście do metody.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.Object>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest wprowadzana.

- `paramObject` <xref:System.Object>

  Parametry, które zostały przesłane do metody.

## <a name="entertracesource-string-string-string-method"></a>Enter (TraceSource, String, String, String) — Metoda

Rejestruje wejście do metody.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.String>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest wprowadzana.

- `param` <xref:System.String>

  Parametry, które zostały przesłane do metody.

## <a name="entertracesource-string-string-object-method"></a>Enter (TraceSource, String, String, Object) — Metoda

Rejestruje wejście do metody.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.String>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest wprowadzana.

- `paramObject` <xref:System.Object>

  Parametry, które zostały przesłane do metody.

## <a name="entertracesource-string-string-method"></a>Enter (TraceSource, String, String) — Metoda

Rejestruje wejście do metody.

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `method` <xref:System.String>

  Metoda, która jest wprowadzana.

- `parameters` <xref:System.String>

  Parametry, które zostały przesłane do metody.

## <a name="entertracesource-string-method"></a>Enter (TraceSource, String) — Metoda

Rejestruje wejście do metody.

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `msg` <xref:System.String>

  Komunikat wejścia do zarejestrowania ze źródłem śledzenia.

## <a name="exception-method"></a>Exception — Metoda

Rejestruje wyjątek i przywraca wcięcia.

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.Object>

  Obiekt, w którym wywołano metodę, w której wywołał wyjątek.

- `method` <xref:System.String>

  Metoda, która wywołała wyjątek.

- `e` <xref:System.Exception>

  Zgłoszono wyjątek.

## <a name="exittracesource-object-string-object-method"></a>Exit (TraceSource, Object, String, Object) — Metoda

Dzienniki opuszczają funkcję.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.Object>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest zamykana.

- `retObject` <xref:System.Object>

  Wartość, która jest zwracana przez metodę.

## <a name="exittracesource-string-string-object-method"></a>Exit (TraceSource, String, String, Object) — Metoda

Dzienniki opuszczają funkcję.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.String>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest zamykana.

- `retObject` <xref:System.Object>

  Wartość, która jest zwracana przez metodę.

## <a name="exittracesource-object-string-string-method"></a>Exit (TraceSource, Object, String, String) — Metoda

Dzienniki opuszczają funkcję.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.Object>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest zamykana.

- `retValue` <xref:System.String>

  Wartość, która jest zwracana przez metodę.

## <a name="exittracesource-string-string-string-method"></a>Exit (TraceSource, String, String, String) — Metoda

Dzienniki opuszczają funkcję.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `obj` <xref:System.String>

  Obiekt, w którym metoda została wywołana.

- `method` <xref:System.String>

  Metoda, która jest zamykana.

- `retValue` <xref:System.String>

  Wartość, która jest zwracana przez metodę.

## <a name="exittracesource-string-string-method"></a>Exit (TraceSource, String, String) — Metoda

Dzienniki opuszczają funkcję.

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `method` <xref:System.String>

  Metoda, która jest zamykana.

- `parameters` <xref:System.String>

  Parametry, które zostały przesłane do metody, która jest zamykana.

## <a name="exittracesource-string-method"></a>Exit (TraceSource, String) — Metoda

Dzienniki opuszczają funkcję.

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Parametry

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Źródło śledzenia do rejestrowania zdarzenia.

- `msg` <xref:System.String>

  Komunikat wyjściowy do zarejestrowania ze źródłem śledzenia.

## <a name="http-property"></a>Właściwość protokołu http

Pobiera źródło śledzenia dla "System .NET. http".

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a>Wartość właściwości

<xref:System.Diagnostics.TraceSource>\
Źródło śledzenia dla "System .NET. http" lub `null` Rejestrowanie nie jest włączone.

## <a name="on-property"></a>Właściwość on

Pobiera wartość wskazującą, czy rejestrowanie jest włączone.

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a>Wartość właściwości

<xref:System.Boolean>\
`true`Jeśli rejestrowanie jest włączone; w przeciwnym razie `false` .

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
