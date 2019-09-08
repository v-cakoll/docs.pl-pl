---
title: Środki zaradcze Niestandardowe implementacje IMessageFilter. PreFilterMessage
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af81468c5c4c4caf2f09725d6c7c4723084e35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779432"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Środki zaradcze Niestandardowe implementacje IMessageFilter. PreFilterMessage

W Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1, implementacja niestandardowa <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować komunikaty, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> gdy <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> Metoda jest wywoływana, jeśli implementacja:

- Wykonuje jedną lub obie następujące czynności:

  - Dodaje filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.

  - Usuwa filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Method.

- **I** pompy komunikatów przez wywołanie <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.

## <a name="impact"></a>Wpływ

Ta zmiana ma wpływ tylko na Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework, począwszy od .NET Framework 4.6.1.

W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji .NET Framework takie implementacje w niektórych przypadkach <xref:System.IndexOutOfRangeException> zgłaszają wyjątek, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> gdy wywoływana jest metoda

## <a name="mitigation"></a>Ograniczenie

Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 lub nowszej wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6-1.md)
