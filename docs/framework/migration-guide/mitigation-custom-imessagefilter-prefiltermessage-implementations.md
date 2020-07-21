---
title: 'Łagodzenie: niestandardowe implementacje IMessageFilter. PreFilterMessage'
description: Dowiedz się więcej o niestandardowej IMessageFilter. PreFilterMessage implementacji zawartej w aplikacjach Windows Forms przeznaczonych dla .NET Framework 4.6.1 i nowszych.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475258"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Łagodzenie: niestandardowe implementacje IMessageFilter. PreFilterMessage

W Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1, implementacja niestandardowa <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować komunikaty, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> Metoda jest wywoływana, jeśli <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacja:

- Wykonuje jedną lub obie następujące czynności:

  - Dodaje filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.

  - Usuwa filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Method.

- **I** pompy komunikatów przez wywołanie <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.

## <a name="impact"></a>Wpływ

Ta zmiana ma wpływ tylko na Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework, począwszy od .NET Framework 4.6.1.

W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji .NET Framework takie implementacje w niektórych przypadkach zgłaszają <xref:System.IndexOutOfRangeException> wyjątek, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> wywoływana jest metoda

## <a name="mitigation"></a>Ograniczanie ryzyka

Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 lub nowszej wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
